<template>
  <header>
    <form @click.prevent>
        <input type="text" placeholder="Enter name" v-model.trim="content">
        <button :disabled="isLoading" v-if="!isEditing" @click="addUser" class="btn">
           {{ isLoading ? 'loading.. ': 'send'}}</button>
        <button :disabled="isLoading" v-if="isEditing" @click="editUser" class="btn1">Edit</button>
    </form>
    <div class="card">
        <h2 v-if="isLoading">Loading ...</h2>
        <div v-else id="car " v-for="(user, id) in ism" :key="id" :class="{ 'car': isEditing && id === activeKey }" class="car">
            <p>{{ user.ism }}</p>
            <div class="ul">
                <button v-if="isEditing && id === activeKey" @click="cancel">cancel</button>
                <button v-if="!isEditing" @click="beforEdit(id, user.ism)">Edit</button>
                <button v-if="!isEditing" @click="deletUser(id)">Delete</button>
            </div>
        </div>
    </div>
  </header>
</template>

<script>


export default {
  data(){
    return{
      content: '',
        ism: {},
        activeKey: null,
        isEditing: false,
        isLoading: false,
        api: 'https://vue-js-f4221-default-rtdb.firebaseio.com/users.json'
    }
  },
  methods:{
      // addUser
      async addUser() {
                if (this.content.length === 0 || this.content.length <= 3) {
                    return
                }
                try {
                    this.isLoading = true
                    const res = await fetch(this.api, {
                        method: 'POST',
                        headers: {
                            'content-type': 'application/json'
                        },
                        body: JSON.stringify({
                            ism: this.content
                        })

                    })
                    const red = await res.json()
                    this.ism[red.name] = {
                        ism: this.content
                    }
                    this.isLoading = false
                    console.log(red);
                } catch (error) {
                    console.log(error);
                }
                console.log(this.content);
                this.content = ''
            },
            // getUser
            async getUser(ism) {
                try {
                    const res = await fetch(this.api)
                    const red = await res.json()
                    this.ism = red
                    console.log(red);
                } catch (error) {
                    console.log(error);
                }
            },
            // editUser
            async editUser() {
                try {
                    const ser = await fetch('https://vue-js-f4221-default-rtdb.firebaseio.com/users/${this.activeKey}.json',
                        {
                            method: 'PUT',
                            headers: {
                                'content-type': 'application/json'
                            },
                            body: JSON.stringify({
                                ism: this.content
                            })
                        })
                    const red = await ser.json
                    this.ism[this.activeKey] = {
                        ism: this.content
                    }
                } catch (error) {
                    console.log(error);
                }
                this.cancel()
            },
            // deleteUser 
            async deletUser(id) {
                try {
                    const res = await fetch('https://vue-js-f4221-default-rtdb.firebaseio.com/users/${id}.json', { method: 'DELETE' })
                    delete this.ism[id]
                  } catch (error) {
                    console.log(error);
                }
            },
            // beforEdit
            async beforEdit(id, text) {
                this.activeKey = id
                this.content = text
                this.isEditing = true
            },
            // cancel
            cancel() {
                this.activeKey = null
                this.content = ''
                this.isEditing = false
            }
    },
    mounted() {
    this.getUser()
  }
}
</script>


<!-- CSS end -->



<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
form {
        width: 400px;
        margin: 200px auto 0;
        padding: 30px;
        border: 1px solid black;
        display: flex;
        flex-direction: column;
    }

    #car {
        background-color: red;
    }

    form button {
        margin-top: 10px;
    }

    form .btn {
        background-color: aqua;
        border: none;
        font-size: 20px;
        height: 30px;
    }

    form .btn1 {
        background-color: gold;
        border: none;
        font-size: 20px;
        height: 30px;
    }

    form input {
        height: 30px;
        padding-left: 10px;
        font-weight: 700;
        outline-color: aqua;
    }

    .card {
        width: 400px;
        margin: 20px auto;
        padding: 20px;
        border: 1px solid black;
    }

    .car {
        display: flex;
        width: 100%;
        margin: 10px;
        justify-content: space-between;
    }

    /* .ul { */
    button {
        margin-left: 10px;
        padding: 2px 5px;
        border: none;
    }
  

    button:nth-child(1) {
        background-color: goldenrod;
    }

    button:nth-child(2) {
        background-color: gold;
    }

    button:nth-child(3) {
        background-color: red;
    }
</style>

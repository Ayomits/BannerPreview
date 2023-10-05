<template>
    <div class="card">
        <div class="banner" :style="{ backgroundColor: bannerUrl }">
            <img class="banner-img" :src="bannerUrl">
            
        </div>
        <div class="avatar">
            <img class="avatar-img" :src="avatarUrl">
        </div>
        <div class="info">
            <div class="infocontainer">
                {{ username }}
            </div>
        </div>
    </div>

    <div class="settings">
  <form action="" class="settingsForm">
    <label for="">Your username</label><br>
    <input maxlength="50" type="text" v-model="username"><br>
    <label for="">{{ bannerLabelText }}</label> <br>
    <input :type="inputType" v-model="bannerUrl"> <br>
    <label>Avatar Link</label><br>
    <input type="link" v-model="avatarUrl"><br>
    <label for="">Choose Banner Type</label>
    <select name="" id="" @change="handlerOptionChange">
      <option value="linkBanner">Banner Link</option>
      <option value="colorBanner">Banner Color</option>
    </select>
  </form>
</div>
  </template>
  


<script>

export default{
    data(){
        return{
            color: '#333',
            username: 'username',
            is_show: false,
            avatarUrl: 'https://cdn.discordapp.com/embed/avatars/0.png',
            bannerUrl: '#3258ae',
            backgroundColor: '#444',
            bannerType: 'linkBanner',
            type: 'text',
            bannerLabel: 'Banner Link',
            

        }
    },
    methods:{
        handlerOptionChange(event){
            const value = event.target.value
            if (value == 'linkBanner'){
                this.bannerType = 'linkBanner'
                this.bannerLabel = 'Banner Link'
                this.type = 'text'
                
            }else{
                this.bannerType = 'colorBanner'
                this.bannerLabel = 'Color Banner'
                this.type = 'color'
                this.bannerUrl = ''
            }
        }
    },
    computed: {
    inputType() {
      return this.bannerType === 'colorBanner' ? 'color' : 'text';
    },
    bannerLabelText() {
      return this.bannerType === 'colorBanner' ? 'Выберите цвет' : 'Banner Link';
    }
  },
}

</script>

<style scoped>
    

    .card{
        position: relative;
        display: flex;
        justify-content: center;
        overflow: hidden;
        background-color: #434040;
        max-width: 20%;
        align-items: center;
        padding: 0 3% 5%;
        margin: 0 auto;
        flex-direction: column;
        border-radius: 15px;
    }
    .banner{
        position: relative;
        width: 640px;
        height: 240px;
        overflow: hidden;
        
    }

    .banner-img {
        width: 100%;
        height: 100%;
        object-fit: cover;
        object-position: center ;
}
    .avatar{
        position: absolute; /* добавлено */
        border-radius: 50%;
        border: 3px solid #2f3136;
        box-shadow: 0 1px 3px rgba(0, 0, 0, 0.3);
        overflow: hidden;
        width: 128px;
        height: 128px;
        margin-top: 35%;
        margin-right: 70%;
    }

    .avatar-img {
        width: 100%;
        height: 100%;
        object-fit: cover;
        
    }

    .settings{
        background-color: #434040;
        max-width: 15%;
        display: flex;
        justify-content: center;
        margin: 2% auto;
        border-radius: 15px;
        padding: 2% 5.5%;
        
    }
    .settingsForm{
        margin-top: -12%;
        vertical-align: middle;
    }
    .settingsForm input{
        border: none;
        padding: 3%;
        padding-right: 35%;
    }
    .settingsForm label{
        font-size: 2rem;
    }
    
</style>
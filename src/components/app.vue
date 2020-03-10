<template>
<f7-app :params="f7params" >
   <!-- Right panel with reveal effect-->
  <f7-panel right reveal theme-dark>
    <f7-view>
      <f7-page>
        <f7-navbar title="EncouterMe"></f7-navbar>
        <f7-block></f7-block>
      </f7-page>
    </f7-view>
  </f7-panel>


<<<<<<< HEAD
  <!-- Views/Tabs container -->
  <f7-views tabs class="safe-areas">
    <!-- Tabbar for switching views-tabs -->
   <!--  <f7-toolbar tabbar labels bottom>
      <f7-link tab-link="#view-home" tab-link-active icon-ios="f7:house_fill" icon-aurora="f7:house_fill" icon-md="material:home" text="Home"></f7-link>
      <f7-link tab-link="#view-catalog" icon-ios="f7:square_list_fill" icon-aurora="f7:square_list_fill" icon-md="material:view_list" text="Catalog"></f7-link>
      <f7-link tab-link="#view-settings" icon-ios="f7:gear" icon-aurora="f7:gear" icon-md="material:settings" text="Settings"></f7-link>
    </f7-toolbar> -->

    <!-- Your main view/tab, should have "view-main" class. It also has "tab-active" class -->
    <f7-view id="view-home" main tab tab-active url="/"></f7-view>

    <!-- Catalog View -->
    <f7-view id="view-catalog" name="catalog" tab url="/catalog/"></f7-view>
=======
  <!-- Your main view, should have "view-main" class -->
  <f7-view main class="safe-areas" url="/"></f7-view>
>>>>>>> upstream/master


<<<<<<< HEAD
  </f7-views>


  <!-- Popup -->
  <f7-login-screen id="my-registration-screen">
    <f7-view>
      <f7-page login-screen>
        <f7-login-screen-title>Registaration</f7-login-screen-title>
        <f7-list form>
          <f7-list-input
            type="text"
            name="username"
            placeholder="Your username"
            :value="username"
            @input="username = $event.target.value"
          ></f7-list-input>
          <f7-list-input
            type="password"
            name="password"
            placeholder="Your password"
            :value="password"
            @input="password = $event.target.value"
          ></f7-list-input>
          <f7-list-input
            type="number"
            name="number"
            placeholder="Your number"
            :value="number"
            @input="number = $event.target.value"
          ></f7-list-input>
        </f7-list>
        <f7-list>
          <f7-list-button title="Regisrtation " @click="alertLoginData"></f7-list-button>
          <f7-block-footer>
            Some text about login information.<br>Click "Sign In" to close Login Screen
          </f7-block-footer>
        </f7-list>
      </f7-page>
    </f7-view>
  </f7-login-screen>

  <f7-login-screen id="my-login-screen">
=======
  
<f7-login-screen id="login-screen" theme-dark :opened="loginScreenOpened">
>>>>>>> upstream/master
    <f7-view>
      <f7-page login-screen>
        <f7-login-screen-title>Вход</f7-login-screen-title>
        <f7-list form>
          <f7-list-input
            type="text"
            placeholder="Имя пользователя или почта"
            :value="username"
            @input="username = $event.target.value"
          ></f7-list-input>
          <f7-list-input
            type="password"
         placeholder="Пароль"
            :value="password"
            @input="password = $event.target.value"
          ></f7-list-input>
        </f7-list>
        <f7-list>
<f7-button fill @click="alertLoginData">Войти</f7-button>
          <f7-block-footer>
          Еще не создали аккаунт?<br><f7-list-button @click="viewOpen('#register-screen')">Зарегистрироваться</f7-list-button>
          </f7-block-footer>
        </f7-list>
      </f7-page>
    </f7-view>
  </f7-login-screen>
  <f7-login-screen id="register-screen" theme-dark >
    <f7-view>
      <f7-page login-screen >
        <f7-login-screen-title>Регистрация</f7-login-screen-title>
        <f7-list form>
          <f7-list-input
            type="text"
          placeholder="Имя пользователя или почта"
            
            @input="username = $event.target.value"
          ></f7-list-input>
          <f7-list-input
            type="password"
           placeholder="Пароль"
            @input="password = $event.target.value"
          ></f7-list-input>
        </f7-list>
        <f7-list>
          <f7-button fill @click="alertRegisterData()">Зарегистрироваться</f7-button>
          <f7-block-footer>
            Уже есть аккаунт?<f7-list-button @click="viewOpen('#login-screen')">Войти</f7-list-button>
          </f7-block-footer>
        </f7-list>
      </f7-page>
    </f7-view>
  </f7-login-screen>
</f7-app>
</template>
<script>

  import routes from '../js/routes.js';

  export default {
    data() {
      return {
        // Framework7 Parameters
        f7params: {
          name: 'EncounterMe!', // App name
          theme: 'auto', // Automatic theme detection


          // App routes
          routes: routes,
        },
        loginScreenOpened:true,
        // Login screen data
        username: '',
        password: '',
        list_username: [],
        list_password: [],
      }
    },
    methods: {
      viewOpen(str){
         this.$f7.loginScreen.close();
        this.$f7.loginScreen.open(str);
        
      },
     back(){
       this.$f7.dialog.alert('Не верный пароль');
         this.$f7.loginScreen.close();
     },
      alertLoginData() {
        let error=true;
      
        if(this.username=='' ||  this.password==''){
          //Тут будет код для вывода ошибки
          this.$f7.dialog.alert("Одно из полей пустое");
        }
        if(this.username && this.password){
          
          if(this.list_username.length!=0){
          for(let i=0;i<this.list_username.length;i++){
            if(this.username==this.list_username[i]){
              if(this.password==this.list_password[i]){
                error=false;
                this.$f7.dialog.alert('Вы успешно вошли', () => {
                   this.$f7.loginScreen.close();
                    });
              }else{
                 this.$f7.dialog.alert('Не верный пароль');
              }
            }
          }
          if(error){
            this.$f7.dialog.alert('Не верный логин или пароль');
          }
          }else{
           
             this.$f7.dialog.alert('База данных пуста Зарегистрируйтесь', () => {
              this.username='';
              this.password='';
              this.viewOpen('#register-screen');
              
        });
        }
        }
       
      },
      alertRegisterData() {
        let error=false;
        if(this.username=='' ||  this.password==''){
          //Тут будет код для вывода ошибки
          this.$f7.dialog.alert("Одно из полей пустое");
        }
      if(this.username && this.password){
          if(this.list_username.length!=0){
          for(let i=0;i<this.list_username.length;i++){
            if(this.username==this.list_username[i]){
              //Вывести о том что такой пользователь есть
              error=true;
              
               this.$f7.dialog.alert('Пользователь с ником '+this.username+' уже есть');
               break;
            }
          }
          if(!error){
            this.list_username.push(this.username);
            this.list_password.push(this.password);
               this.$f7.dialog.alert('Вы успешно зарегистрировались Ваши данные <br>Username: ' + this.username + '<br>Password: ' + this.password, () => {
                this.$f7.loginScreen.close();
                });
          }
          }else{
            this.list_username.push(this.username);
            this.list_password.push(this.password);
             this.$f7.dialog.alert('Вы успешно зарегистрировались Ваши данные <br>Username: ' + this.username + '<br>Password: ' + this.password, () => {
                this.$f7.loginScreen.close();
                });
        }
        }
      }
    },
    mounted() {
      this.$f7ready((f7) => {
        
        // Call F7 APIs here
      });
    }
  }
</script>

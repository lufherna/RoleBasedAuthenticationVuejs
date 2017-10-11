<script>
import loginService from './loginService.js';
export default {
    template:require('./login.html'),
    data() {
        return {
            loginDetails : {
                residentID : '',
                password : ''
            },
        }
    },
    // the user credential is captured and from the login.service.js the user credential is sent to the server
    // the server return with success, along with token and role
    // this server response is sent to login.vue, where
    // if the response is success then the return data is stored
    // in local storage 
    methods: {
        loginUser:function() {  
             const authUser = {}
             var app = this;
            loginService.login(this.loginDetails)
            .then(function(res) {
                if(res.status === "success") {
                    authUser.data = res.data;
                    authUser.token = res.token;
                    app.$store.state.isLoggedIn = true
                    window.localStorage.setItem('lbUser',JSON.stringify(authUser));
                    if(authUser.data.role_id === 'ADMIN') {
                     app.$router.push('/admin');
                    }else {
                      app.$router.push('/resident');
                    }
                }else {
                      app.$store.state.isLoggedIn = false;
                }
            })
            .catch(function (err){
                console.log(err.data)
            })
        },
        loginAuth:function () {
             var app = this;
            const status =  JSON.parse(window.localStorage.getItem('lbUser'));
            if(status === null || status === undefined) {
                 app.$router.push('/login');
            }else if (status.data.role_id === 'ADMIN') {
               app.$router.push('/admin');
            }else {
               app.$router.push('/resident');
            }
        }
    },
    created:function() {
        this.loginAuth();
    }
}
</script>

<style lang="scss">
    @import './login.scss';
</style>
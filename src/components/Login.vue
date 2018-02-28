<template>
<div>
    <div class="card login-card">
        <div class="card-header">
            {{title}}
        </div>
        <div class="card-block card-body">
            <div :class="['input-group', groupMargin]">
                <span class="input-group-name">
                    用户名
                </span>
                <input type="text" class="form-control" autofocus v-model="user">
            </div>

            <div :class="['input-group', groupMargin]">
                <span class="input-group-name">
                    密码
                </span>
                <input type="password" class="form-control" v-model="pwd">
            </div>

            <div :class="['input-group', groupMargin]" v-if="reg">
                <span class="input-group-name">
                    重复密码
                </span>
                <input type="password" class="form-control" v-model="pwd2">
            </div>

            <button type="button" class="btn btn-primary btn-lg btn-block" @click="submit">{{title}}</button>
            
        </div>
    </div>
</div>
</template>


<script>
import axios from 'axios'
export default {
    name: 'login',
    data() {
        return {
            autofocus: true,
            user: '',
            pwd: '',
            pwd2: ''
        }
    },
    computed: {
        groupMargin() {
            return  this.reg ? 'margin10' : 'margin20'
        }
    },
    props: {
        reg: {
            type: Boolean,
            default: false
        },
        title: {
            type: String,
            default: '登陆'
        },
        url: {
            type: String,
            default: ''
        }
    },
    methods: {
        submit() {
            const {
                user,
                pwd,
                pwd2,
                reg
            } = this.$data
            if (!user || !pwd) {
                return alert('请输入用户名和密码')
            }
            if (reg && !pwd2) {
                return alert('请输入重复密码')
            }
            axios.post(this.url, {
                username: this.username,
                pwd: this.pwd,
                pwd2: this.pwd2
            }).then(res => {
                this.$router.push('/')
            }).catch(e => {
                alert(e.message)
            })
        }
    }
}
</script>

<style lang="less" scoped>
@import '../common/utils.less';
.login-card {
   .center(@width: 500px, @height: 350px)
}

.margin10 {
    margin: 10px auto;
}

.margin20 {
    margin: 20px auto;
}

.card-body {
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
    .input-group {
        line-height: 38px;
        input {
            margin-left: 10px;
        };
        .input-group-name {
            width: 80px;
        }
    };
    button {
        margin-top: 20px;
    }
}
</style>

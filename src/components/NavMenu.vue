<template>
<div>
    <nav class="navbar navbar-expand-lg navbar-light bg-faded fixed-top" style="background-color: #e3f2fd;">
        <a class="navbar-brand" href="/">CNODE</a>
        <!-- <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
        </button> -->
        
        <form class="form-inline my-2 my-lg-0">
            <input class="form-control mr-sm-2" type="text" placeholder="Search" aria-label="Search">
            <!-- <button class="btn btn-outline-success my-2 my-sm-0" type="submit">Search</button> -->
        </form>

        <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <ul class="navbar-nav pull-right">
                <li v-for="m in menus" :key="m.path" :class="['nav-item', {active : activeMenu === m.path}]">
                    <a class="nav-link" @click="go(m.path)" href="javascript:void">{{m.label}}</a>
                </li>
            </ul>
        </div>
    </nav>
</div>
</template>

<script>
export default {
    name: 'cheader',
    data() {
        return {
            menus: [{
                label: '登陆',
                path: '/login'
            }, {
                label: '注册',
                path: '/register'
            }],
            login: true
        }
    },
    methods: {
        go(path) {
            this.$router.push(path)
        }
    }
}
</script>


<style lang="less" scoped>
    .pull-right {
        position: absolute;
        right: 20px;
        // border: 1px solid red
    }
</style>


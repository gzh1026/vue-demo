<template>
    <div>
        <table>
            <tr>
                <td>编号</td>
                <td>图书名称</td>
                <td>作者</td>
            </tr>
            <tr v-for="item in books">
                <td>{{item.id}}</td>
                <td>{{item.name}}</td>
                <td>{{item.author}}</td>
            </tr>
        </table>
        {{msg}}
    </div>
</template>

<script>
    export default {
        name: "Book",
        data(){
            return {
                msg:'hello vue',
                books:[
                    {
                        id:1,
                        name:'java零基础实战',
                        author:'me'
                    },{
                        id:2,
                        name:'python零基础实战',
                        author:'you'
                    },{
                        id:3,
                        name:'spring零基础实战',
                        author:'he'
                    }
                ]
            }
        },
        created() {
            const _this=this
            axios.get('http://localhost:8181/book').then(function (resp) {
                _this.books = resp.data
            })
        }
    }
</script>

<style scoped>

</style>
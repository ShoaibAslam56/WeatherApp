<template>
    <div>
        <table>
            <tr v-for="item in user"  :key="item.id">
                <td>{{ item.id }}</td>
                <td>{{ item.name }}</td>
            </tr>
        </table>
    </div>
</template>

<script>


export default {                
    name:'LoopData' ,
    data() {
       return{
        user:[
            {id:1,name:'John'},
            {id:2,name:'Jane'},
            {id:3,name:'Bob'},
        ]
       }
    },
}
</script>

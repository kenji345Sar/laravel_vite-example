<template>
    <v-container fluid>
        <h4 class="mb-5">ToDo一覧</h4>
        <div class="table-list">
            <v-table density="compact">
                <thead>
                    <tr>
                        <th>No.</th>
                        <th>タイトル</th>
                        <th>ステータス</th>
                        <th>作成日</th>
                        <th></th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="(item, index) in todoList" :key="index">
                        <td>{{ index + 1 }}</td>
                        <td>{{ item.title }}</td>
                        <td>{{ item.status }}</td>
                        <td>{{ item.create_date }}</td>
                    </tr>
                </tbody>
            </v-table>
        </div>
    </v-container>
</template>

<script>
export default {
    data() {
        return {
            todoList: []
        }
    },
    methods: {
        getTodoList() {
            axios.get('/api/todo')
                .then(response => {
                    this.todoList = response.data
                })
                .catch(error => {
                    console.log(error)
                })
        }
    },
    mounted() {
        this.getTodoList()
    }
}

</script>

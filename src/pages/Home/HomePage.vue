<template>
    <div class="row">
        <div class="col-lg-8">
            <post-list/>
        </div>
        <div class="col-lg-4">
            <sidebar />
        </div>
    </div>
</template>

<script>
import { mapActions } from 'vuex';

import PostList from '../../components/Post/PostList';
import Sidebar from '../../components/General/Sidebar';
export default {
    name: 'home-page',
    components: {
        PostList,
        Sidebar
    },
    // watch $route chỉ chạy khi có sự thay đổi router 
    // Nếu như lần load đầu tiên -> Không có chạy
    watch: {
        '$route' (to, from) {
            var tagIndex = to.query.tagIndex;
            this.getListPostHasPaging({ tagIndex })
        }
    },
    created() {
        var tagIndex = this.$route.query.tagIndex;
        this.getListPostHasPaging({ tagIndex })
    },
    methods: {
        ...mapActions([
            'getListPostHasPaging',
        ])
    }
}
</script>

<style>

</style>
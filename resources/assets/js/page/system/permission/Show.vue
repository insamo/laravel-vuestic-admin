<template>
    <div class="form-elements">
        <div class="row">
            <div class="col-md-12">
                <vuestic-widget headerText="查看权限">
                    <form>
                        <div class="row">
                            <div class="col-md-12">
                                <fieldset>
                                    <div class="form-group">
                                        <div class="input-group">
                                            <input id="name" v-model="form.name" required/>
                                            <label class="control-label" for="name">权限值</label><i class="bar"></i>
                                        </div>
                                    </div>
                                    <div class="form-group">
                                        <div class="input-group">
                                            <input id="display_name" v-model="form.display_name" required/>
                                            <label class="control-label" for="display_name">展示名称</label><i
                                                class="bar"></i>
                                        </div>
                                    </div>
                                    <div class="form-group">
                                        <div class="input-group">
                                            <textarea type="text" v-model="form.description" id="description"
                                                      required></textarea>
                                            <label class="control-label" for="description">描述</label><i class="bar"></i>
                                        </div>
                                    </div>
                                    <div class="form-group">
                                        <div class="input-group">
                                            <textarea type="text" v-model="form.class_settings" id="class_settings"
                                                      required></textarea>
                                            <label class="control-label" for="class_settings">ClassSettings</label><i
                                                class="bar"></i>
                                        </div>
                                    </div>
                                    <div class="form-group">
                                        <button class="btn btn-info"
                                                @click="$router.push({name:'system.permission.edit',params:{id:$route.params.id}})">
                                            编辑
                                        </button>
                                    </div>
                                </fieldset>

                            </div>
                        </div>
                    </form>
                </vuestic-widget>
            </div>
        </div>
    </div>
</template>
<script>
    import {showSystemPermission} from './../../../api/api';

    export default {
        data() {
            return {
                form: {
                    name: '',
                    display_name: '',
                    description: '',
                    class_settings: ''
                }
            }
        },
        mounted() {
            this.fetchPermission();
        },
        methods: {
            fetchPermission() {
                showSystemPermission({id: this.$route.params.id}).then((response) => {
                    this.form = response.data.data;
                });
            }
        }
    }
</script>
<style lang="scss">
    .abc-checkbox, .abc-radio {
        display: flex !important;
        justify-content: flex-start;
    }

    input[type=checkbox]:disabled + label, input[type=radio]:disabled + label,
    input[type=checkbox]:disabled, input[type=radio]:disabled {
        cursor: not-allowed;
    }
</style>
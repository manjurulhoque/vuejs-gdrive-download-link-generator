<template>
    <div>
        <div class="container">
            <div style="padding-top:25px">
                <center>
                    <h2>
                        Google Drive Link Generator
                    </h2>
                </center>
            </div>
            <div class="col-md-8 col-md-offset-2">
                <div class="panel panel-primary" style="margin-top: 70px;">
                    <div class="panel-heading">
                        <h1 class="panel-title">Google Drive Direct Download Link Generator</h1>
                    </div>
                    <div class="panel-body">
                        <form>
                            <div class="form-group">
                                <label for="sharelink">Shareable link</label>
                                <input type="text" class="form-control" v-model="shareable" placeholder="https://drive.google.com/file/d/XX-X__XXXXX-XXXXXXXXXXXXXXXX/view?usp=sharing" autofocus="true">
                            </div>
                            <div class="form-group">
                                <label for="downloadlink">Downloadable link</label>
                                <div class="input-group">
                                    <input type="text" class="form-control" v-model="downloadable" readonly>
                                    <span class="input-group-btn">
                                        <a class="btn btn-success" :href="downloadable" target="_blank" v-on:click="onDownload" type="button" :disabled="downloadable.length == 0">Download</a>
                                    </span>
                                </div>
                            </div>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>

export default {
    name: 'app',
    data() {
        return {
            shareable: ''
        }
    },
    methods: {
        onDownload() {
            console.log('clicked');
        }
    },
    computed: {
        downloadable() {
            return this.shareable.replace(/\/file\/d\/(.+)\/(.+)/, "/uc?export=download&id=$1");
        }
    }
}
</script>
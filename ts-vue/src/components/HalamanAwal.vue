<template>
    <div class="hello">
        <h2>{{ msg }}</h2>
        <p>
            <button @click="tampilkanMhs">Tampilkan Mahasiswa</button>
        </p>

        <p v-if="tampil">
            <table class="center">
                <caption>Daftar Mahasiswa UT</caption>
                <thead>
                    <tr>
                        <th>NIM</th>
                        <th>Nama</th>
                        <th>Tanggal Lahir</th>
                        <th>E-Mail</th>
                        <th>Program Studi</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="dataMhs in dataMhsList" :key="dataMhs.id">
                        <td>{{dataMhs.nim}}</td>
                        <td>{{dataMhs.nama}}</td>
                        <td>{{dataMhs.tglLahir}}</td>
                        <td>{{dataMhs.email}}</td>
                        <td>{{dataMhs.prodi}}</td>
                    </tr>
                </tbody>
            </table>
        </p>
    </div>
</template>

<script>
    import axios from 'axios'

    export default{
        name:'HalamanAwal',
        data(){
            return{
                tampil:false,
                dataMhsList:[]
            }
        },
        props:{
            msg:String
        },
        methods:{
            tampilkanMhs(){
                let AxiosInstance = axios.create();
                let requestedData;

                AxiosInstance.get('http://localhost:4000/mhs')
                .then(
                    response=>{
                        requestedData = response.data
                        this.dataMhsList = requestedData
                        this.tampil = true
                    }
                ).catch(error=>{
                    console.log(error.message)
                })
            }
        }
    }
</script>

<style scoped>
    h3{margin: 40px 0 0;}
    ul{list-style: none;padding: 0;}
    li{display: inline-block;margin: 0 10px;}
    a{color:#42b983}
    .center{margin-left: auto;margin-right: auto;}
</style>
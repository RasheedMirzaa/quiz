<template>
    <div>
        <b-container>
            <p>Skor Kamu = {{ score * 20 }}</p>
            <div role="tablist">
                <b-card v-for="(item,index) in items" no-body class="mb-1" :key="item.soal">
                    <b-card-header header-tag="header" class="p-1" role="tab">
                        <b-btn block  type="button" v-b-toggle="'accordion-'+ index" v-on:click="setPosition(index)">{{ 'Soal ' + (index+1) }}</b-btn>
                    </b-card-header>
                    <b-collapse v-bind:id="'accordion-'+index" visible accordion="my-accordion" role="tabpanel">
                        <b-card-body>
                            <p class="card-text">{{ item.soal }}</p>
                            <div v-if="item.btn_click">
                                <b-form-group>
                                    <b-form-radio-group v-model="item.clicked"
                                                        :options="item.pilihan"
                                                        name="radioInline">
                                    </b-form-radio-group>
                                </b-form-group>
                                <b-button variant="success" v-on:click="checkingAnswer">Yakin</b-button>
                            </div>

                        </b-card-body>
                    </b-collapse>
                </b-card>
            </div>
        </b-container>
    </div>
</template>
<script>
    export default {
        name : 'CardQuestion',
        data : function () {
            return {
                score:0,
                position:0,
                items: [{
                   soal : 'Hewan apa yang hidup di air?',
                    btn_click : true,
                    clicked:String,
                    pilihan:[
                        { text:'Ikan',value:'ikan'},
                        { text:'Ayam',value:'ayam'},
                        { text:'Kalajengking',value:'kalajengking'},
                        { text: 'Gorila',value:'gorila'}],
                    jawaban:'ikan'
                },{
                    soal : '90+110+5000x0 = ',
                    btn_click : true,
                    clicked:String,
                    pilihan:[
                        { text:'5000',value:'5000'},
                        { text:'5200',value:'5200'},
                        { text: '0',value:'0'},
                        { text: '200',value:'200'}],
                    jawaban:'200'
                },{
                    soal : 'Kitab Al-Quran diturunkan kepada nabi ?',
                    btn_click : true,
                    clicked:String,
                    pilihan:[
                        { text:'Musa a.s.',value:'musa a.s.'},
                        { text:'Daud a.s.',value:'daud a.s.'},
                        { text: 'Isa a.s.',value:'isa a.s.'},
                        { text: 'Muhammad saw.',value:'muhammad saw.'}],
                    jawaban:'muhammad saw.'
                },{
                    soal : 'Siapakah orang terkaya didunia ?',
                    btn_click : true,
                    clicked:String,
                    pilihan:[
                        { text:'Rasheed',value:'rasheed'},
                        { text:'Bill Gates',value:'bill'},
                        { text: 'Yang melaksanakan solat di sepertiga malam',value:'solat'},
                        { text: 'Umuh Muchtar',value:'umuh'}],
                    jawaban:'solat'
                },{
                    soal : 'Dibawah ini pemain sepak bola yang menggunakan nomor punggung 10,KECUALI?',
                    btn_click : true,
                    clicked:String,
                    pilihan:[
                        { text:'Tsubatsa',value:'subasa'},
                        { text:'Messi',value:'messi'},
                        { text: 'Ronaldo',value:'ronaldo'},
                        { text: 'Rashford',value:'rashford'}],
                    jawaban:'ronaldo'
                }],
            }
        },
        methods:{
            setPosition(i){
               this.position = i;
            },
            checkingAnswer(){
                this.items[this.position].btn_click = false;
                if(this.items[this.position].jawaban === this.items[this.position].clicked){this.score++;}
            },
        }
    }
</script>
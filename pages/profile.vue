<template>
    <div>
        <section class='profile-container divide-y divide-blue-400'>
            <div class='pl-10 py-5'>
                <h1 class='text-5xl font-serif'>Profile</h1>
            </div>
            <div class='flex justify-center mt-4 mb-4'>
                <div class='profile-image-wrapper'>
                    <div class='profile-image'>
                    <img src="../static/CEOFace.png" alt="" class='w-100%'>
                    </div>
                </div>
                <div class='history-wrapper'>
                    <p class='mt-2 mb-2'>1983年　神戸市生まれ</p>
                    <p class='mt-2 mb-2'>2001年　私立灘高校卒業</p>
                    <p class='mt-2 mb-2'>2009年　大阪大学医学部医学科卒業</p>
                    <p class='mt-2 mb-2'>2009年〜亀田総合病院初期研修、太田記念病院で一般外科研修、大阪大学医学部心臓外科にて外科医として研鑽をつみ、その間にUSMLE1,2,3を取得</p>
                    <p class='mt-2 mb-2'>2017年~2018年 Yale University Hospital CT Surgery Clinical Fellow</p>
                    アメリカ留学を機に自分の人生を見つめ直し、外科医を辞め新しい道を模索する決意をする
                    <p class='mt-2 mb-2'>2019年　Tokyo Gs Academy に入学。プログラミングに出会い、その魅力に取り憑かれる</p>
                    <p class='mt-2 mb-2'>2020年1月　BlockAidを起業、複数のWebサービスを運営</p>
                    <p class='mt-2 mb-2'>2021年3月〜株式会社AMIにエンジニアとしてJoin</p>
                            6月〜York University(UK) Computer Science Master Cource 就学中
                </div>
            </div>
            <div class='profile-lower-wrapper mt-4 mb-4'>
                <p class='mt-2 mb-2'>主な資格等</p>
                <p class='mt-2 mb-2'>
                    医師免許、USMLE Step1,2,3, 外科専門医、心臓外科専門医、産業医専門医<br/>
                    Duolingo English Test 120, 統計検定２級、AtCoder 緑
                </p>
                <p class='mt-2 mb-2'>趣味</p>
                <p class='mt-2 mb-2'>ピアノ、ランニング、釣り、ラグビー観戦</p>
            </div>
            <!-- <p>{{routeInfo}}</p> -->
        </section>
    </div>
</template>

<script>
export default {
    // props:['routeInfo'],
    // mounted(){
    //     console.log(this.routeInfo)
    // }
}
</script>

<style scoped>
.profile-container{
    margin-left: auto;
    margin-right:auto;
    width:80%;
    margin-top:60px;
    margin-bottom:60px;
    /* background: rgb(216, 157, 157); */
    height:800px;
}
.profile-image-wrapper{
    width:40%;
    height:500px;
    /* background: rgb(174, 237, 111); */
    padding:10px;
    display: flex;
    align-items: center;
}
.history-wrapper{
    width:60%;
    height:500px;
    /* background: rgb(108, 165, 250); */
    padding:25px;
}
.profile-image{
    width:270px;
    margin-left: auto;
    margin-right:auto;
}
.profile-lower-wrapper{
    padding: 15px;
}
</style>
<template>
    <div>
        <section class='profile-container'>
            <div class='pl-10 py-5'>
            <h1 class='text-4xl font-serif'>Profile</h1>
            </div>
            <div class='flex justify-center'>
                <div class='profile-image-wrapper'>
                    <div class='profile-image'>
                    <img src="../static/CEOFace.png" alt="" class='w-100%'>
                    </div>
                </div>
                <div class='history-wrapper'>
                    <p class='text-xl'>略歴</p>
                    <p>1983年　神戸市生まれ</p>
                    <p>2001年　私立灘高校卒業</p>
                    <p>2009年　大阪大学医学部医学科卒業</p>
                    <p>2009年〜亀田総合病院初期研修を経て、太田記念病院で一般外科研修、大阪大学医学部心臓外科入局外科医として研鑽をつむ</p>
                    <p>2017年 Yale University Hospital Clinical Fellow</p>
                    アメリカ留学を機会に一旦立ち止まって、今後の人生を考える決意をする
                    <p>2019年　Tokyo Gs Academy にてプログラミングに出会う</p>
                    <p>2020年　BlockAidを起業</p>
                    <p>2021年3月〜株式会社AMIにエンジニアとしてJoin</p>
                            7月〜York University(UK) Computer Science Master Cource 就学中
                </div>
            </div>
            <div class='profile-lower-wrapper'>
                <p>主な資格等</p>
                <p>
                    医師免許、USMLE Complete, 外科専門医、心臓外科専門医、産業医専門医<br/>
                    Duolingo English 120, 統計検定２級、AtCoder 緑
                </p>
                <p>趣味</p>
                <p>ピアノ、ランニング、釣り、ラグビー観戦</p>
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
    background: rgb(216, 157, 157);
    height:800px;
}
.profile-image-wrapper{
    width:40%;
    height:500px;
    background: rgb(174, 237, 111);
    padding:10px;
    display: flex;
    align-items: center;
}
.history-wrapper{
    width:60%;
    height:500px;
    background: rgb(108, 165, 250);
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
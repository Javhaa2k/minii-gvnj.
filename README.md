<!DOCTYPE html>
<html lang="mn">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Миний Гүнжид</title>

<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

body{
    font-family:Arial, sans-serif;
    background:linear-gradient(135deg,#ff9a9e,#fad0c4);
    min-height:100vh;
    display:flex;
    justify-content:center;
    align-items:center;
    overflow:hidden;
    padding:20px;
}

.page{
    display:none;
    width:100%;
    max-width:700px;
    text-align:center;
}

.active{
    display:block;
}

.card{
    background:rgba(255,255,255,0.95);
    padding:30px 20px;
    border-radius:25px;
    box-shadow:0 10px 30px rgba(0,0,0,0.2);
}

h1{
    color:#ff3366;
    margin-bottom:25px;
    font-size:clamp(28px,6vw,45px);
}

button{
    padding:14px 35px;
    border:none;
    border-radius:30px;
    margin:10px;
    font-size:18px;
    cursor:pointer;
    transition:0.3s;
}

.yes{
    background:#ff3366;
    color:white;
}

.no{
    background:#666;
    color:white;
}

button:hover{
    transform:scale(1.1);
}

p{
    line-height:1.9;
    font-size:18px;
    color:#444;
    word-wrap:break-word;
    overflow-wrap:break-word;
}

.red{
    color:red;
    cursor:pointer;
    font-weight:bold;
}

.letter{
    max-height:70vh;
    overflow-y:auto;
    text-align:left;
}

.poem{
    white-space:pre-line;
    text-align:center;
    font-size:22px;
    line-height:2;
    word-wrap:break-word;
    overflow-wrap:break-word;
}

.heart{
    position:fixed;
    color:red;
    font-size:30px;
    animation:fly 3s linear forwards;
}

@keyframes fly{
    0%{
        transform:translateY(0) scale(1);
        opacity:1;
    }
    100%{
        transform:translateY(-700px) scale(2);
        opacity:0;
    }
}

/* Утасны тохиргоо */
@media(max-width:600px){

    .card{
        padding:25px 15px;
    }

    p{
        font-size:16px;
    }

    .poem{
        font-size:20px;
        line-height:1.8;
        white-space:pre-line;
        word-break:break-word;
    }

    button{
        width:120px;
    }
}
</style>
</head>
<body>

<!-- Эхний нүүр -->
<div class="page active" id="page1">
    <div class="card">
        <h1>Миний гүнжээ намайг уучлаарай</h1>

        <button class="yes" onclick="openLetter()">
            Тийм
        </button>

        <button class="no" onclick="errorMsg()">
            Үгүй
        </button>
    </div>
</div>

<!-- Захиа -->
<div class="page" id="page2">
    <div class="card letter">

        <p>
        Миний гүнжээ энэ захиаг унших өдөр цаг минутын мэндийг хүргэе.
        Бяцхан гүнжийгээ гомдоосондоо чин сэтгэлээсээ уучлалт хүсэж байна.
        Хайр нь зөндөө гэмшиж байгаа.

        Миний хайр нь наддаа маш үнэ цэнтэй учраас чамайгаа ингэж гомдоосондоо өөрийгөө буруутгаж байна.
        Би өнгөрснөө өөрчилж чадахгүй ч цаашид алдаагаа давтахгүй байхын төлөө хичээх болно.
        Хайрынхаа итгэлийг алдахгүй байхын төлөө хичээх болно.

        Хэрэв боломж өгвөл би хайрынхаа инээмсэглэж байхыг хархын төлөө бүгдийг хийх болно.
        Намайг уучлах эсэх нь миний гүнжийн шийдвэр ч гэсэн миний уучлалт чин сэтгэлээсээ гэдгийг мэдээсэй гэж хүсэж байна.

        Миний гүнжээ хайр нь энэ үгийг маш их хэлсэн байхалдаа магадгүй хайрыгаа залхатлан хэлсэн байх гэхдээ хайрыгаа уучлаарай.

        Бүхнээс илүү хайртай шүү. ❤️
        </p>

        <br><br>

        <p style="text-align:center">
            Хэрэв зөвхөн танд зориулж зохиосон шүлгийг уншихыг хүсвэл
            <span class="red" onclick="openPoem()">энд</span>
            дарна уу.
        </p>

    </div>
</div>

<!-- Шүлэг -->
<div class="page" id="page3">
    <div class="card">
        <div class="poem">
Чамгүй өдрүүд даанч уйтгартай юм
Хэрвээ чи минь сонсоно гэвэл
Энэ дэлхийг цуурайттал
Энэхэн цээжээ хагартал
Ганцхан чамд л хайртай гэж
Орилмоор байна
Тэр минь харанхуй шөнийн
Одтой тэнгэр
Гэрэл, сүүдрийн төгс зохицол
Гоо үзэсгэлэнгийн оршихуй ❤️
        </div>
    </div>
</div>

<script>

function errorMsg(){
    alert("Алдаа гарлаа!");
}

function openLetter(){

    document.getElementById("page1").classList.remove("active");
    document.getElementById("page2").classList.add("active");

    for(let i=0;i<35;i++){

        let heart=document.createElement("div");
        heart.className="heart";
        heart.innerHTML="❤️";

        heart.style.left=Math.random()*100+"vw";
        heart.style.top="100vh";

        document.body.appendChild(heart);

        setTimeout(()=>{
            heart.remove();
        },3000);
    }
}

function openPoem(){

    document.getElementById("page2").classList.remove("active");
    document.getElementById("page3").classList.add("active");
}

</script>

</body>
</html>

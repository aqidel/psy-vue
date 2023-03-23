<template>
  <main>
    <article id="get-started">
      <div class="max-width-wrap">
        <h1>Создавая Пути к Счастью</h1>
        <p>Начните заботиться о себе с помощью арт-терапии!</p>
        <p>Давайте познакомимся в бесплатном получасовом вступительном сеансе!</p>
        <a href="mailto:psyrudenko@yandex.ru">Записаться на сеанс</a>
        <p>Елена Руденко, практикующий психолог</p>
      </div>
    </article>
    <article id="art-therapy"></article>
    <article id="about-me"></article>
    <article id="online"></article>
    <article id="appointments"></article>
    <article id="contact"></article>
  </main>
  <footer></footer>
</template>

<style>

@font-face {
  font-family: Montserrat Bold;
  src: url(@/assets/fonts/Montserrat-Bold.ttf);
}

@font-face {
  font-family: OpenSans Regular;
  src: url(@/assets/fonts/OpenSans-Regular.ttf);
}

@font-face {
  font-family: OpenSans Bold;
  src: url(@/assets/fonts/OpenSans-Bold.ttf);
}

body {
  margin: 0;
}

#get-started {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 100px 24px 40px;
  background-image: linear-gradient(to bottom, rgba(0, 0, 0, 0.25) 0%, rgba(0, 0, 0, 0.25) 100%), url(@/assets/img/background.webp);
  background-position: center center;
  background-repeat: no-repeat;
  background-size: cover;
}

#get-started h1 {
  margin: 0 0 8px 0;
  font-family: Montserrat Bold, sans-serif;
  font-size: 40px;
  font-weight: 700;
  line-height: 48px;
  text-align: center;
  color: rgb(247, 247, 247);
}

#get-started p {
  margin: 0;
  font-family: OpenSans Regular, sans-serif;
  font-size: 22px;
  font-weight: 400;
  line-height: 33px;
  text-align: center;
  color: rgb(247, 247, 247);
}

#get-started a {
  display: block;
  margin: 24px 0;
  border-radius: 4px;
  padding: 10px 32px;
  background-color: rgb(230, 148, 101);
  font-family: OpenSans Bold, sans-serif;
  font-size: 14px;
  font-weight: 700;
  line-height: 30px;
  text-decoration: none;
  text-transform: uppercase;
  text-align: center;
  color: rgb(0, 0, 0);
}

#get-started a:hover {
  background-color: rgb(236, 183, 160);
}

</style>
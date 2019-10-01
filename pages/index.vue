<template>
  <div class="container-fluid px-0">
    <article class="main-image">
      <section>
        <h1>Portfolio</h1>
        <span>Template</span>
        <button class="btn btn-xl btn-light" @click="scrollTo('find-more')">Find Out More</button>
      </section>
    </article>

    <article id="find-more" class="white-section">
      <section>
        <h3>SEC2</h3>
        <span>PPPPP</span>
        <button class="btn btn-xl btn-dark" @click="scrollTo('offers')">What We Offer</button>
      </section>
    </article>

    <article id="offers" class="blue-section">
      <section class="container">
        <h2>What We Offer</h2>
        <div class="row">
          <div class="col-lg-3 col-md-6 mb-5 mb-lg-0" 
               v-for="(offer,index) in offers"
               :key ="index"
          >
            <div class="icon mx-auto"><i class="fas" :class="offer.icon"></i></div>
            <h4>{{ offer.title }}</h4>
            <span>{{ offer.description }}</span>
          </div>
        </div>
      </section>
    </article>

    <article class="second-image">
      <section>
        <h2>Welcome to <i>your</i><br>next website!</h2>
        <button class="btn btn-xl btn-dark" @click="scrollTo('recent-projects')">Recent Projects</button>
      </section>
    </article>

    <article id="recent-projects" class="white-section">
      <section class="container">
        <h3>Recent Projects</h3>
        <div class="row no-gutters">
          <div class="col-log-6" v-for="(project,index) in recentProjects" :key="index">
            <a href="" class="portfolio-item">
              <span class="caption">
                <span class="caption-content">
                  <h2>{{ project.title}}</h2>
                  <p class="mb-0">{{ project.description}}</p>
                </span>
              </span>
              <img class="img-fluid" :src="require('../assets/'+project.img)" alt=""/>
            </a>
          </div>
        </div>
      </section>
    </article>

    <article class="blue-section">
      <section class="container">
        <section>
          <h2>Have a nice day</h2>
          <button class="btn btn-xl btn-light mr-4" @click="scrollTo('app')">Click Me</button>
          <button class="btn btn-xl btn-dark" @click="scrollTo('app')">Look at Me</button>
        </section>
      </section>
    </article>
  </div>
</template>

<script>
export default {
  data: () => {
    return {
      offers: [
        {
          icon : 'fa-mobile',
          title : 'Responsive',
          description : 'Looks great on any screen size'
        },
        {
          icon : 'fa-pencil-alt',
          title : 'Redesigned',
          description : 'Freshly redesigned for Vue JS'
        },
        {
          icon : 'fa-thumbs-up',
          title : 'Favorited',
          description : 'Millions of users like us'
        },
        {
          icon : 'fa-question-circle',
          title : 'Questions?',
          description : 'We answer all questions'
        },
      ],
      recentProjects:[
        {
          img : 'main_image.jpg',
          title : 'Stationary',
          description : 'des'
        },
        {
          img : 'main_image.jpg',
          title : 'Ice Cream',
          description : 'ice cream'
        },
        {
          img : 'main_image.jpg',
          title : 'Strawberries',
          description : 'Strawberries'
        }
      ]
    }
  },
  methods : {
      scrollTo(element){
        const el = document.querySelector('#'+element);
        el.scrollIntoView({
          behavior: 'smooth',
          block: 'start'
        });
      }
  }
}
</script>

<style lang="scss">
  @import url('https://use.fontawesome.com/releases/v5.8.1/css/all.css');

  article {
    display: flex;
    justify-content : center;
    align-items: center;
    width: 100%;
    padding : 0 10px;
  }

  .btn-xl {
    padding: 20px 35px;
    font-family: serif;
    font-size: 1.25rem;
  }

  .main-image, .second-image{
    min-height: 100vh;
    background-size: cover;
    padding : 0 10px;
    text-align: center;

    h1 {
      font-size : 5rem;
      font-weight: bold;
      margin-bottom : 30px;
    }

    h2 {
      font-size : 3rem;
      font-weight: bold;
      margin-bottom : 30px;
    }

    span {
      display: block;
      padding-bottom: 30px;
      font-size: 1.6rem;
      font-weight: bold;
    }
  }

  .main-image{
    background : url('../assets/main_image.jpg') center center;
  }

  .second-image{
    background : url('../assets/main_image.jpg') center center;
  }

  .white-section {
    padding : 120px 10px;
    background-color: #fff;
    text-align: center;

    h3 {
      font-size: 2rem;
      font-weight: bold;
    }

    span {
      display: block;
      padding-bottom: 30px;
      font-size: 1.25rem;
    }

    .row {
      padding-top: 50px;
    }

    .portfolio-item {
      display: block;
      position: relative;
      overflow: hidden;

      .caption {
        display: flex;
        height: 100%;
        width: 100%;
        position : absolute;
        top: 0;
        bottom: 0;
        z-index: 1;
        background-color: rgba($color: #000000, $alpha: .2);
        transition: transform .2s linear;

        .caption-content {
          text-align : left;
          color: #fff;
          margin : auto 2rem 2rem;
        }
      }

      img {
        transition: transform .2s linear;
      }

      &:hover {
        img {
          transform: scale(.9);
        }

        .caption {
          transform: scale(.9);
          background-color: rgba($color: #000000, $alpha: .2);
        }
      }
    }
  }

  .blue-section {
    padding: 120px 10px;
    background-color: #1d809f;
    color : #fff;
    text-align: center;

    h2 {
      font-size: 3rem;
      font-weight: bold;
      margin-bottom: 50px;
    }

    h4 {
      font-size: 1.6rem;
      padding-top: 20px;
    }

    .icon {
      display: flex;
      justify-content: center;
      align-items: center;
      width: 120px;
      height: 120px;
      background-color: #fff;
      color: #1d809f;
      border-radius: 50%;

      i {
        font-size: 2rem;
      }
    }
  }
</style>

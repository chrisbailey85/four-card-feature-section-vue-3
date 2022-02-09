<template>

  <transition tag="header" @before-enter="beforeEnter" @enter="enter" appear>
    <div>
        <h1 class="heading">
          Reliable, efficient delivery 
          <span class="heading__span"> Powered by Technology</span>
        </h1>
        <p class="header__text">
          activity to identify project roadblocks Our Artificial Intelligence
          powered tools use millions of project data points to ensure that your
          project is successful
        </p>
    </div>
  </transition>

 <main class="main">
   <transition-group tag="div" class="cards"  @before-enter="beforeEnterCards" @enter="enterCards" appear>
   <Card  v-for="(card) in cards" 
   :key="card.id" 
   :title="card.title" 
   :text="card.text" 
   :icon="card.icon" 
   :borderColor="card.borderColor"
   :data-index="card.id"
   />
   </transition-group>
 </main>
</template>

<script>
import Card from '@/components/Card.vue'
import gasp from 'gsap'
export default {
  name: 'App',
  components: {
    Card
  },
    setup() {
      const  cards = [ 
      {
        title: 'Supervisor',
        text: 'Monitors activity to identify project roadblocks',
        icon: 'icon-supervisor.svg',
        borderColor: '#45d3d3',
        id: 1
      },
      {
        title: 'Team Builder',
        text: 'Scans our talent network to create the optimal team for your project',
        icon: 'icon-team-builder.svg',
        borderColor: '#ea5353',
        id: 2
      },
      {
        title: 'Karma',
        text: 'Regularly evaluates our talent to ensure quality',
        icon: 'icon-karma.svg',
        borderColor: '#fcaf4a',
        id: 3
      },
      {
        title: 'Calculator',
        text: 'Uses data from past projects to provide better delivery estimates',
        icon: 'icon-calculator.svg',
        borderColor: '#549ef2',
        id: 4
      }
    ]
        const beforeEnter = (el) => {
           el.style.transform = 'translateY(-100px)'
           el.style.opacity = 0
        }
        const enter = (el) => {
          gasp.to(el, {
            y: 0,
            opacity: 1,
            duration: 1,
            ease: 'slow'
          })
        }
        const beforeEnterCards = (el) => {
           el.style.transform = 'translateY(100px)'
           el.style.opacity = 0
        }
        const enterCards = (el, index) => {
          gasp.to(el, {
            y: 0,
            opacity: 1,
            duration: 1.2,
            ease: 'elastic.out',
            delay: el.dataset.index / 1.3
          })
        }
        return {beforeEnter, enter, cards, beforeEnterCards , enterCards}
    }
}
</script>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  padding: 3rem 1rem;
  min-height: 100vh;
  background-color: #fafafa;
  font-family: "Poppins", sans-serif;
  display: grid;
  place-items: center;
  line-height: 1.5;
}
.heading {
  color: #4c4e61;
  font-weight: 200;
  font-size: 1.5rem;
  margin: 1rem auto;
  width: max-content;
}
.heading__span {
  display: block;
  font-weight: 600;
}
.header__text {
  color: #a3a5ae;
  font-size: 0.9rem;
  text-align: center;
  max-width: 60ch;
  margin: 0 auto;
}
.cards {
  display: grid;
  margin-top: 3rem;
  gap: 2rem;
  place-items: center;
}
@media (min-width: 375px) {
  body {
    padding: 3rem 2rem;
  }
}
@media (min-width: 768px) {
  .heading {
    font-size: 2.5rem;
  }
  .header__text {
    max-width: 70ch;
  }
  .cards {
    grid-template-columns: 1fr 1fr;
  }
}

@media (min-width:1440px) {
  .cards {
    grid-template-rows: repeat(4, 125px);
    grid-template-columns: 1fr 1fr 1fr;
    gap: 1rem 2rem;
    margin-top: 4rem;
    place-items: unset;
  }
  .card:nth-child(1) {
    grid-row: 2/3;
  }
  .card:nth-child(2) {
    grid-column: 2/3 ;
  }
  .card:nth-child(3) {
    grid-row: 3/-1;
    grid-column: 2/3;
  }
  .card:nth-child(4) {
    grid-row: 2/3;
    grid-column: 3/-1;

  }
}

/* .fade-enter-from {
  opacity: 0;
  transform: translateY(-100px);
}

.fade-enter-active {
  transition: all 2s ease-in;
} */
</style>

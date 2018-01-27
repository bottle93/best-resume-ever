<template>
<div id="resume3" class="resume">
  <div class="resume-header">
    <div class="triangle"></div>
    <div class="person-header">
      <div class="person-wrapper">
        <div class="person">
          <div class="name">{{person.name.first}} {{person.name.middle}} {{person.name.last}}</div>
          <div class="position">{{person.position}}</div>
        </div>
      </div>

    </div>
  </div>
  <div class="resume-content">
    <div class="contact">
      <h3>{{ lang.contact }}</h3>
      <div class="contact-container">
        <div class="col-1">
          <span class='display-loc'><i class="material-icons">email</i><a :href="'mailto:'+person.contact.email"> {{person.contact.email}}</a></span>
          <span class='display-loc'><i class="material-icons">phone</i><a :href="'tel:'+person.contact.phone">{{person.contact.phone}}</a></span>
        </div>
        <div class="col-2">
          <span class='display-loc'>
            <i class="fa fa-github"></i>
            <a v-if="person.contact.github" :href="'https://github.com/'+person.contact.github">
            https://github.com/{{person.contact.github}}</a>
          </span>
          <span class='display-loc'>
            <i class="material-icons">language</i>
            <a v-if="person.contact.website" :href="person.contact.website">
            {{person.contact.website}}
            </a>
          </span>
        </div>
      </div>

    </div>
    <div class='about'>
      <h3>
        {{ lang.about }}
      </h3>
      <div class="about-container">
        {{ person.name.about }}
      </div>
    </div>
    <div class="experience">
      <h3>{{ lang.experience }}</h3>

      <div class="experience-block" v-for="experience in person.experience" :key="experience.company">
        <div class="row">
          <span class="company"> {{experience.company}} </span>
          <span class="time-period"> {{experience.timeperiod}}</span>
          <!--<i class="material-icons">details</i>-->
        </div>
        <div class="row to-space">
          <span class="job-title"> {{experience.position}} </span>
        </div>
        <div class="row row-job-description">
          <span class="job-description">{{experience.descriptionone}} </span>
          <span class="job-description">{{experience.descriptiontwo}} </span>
        </div>
      </div>
    </div>
    <div class="education">
      <h3>{{ lang.education }}</h3>
      <div class="education-block" v-for="education in person.education" :key="education.degree">
        <div class="row">
          <span class="degree">{{education.degree}}</span><span class="time-period"> {{education.timeperiod}}</span>
        </div>
        <div class="row to-space">
          <span class="degree-description">{{education.description}}</span>
        </div>
        <div class="row">
          {{ education.coursedes }}
        </div>
      </div>
    </div>
    <div class="skill-section">
      <h3>{{ lang.skills }}</h3>
      <div class="skills" v-for="skill in person.skills" :key="skill.name">
        <div class="skill-block">
          <i class="material-icons">send</i>
          <span class="skill">{{skill.name}}</span>
        </div>
      </div>
    </div>
  </div>
  <div>
    <p class="clause">
      Wyrażam zgodę na przetwarzanie moich danych osobowych dla potrzeb niezbędnych do realizacji procesu rekrutacji
      (zgodnie z Ustawą z dnia 29.08.1997 roku o Ochronie Danych Osobowych; tekst jednolity: Dz. U. 2016 r. poz. 922).
    </p>
  </div>
</div>
</template>

<script>
import Vue from 'vue';
import { getVueOptions } from './options';

let name = 'oblique';
export default Vue.component(name, getVueOptions(name));
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="less" scoped>
#resume3 {
  font-size: 18px;
  font-family: sans-serif;
  font-weight: 300;
  padding-bottom:50px;
  a, a:focus, a:hover {
    color:black;
    text-decoration:none;
  }
  h3 {
    font-size: 23px;
    font-weight:bold;
    margin:15px 0 5px 0;
  }
  .resume-header .triangle {
    width:0;
    height:0;
    border-style:solid;
    border-width:300px 0 0 1500px;
    border-color:#006064 transparent transparent transparent;
    position:absolute;
    left:-400px;
    top:0;
  }
  .person-header {
    position:absolute;
    z-index:20;
    right:5%;
    top: 30px;
    .person-wrapper {
      overflow:hidden;
      position:relative;
    }
    .person {
      float:right;
      color:white;
      margin-right:50px;
    }
    .name {
      text-transform:uppercase;
      font-size:50px;
      display:table-caption;
      text-align:right;
      line-height:1.0;
      font-weight:bold;
    }
    .position {
      font-size:20px;
      display:table-caption;
      text-align:right;
      line-height:1.0;
      margin-top:10px;
    }
  }
  .resume-content {
    margin-top:160px;
    margin-left:5%;
    width:90%;
    .experience .experience-block {
      line-height:1;
      margin-bottom:10px;
      .row:first-child {
        font-size:20px;
        font-weight: bold;
        color: #006064;
        i {
          font-size:17px;
        }
      }
      .job-title {
        font-weight: 600;
        color: #333;
      }
    }
    .experience .experience-block:first-of-type {
      width:80%;
    }
  }
  .education-block {
    line-height:1;
    margin-bottom:10px;
    .row:first-child {
      font-size:20px;
      font-weight: bold;
      color: #006064;
    }

  .degree-description {
    font-weight: 600;
    color: #333;
  }
  }
  .about{
    //margin-top: 110px;
  }
  .skill-section{
    height: 150px;
  }

  .skill-section .skills {
    width:100%;
    .skill-block {
      width:50%;
      float:left;
      i {
        font-size:17px;
        margin-right:15px;
        color: #999;
      }
      .skill {
        font-size:20px;
      }
    }
  }
  .skills-other {
    display:inline-block;
    font-size:20px;
    margin-top:0;
    line-height:1;
  }
  .contact {
    .contact-container {
      display: flex;
      justify-content: space-between;
      .col-1, .col-2{
        display: flex;
        flex-direction: column;
        align-content: center;
        .display-loc {
          display: flex;
          align-items: center;
        }
        i {
          margin: 5px;
          color: #999;
          font-size: 35px;
        }
      }
      .col-1 {
        width: 50%;
      }
    }
  }
}
  .to-space {
    margin-bottom: 5px;
  }

  .time-period {
    color: #666;
    font-size: smaller;
    font-weight: lighter;
  }

  .clause {
    text-align: center;
    font-size: smaller;
    color: #999;
    margin-top: 20px;
  }

  .row-job-description {
    display: flex;
    flex-direction: column;
    .job-description {
      padding: 2px;
    }
  }
</style>

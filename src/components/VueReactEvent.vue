<template>
  <div v-if="!isEvent" :class="dayClass">{{ this.date.getDate() }}</div>
  <div v-else @click="toggleInfo" :class="eventClasses">
    {{ this.date.getDate() }}
    <p className="name">{name}</p>
    <div className={infoClass}>
      <div key={ev.name}>
        <p className="title">{ev.name}</p>
        {ev.description.trim()?
        <p className="description">
          {ev.description}<br/><br/>
          {ev.link.trim()? <a className="btn btn-dark" href={ev.link} target="_blank" rel="noopener noreferrer">Mehr erfahren</a>: " "}
        </p>
        : <p className="description">
        {ev.link.trim()?
        <a className="btn btn-dark" href={ev.link} target="_blank" rel="noopener noreferrer">
          Mehr erfahren
        </a>
        : " "}
      </p>}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "VueReactDay",
  props:{
    date:{
      type: Date,
      required: true
    },
    oldMonth:{
      type:Boolean,
      default: false
    },
    events:{
      type:Array
    }
  },
  data(){
    return {
      infoShow:false,
    }
  },
  computed:{
    dayClass(){
      let today = new Date();
      let dayClass = "date " + (this.oldMonth?"oldMonth ":" ");
      if(this.date.getDate() === today.getDate() && this.date.getMonth() === today.getMonth()){
        dayClass += " today";
      }
      return dayClass;
    },
    isEvent(){
      for(let i = 0; i< this.events.length; i++) {
        if (this.date.getDate() === parseInt(this.events[i].day) && this.date.getMonth() + 1 === parseInt(this.events[i].month) && this.date.getFullYear() === parseInt(this.events[i].year)) {
          return true;
        }
      }
      return false;
    },
    eventClasses(){
      return this.dayClass + " event weekday-" + this.date.getDay();
    }
  },
  methods:{
    toggleInfo(){
      this.infoShow = !this.infoShow;
    }
  }
}
</script>

<style scoped>

</style>
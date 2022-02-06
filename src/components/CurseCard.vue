<template>
  <div class="card" >
    <h3>{{ title }}</h3>
    <span>{{ moment }}</span>
    <p v-if="type === 'seminar' && duration" >Семинар {{numberToDate(duration)}}</p>
    <p v-if="type === 'training' && duration" >Повышение  квалификации {{numberToDate(duration)}}</p>
    <p v-if="type === 'seminar' && dateStart">Сессия {{ dateFormat(dateStart) }}</p>
    <p v-if="type === 'training ' && dateStart">Начало {{ dateFormat(dateStart) }}</p>
    <p v-if="description != ''">{{ description }}</p>
    <p class="test" v-if="curators">{{ (curators && curators.length) <= 1 ? 'Куратор:' : 'Кураторы:'}}
      <span v-for="curator in curators" :key="curator">{{curator}}, </span>
    </p>
    <p class="test" v-if="methodists">
      {{ methodists && methodists.length <= 1 ? "Методист:" : "Методисты:"}}
      <span v-for="methodist in methodists" :key="methodist">{{methodist}}, </span>
    </p>
<!--    <card-button  v-if="seminars"
        v-bind="seminar"
    ></card-button>-->
    <a v-if="type==='seminar'" :href=link>{{ price }}</a>
    <a v-else :href=link>Выбрать тариф</a>
  </div>
</template>

<script>
/*import CardButton from "@/components/CardButton";*/
import moment from 'moment'

export default {
  props: ['title', 'type', 'description','curators','methodists','price', 'link','dateStart','moment','duration'],
  name: "CurseCard",
  components: {
  /*moment,
  'card-button': CardButton*/

  },
  methods: {
    dateFormat : function (date) {
      return moment(date, 'YYYY-MM-DD').locale('ru').format('Do MMMM');
    },
    numberToDate : function (date) {
      return moment.duration(date, "weeks").locale("ru").humanize();
    }
  }

}

</script>

<style scoped>

</style>
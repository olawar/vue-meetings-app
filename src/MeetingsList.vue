<template>
  <table v-if="meetings.length > 0">
    <thead>
    <tr>
      <th>Nazwa spotkania</th>
      <th>Opis</th>
      <th>Uczestnicy</th>
      <th></th>
    </tr>
    </thead>
    <tbody>
    <tr v-for="meeting in meetings" :key="meeting.name">
      <td>{{ meeting.name }}</td>
      <td>{{ meeting.description }}</td>
      <td>
        <ul v-if="meeting.participants.length > 0">
          <li v-for="(participant, index) in meeting.participants" :key="index">{{ participant }}</li>
        </ul>
      </td>
      <td>
        <button v-if="meeting.participants.indexOf(user) < 0" class="button button-outline" @click="subscribe(meeting)">Zapisz się</button>
        <button v-if="meeting.participants.length < 1">Usuń puste spotkanie</button>
        <button v-if="meeting.participants.indexOf(user) > -1" class="button button-outline" @click="unsubscribe(meeting)">Wypisz się</button>
      </td>
    </tr>
    </tbody>
  </table>
</template>

<script>
  export default {
    props: ['meetings', 'user'],
    methods: {
      subscribe(meeting) {
        this.$emit('subscribe', meeting);
      },
      unsubscribe(meeting) {
        this.$emit('unsubscribe', meeting);
      }
    }
  }
</script>

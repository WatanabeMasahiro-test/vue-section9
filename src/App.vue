<!--**
    *** 以下、未解決 ***
    * EventIsPrivate,
    * EventAgeConditions,
    * EventParticipation,
    * EventMarriage,
    **  -->
<template>
  <div class="container">
    <h2>イベントのフォーム</h2>
    <hr class="py-1">
    <div class="row">
      <div class="col-6">
        <form action="#" method="GET">
          <div class="mb-3">
            <label for="title" class="form-label d-block">タイトル</label>
            <input 
              id="title" 
              name="title" 
              type="text" 
              class="form-controll" 
              v-model="eventData.title"
            >
            <!--*** v-modelの別の書き方 <input type="text"> の場合 ***
              <input @input="eventData.title = $event.target.value"> 
              <input @change="eventData.title = $event.target.value"> ⏪これはv-model.lazyの場合(@change) 
            -->
            <pre class="text-secondary">{{ eventData.title }}</pre>
            <hr>
          </div>
          <div class="mb-3">
            <label for="host" class="form-label d-block">主催者</label>
            <input 
              id="host" 
              name="host" 
              type="text" 
              class="form-controll" 
              v-model.trim="eventData.host"
            >
            <pre class="text-secondary">{{ eventData.host }}</pre>
            <hr>
          </div>
          <div class="mb-3">
            <label for="detail" class="form-label d-block">イベントの内容</label>
            <textarea 
              id="detail" 
              name="detail" 
              cols="15" 
              rows="5" 
              class="form-controll d-inline-block mx-1" 
              v-model="eventData.detail"
            ></textarea>
            <pre class="text-secondary d-inline-block align-top mx-1">{{ eventData.detail }}</pre>
            <hr>
          </div>
          <div class="mb-3">
            <label for="mail" class="form-label d-block">メールアドレス</label>
            <input 
              id="mail" 
              name="mail" 
              type="email" 
              class="form-controll" 
              v-model.lazy="eventData.mail"
            >
            <pre class="text-secondary">{{ eventData.mail }}</pre>
            <hr>
          </div>
          <div class="mb-3">
            <label for="maxNumber" class="form-label d-block">最大値</label>
            <input 
              id="maxNnumber" 
              name="maxNnumber" 
              type="number" 
              class="form-controll" 
              v-model.number="eventData.maxNumber"
            >
            <pre class="text-secondary">{{ eventData.maxNumber }}</pre>
            <hr>
          </div>
          <div class="mb-3">
            <div class="form-check">
              <input 
                id="isPrivate" 
                name="checkbox" 
                type="checkbox" 
                class="form-check-input" 
                v-model="eventData.isPrivate" 
                @change="changePrivate()" 
                checked
              >
              <label class="form-check-label" for="isPrivate">非公開</label>
              <pre class="text-secondary">{{ eventData.isPrivate }}</pre>
            </div>
            <hr>
          </div>
          <div class="mb-3">
            <p class="fw-bold">【参加条件】</p>
            <div class="form-check form-check-inline">
              <input 
                id="teenager" 
                name="age" 
                value="10" 
                type="checkbox" 
                class="form-check-input" 
                v-model="eventData.ageTarget" 
                @change="alertAge" 
              >
              <label class="form-check-label" for="teenager">10代</label>
            </div>
            <div class="form-check form-check-inline">
              <input 
                id="twenties" 
                name="age" 
                value="20" 
                type="checkbox" 
                class="form-check-input" 
                v-model="eventData.ageTarget" 
                @change="alertAge" 
              >
              <label class="form-check-label" for="twenties">20代</label>
            </div>
            <div class="form-check form-check-inline">
              <input 
                id="thirties" 
                name="age" 
                value="30" 
                type="checkbox" 
                class="form-check-input" 
                v-model="eventData.ageTarget" 
                @change="alertAge" 
              >
              <label class="form-check-label" for="thirties">30代</label>
            </div>
            <pre class="text-secondary">{{ eventData.ageTarget }}</pre>
            <hr>
          </div>
          <div class="mb-3">
            <p class="fw-bold">【参加費】</p>
            <div class="form-check">
              <input 
                id="participation-free" 
                name="participation-fee" 
                value="0" 
                type="radio" 
                class="form-check-input" 
                v-model="eventData.price" 
                checked 
              >
              <label class="form-check-label" for="participation-free">無料</label>
            </div>
            <div class="form-check">
              <input 
                id="participation-paid" 
                name="participation-fee" 
                value="2800" 
                type="radio" 
                class="form-check-input" 
                v-model="eventData.price" 
              >
              <label class="form-check-label" for="participation-paid">有料</label>
            </div>
            <pre class="text-secondary">{{ eventData.price }}</pre>
            <hr>
          </div>
          <div class="mb-3">
            <!-- checkedの代わりに、v-modelのデータをtrueにする -->
            <div class="form-check form-switch">
              <input 
                id="marriage-select" 
                name="marriage-select" 
                value="" 
                type="checkbox" 
                class="form-check-input" 
                v-model="eventData.marriage" 
              >
              <label class="form-check-label" for="marriage-select">結婚歴</label>
            </div>
            <pre class="text-secondary">{{ eventData.marriage }}</pre>
            <hr>
          </div>
          <div class="mb-3">
            <p class="fw-bold">【開催場所】</p>
            <div class=""><!-- 複数選択の場合、multiple -->
              <select 
                name="venue" 
                class="form-select" 
                aria-label="都道府県の選択" 
                v-model="eventData.location"
              >
                <option selected>選択してください</option><!-- 無効表示選択の場合、disabled -->
                <option 
                  v-for="location in locations" 
                  :key="location"
                  :value="location"
                >{{ location }}</option>
              </select>
            </div>
            <pre class="text-secondary">{{ eventData.location }}</pre>
            <hr>
          </div>
          <button type="submit" class="btn btn-primary">送信</button>
        </form>
      </div>
      <div class="col-6" style="background-color: beige;">
        <form action="#" method="GET">
          <EventTitle v-model="eventData.title"></EventTitle>
            <!--*** v-modelの別の書き方 コンポーネント の場合 ***
            <EventTitle 
              :value="eventData.title" 
              @input="eventData.title = $event"
            ></EventTitle> -->
          <EventHost v-model="eventData.host"></EventHost>
          <EventDetail v-model="eventData.detail"></EventDetail>
          <EventMail v-model="eventData.mail"></EventMail>
          <EventMaxNumber v-model="eventData.maxNumber"></EventMaxNumber>
          <EventIsPrivate v-model="eventData.isPrivate"></EventIsPrivate>
          <EventAgeConditions v-model="eventData.ageTarget"></EventAgeConditions>
          <EventParticipation v-model="eventData.price"></EventParticipation>
          <EventMarriage v-model="eventData.marriage"></EventMarriage>
          <EventLocations v-model="eventData.location"></EventLocations>
          <EventButton></EventButton>
        </form>
      </div>
    </div>

    <hr class="py-1">
  </div>
</template>

<script>
import EventTitle from './components/events/EventTitle.vue'
import EventHost from './components/events/EventHost.vue'
import EventDetail from './components/events/EventDetail.vue'
import EventMail from './components/events/EventMail.vue'
import EventMaxNumber from './components/events/EventMaxNumber.vue'
import EventIsPrivate from './components/events/EventIsPrivate.vue'
import EventAgeConditions from './components/events/EventAgeConditions.vue'
import EventParticipation from './components/events/EventParticipation.vue'
import EventMarriage from './components/events/EventMarriage.vue'
import EventLocations from './components/events/EventLocations.vue'
import EventButton from './components/events/EventButton.vue'
import './assets/css/style.css'

export default {
  components: {
    EventTitle,
    EventHost,
    EventDetail,
    EventMail,
    EventMaxNumber,
    EventIsPrivate,
    EventAgeConditions,
    EventParticipation,
    EventMarriage,
    EventLocations,
    EventButton,
  },
  name: 'App',
  data: () => ({
    locations : [ '東京', 
                  '大阪', 
                  '名古屋',
    ],
    eventData: {
      title     : 'タイトル',
      host      : '主催者名',
      detail    : '詳細は\nこちら',
      mail      : 'aaa@gmail.com',
      maxNumber : 0,
      isPrivate : false,
      ageTarget : [],
      price     : '無料',
      marriage  : true,
      location  : '選択してください',
    }
  }),
  computed: {
    alertAge() {
      var result = '';
      for(let i = 0 ; i < this.eventData.ageTarget.length; ++i) {
        result = ', ' + this.eventData.ageTarget;
      }
      return alert(result.replace(', ' , ''));
    },
  },
  methods: {
    changePrivate() {
      if(this.eventData.isPrivate == true) {
        alert("非公開にしました！！！");
      }
    },
  },
}
</script>

<style>

</style>

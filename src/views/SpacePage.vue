<template>
  <div>
    <MuseumHighlight :museumHighlights="museumHighlights" :badgeImage="badgeImage" />
  </div>
</template>

<script>
import MuseumHighlight from '../components/MuseumHighlight.vue'
import _ from 'lodash'
import moment from 'moment'

export default {
  name: 'SpacePage',
  components: {
    MuseumHighlight
  },
  data() {
    return {
      museumHighlights: null,
      badgeImage: ['https://cdn-icons-png.flaticon.com/512/929/929424.png'],
      spaceHighlights: [
        {
          date: '2020-04-20 12:20:00',
          description:
            'Asteroids are minor planets, especially of the inner Solar System. Larger asteroids have also been called planetoids.',
          id: 1,
          image:
            'https://images.unsplash.com/photo-1506703244717-0f4fb867779d?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=880&q=80',
          name: 'Asteroids'
        },
        {
          date: '2020-05-20 15:50:00',
          description:
            'A comet is an icy, small Solar System body that, when passing close to the Sun, warms and begins to release gases, a process called outgassing.',
          id: 9,
          image:
            'https://images.unsplash.com/photo-1623284577359-a0130bb9a86d?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1470&q=80',
          name: 'Comets'
        },
        {
          date: '2020-05-01 9:22:00',
          description:
            'The term planet is ancient, with ties to history, astrology, science, mythology, and religion.',
          id: 7,
          image:
            'https://img.freepik.com/free-photo/3d-space-scene_1048-5311.jpg?w=740&t=st=1681124680~exp=1681125280~hmac=deb844125efa194bfdaf6905b997fc0c909df57f623a52f1ff7f70fe418b9d47',
          name: 'Planets',
          news: {
            date: '2020-08-18 18:00:00',
            title: 'Attend our talk about Jupiter with Dr. Hogarth'
          },
          quiz: 'https://planetquiz.space'
        },
        {
          date: '2020-07-05 4:10:00',
          description:
            'A meteor shower is a celestial event in which a number of meteors are observed to radiate, or originate, from one point in the night sky.',
          id: 12,
          image:
            'https://images.unsplash.com/photo-1438932150719-500cc59a04cd?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1332&q=80',
          name: 'Meteor showers',
          news: {
            title: 'The Lyrids will peak at on April 21-22 2021, at night'
          }
        }
      ],
      spacePartners: {
        observatory: {
          createdAt: '2020-06-01 11:45:00',
          info: 'The Mauna Kea Observatories (MKO) are a number of independent astronomical research facilities and large telescope observatories that are located at the summit of Mauna Kea on the Big Island of Hawaiʻi, United States.',
          image:
            'https://images.unsplash.com/photo-1444703686981-a3abbc4d4fe3?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1470&q=80',
          name: 'Mauna Kea Observatories'
        }
      }
    }
  },
  computed: {
    allSpaceObjectsArray() {
      const allObjects = _.concat(this.spaceHighlights, Object.values(this.spacePartners).flat())

      return allObjects.map((obj) => {
        const newObj = { ...obj }
        if (newObj.date) {
          newObj.date = moment(newObj.date).format('DD/MM/YYYY')
        }
        if (newObj.news && newObj.news.date) {
          newObj.news.date = moment(newObj.news.date).format('DD/MM/YYYY')
        }
        if (newObj.createdAt) {
          newObj.createdAt = moment(newObj.createdAt).format('DD/MM/YYYY')
        }
        return newObj
      })
    }
  },
  mounted() {
    this.museumHighlights = _.cloneDeep(this.allSpaceObjectsArray)
  }
}
</script>

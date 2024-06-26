<template>
  <div class="container mx-auto">
    <!-- Project heading and meta info -->
    <div>
      <p
        class="
            font-general-medium
            text-left text-3xl
            sm:text-4xl
            font-bold
            text-primary-dark
            dark:text-primary-light
            mt-14
            sm:mt-20
            mb-7
          "
      >
        {{ project.title }}
      </p>
      <div class="flex">
        <div class="flex items-center mr-10">
          <i
            data-feather="clock"
            class="w-4 h-4 text-ternary-dark dark:text-ternary-light"
          />
          <span
            class="
                font-general-medium
                ml-2
                leading-none
                text-primary-dark
                dark:text-primary-light
              "
          >{{ project.publishDate }}</span>
        </div>
        <div class="flex items-center">
          <i
            data-feather="tag"
            class="w-4 h-4 text-ternary-dark dark:text-ternary-light"
          />
          <span
            class="
                font-general-medium
                ml-2
                leading-none
                text-primary-dark
                dark:text-primary-light
              "
          >{{ project.tag }}</span>
        </div>
      </div>
    </div>

    <!-- Project gallery -->
    <div class="grid grid-cols-1 sm:grid-cols-3 sm:gap-10 mt-12">
      <div
        v-for="(item, index) in items"
        :key="index"
        class="mb-10 sm:mb-0"
      >
        <img
          :src="item"
          class="rounded-xl cursor-pointer shadow-lg sm:shadow-none"
        >
      </div>
    </div>

    <!-- Project info -->
    <div class="block sm:flex gap-0 sm:gap-10 mt-14">
      <!-- Single project left section details -->
      <div class="w-full sm:w-1/3 text-left">
        <!-- Single project client details -->
        <div class="mb-7">
          <p
            class="
                font-general-medium
                text-2xl text-secondary-dark
                dark:text-secondary-light
                mb-2
              "
          >
            project.clientTitle
          </p>
          <ul class="leading-loose">
            <li
              v-for="info in project.companyInfos"
              :key="info.id"
              class="
                  font-general-regular
                  text-ternary-dark
                  dark:text-ternary-light
                "
            >
              <span>{{ info.title }}: </span>
              <a
                href="#"
                :class="
                  info.title == 'Website' || info.title == 'Phone'
                    ? 'hover:underline cursor-pointer'
                    : ''
                "
                aria-label="Project website and phone"
              >{{ info.details }}</a>
            </li>
          </ul>
        </div>

        <!-- Single project objectives -->
        <div class="mb-7">
          <p
            class="
                font-general-medium
                text-2xl text-ternary-dark
                dark:text-ternary-light
                mb-2
              "
          >
            project.objectivesTitle
          </p>
          <p
            class="
                font-general-regular
                text-primary-dark
                dark:text-ternary-light
              "
          >
            project.objectivesDetails
          </p>
        </div>

        <!-- Single project technologies -->
        <div class="mb-7">
          <p
            class="
                font-general-medium
                text-2xl text-ternary-dark
                dark:text-ternary-light
                mb-2
              "
          >
            project.techTitle
          </p>
          <p
            class="
                font-general-regular
                text-primary-dark
                dark:text-ternary-light
              "
          >
            project.technologies.join(", ")
          </p>
        </div>

        <!-- Single project social sharing -->
        <div>
          <p
            class="
                font-general-medium
                text-2xl text-ternary-dark
                dark:text-ternary-light
                mb-2
              "
          >
            project.socialTitle
          </p>
          <div class="flex items-center gap-3 mt-5">
            <a
              v-for="social in project.socialSharings"
              :key="social.id"
              :href="social.url"
              target="__blank"
              aria-label="Share Project"
              class="
                  bg-ternary-light
                  dark:bg-ternary-dark
                  text-gray-400
                  hover:text-primary-dark
                  dark:hover:text-primary-light
                  p-2
                  rounded-lg
                  shadow-sm
                  duration-500
                "
            ><i
              :data-feather="social.icon"
              class="w-4 lg:w-5 h-4 lg:h-5"
            /></a>
          </div>
        </div>
      </div>

      <!-- Single project right section details -->
      <div class="w-full sm:w-2/3 text-left mt-10 sm:mt-0">
        <p
          class="
              font-general-medium
              text-primary-dark
              dark:text-primary-light
              text-2xl
              font-bold
              mb-7
            "
        >
          {{ project.detailsTitle }}
        </p>
        <p
          v-for="projectDetail in project.projectDetails"
          :key="projectDetail.id"
          class="
              font-general-regular
              mb-5
              text-lg text-ternary-dark
              dark:text-ternary-light
            "
        >
          {{ projectDetail.details }}
        </p>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
const items = [
  'https://picsum.photos/600/800?random=1',
  'https://picsum.photos/600/800?random=2',
  'https://picsum.photos/600/800?random=3'
]

const project = {
  id: '260d1271-f1f2-4bc9-a5eb-05a89c8cccdb',
  title: 'Google Health Platform',
  category: 'Web Application',
  img: 'images/web-project-2.jpg',
  publishDate: 'Nov 04, 2021',
  tag: 'UI / Frontend',
  clientTitle: 'About Client',
  objectivesTitle: 'Objective',
  objectivesDetails:
        'Lorem ipsum dolor sit amet consectetur adipisicing elit. Optio, natus! Quibusdam enim quod in esse, mollitia molestias incidunt quas ipsa accusamus veniam.',
  techTitle: 'Tools & Technologies',
  detailsTitle: 'Challenge',
  socialTitle: 'Share This',
  projectImages: [
    {
      id: 'rand1',
      title: 'Uber Project Management UI',
      img: '../images/ui-project-1.jpg'
    },
    {
      id: 'rand2',
      title: 'Uber Project Management UI',
      img: '../images/web-project-1.jpg'
    },
    {
      id: 'rand3',
      title: 'Uber Project Management UI',
      img: '../images/web-project-2.jpg'
    }
  ],
  companyInfos: [
    {
      id: 'rand4',
      title: 'Name',
      details: 'Company Ltd'
    },
    {
      id: 'rand5',
      title: 'Services',
      details: 'UI Design & Frontend Development'
    },
    {
      id: 'rand6',
      title: 'Website',
      details: 'https://company.com'
    },
    {
      id: 'rand7',
      title: 'Phone',
      details: '555 8888 888'
    }
  ],
  technologies: [
    'HTML',
    'CSS',
    'JavaScript',
    'Nuxt.js',
    'TailwindCSS',
    'AdobeXD'
  ],
  projectDetails: [
    {
      id: 'rand8',
      details:
            'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Nihil vel illum asperiores dignissimos cumque quibusdam et fugiat voluptatem nobis suscipit explicabo, eaque consequatur nesciunt, fugit eligendi corporis laudantium adipisci soluta? Lorem ipsum, dolor sit amet consectetur adipisicing elit. Incidunt totam dolorum, ducimus obcaecati, voluptas facilis molestias nobis ut quam natus similique inventore excepturi optio ipsa deleniti fugit illo. Unde, amet! Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ipsum illo necessitatibus perspiciatis! Aperiam perferendis labore temporibus, eos culpa corporis recusandae quas, fuga voluptatibus nesciunt odit libero tenetur neque consequatur ea.'
    },
    {
      id: 'rand9',
      details:
            'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Nihil vel illum asperiores dignissimos cumque quibusdam et fugiat voluptatem nobis suscipit explicabo, eaque consequatur nesciunt, fugit eligendi corporis laudantium adipisci soluta?'
    },
    {
      id: 'rand10',
      details:
            'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Nihil vel illum asperiores dignissimos cumque quibusdam et fugiat voluptatem nobis suscipit explicabo, eaque consequatur nesciunt, fugit eligendi corporis laudantium adipisci soluta?'
    },
    {
      id: 'rand11',
      details:
            'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Nihil vel illum asperiores dignissimos cumque quibusdam et fugiat voluptatem nobis suscipit explicabo, eaque consequatur nesciunt, fugit eligendi corporis laudantium adipisci soluta? Lorem ipsum, dolor sit amet consectetur adipisicing elit. Incidunt totam dolorum, ducimus obcaecati, voluptas facilis molestias nobis ut quam natus similique inventore excepturi optio ipsa deleniti fugit illo. Unde, amet! Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ipsum illo necessitatibus perspiciatis! Aperiam perferendis labore temporibus, eos culpa corporis recusandae quas, fuga voluptatibus nesciunt odit libero tenetur neque consequatur ea.'
    }
  ],
  socialSharings: [
    {
      id: 'rand12',
      name: 'Twitter',
      icon: 'twitter',
      url: 'https://twitter.com/realstoman'
    },
    {
      id: 'rand13',
      name: 'LinkedIn',
      icon: 'linkedin',
      url: 'https://linkedin.com/in/realstoman'
    },
    {
      id: 'rand14',
      name: 'Facebook',
      icon: 'facebook',
      url: 'https://facebook.com'
    },
    {
      id: 'rand15',
      name: 'Instagram',
      icon: 'instagram',
      url: 'https://instagram.com'
    }
  ]
}
</script>

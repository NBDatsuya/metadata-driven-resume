<script setup lang="ts">
import RHeader from './components/r-header.vue';
import RSection from './components/r-section.vue';

const headerMetaData = {
  avatar: '/vite.svg',
  name: 'YOUR NAME',
  secondName: 'YOUR SECOND NAME',
  misc: [
    { key: 'EMAIL', value: 'your-email@the-service.com' },
    { key: 'TEL', value: '1145 1419 1981 0' },
    { key: 'GitHub', value: 'your-github' }
  ],
  position: 'YOUR POSITION'
};

const contentMetaDataList = [
  {
    title: 'PROFESSIONAL SUMMARY & SKILLS',
    contents: [
      {
        content: `# MARKDOWN SUPPORTED BUT THE TITLE ELEMENTS ARE NOT SUPPORTED AT PRESENT. MAYBE IN THE NEXT COMMIT.`
      }
    ]
  },
  {
    title: 'EDUCATION',
    contents: [
      {
        content: ` - LISTS ARE SUPPORTED AND WELL STYLED.
- BUT THERE IS SEVERAL PROBLEMS WITH TAB INDENTATION IN MARKDOWN PARSER.
- SO PLEASE DO NOT USE SPACES OR ANY TABS FOR INDENTATION.
- or you can say, list indentation is not supported at present.`,
        timeline: {
          start: '1919.8',
          end: '2025.11',
          className: 'bg-blue-100 text-blue-800',
          subTitle: 'YOUR UNIVERSITY NAME',
          endText: 'YOUR DEGREE NAME'
        }
      }
    ]
  },
  {
    title: 'WORK EXPERIENCE',
    contents: [
      {
        content: `If timeline is not provided, it will not be rendered. The indent is default as the author is Chinese.

In Chinese writing system, indent is needed for new paragraphs.

> Eg. 

你好，你好吗？好你吗？你吗好？吗你好？吗好你？好你好？你好吗？

你好，你好吗？好你吗？你吗好？吗你好？吗好你好？好你好？你好吗？

你好，你好吗？好你吗？你吗好？吗你好？吗好你好？好你好？你好吗？

So please do not use spaces or any tabs for indentation.

The configurable indent toggle will be supported in the future.

> But there is no indent in the blockquotes. And as you can see, blockquotes use serif fonts
`,
      }
    ]
  },
  {
    title: 'SELF EVALUATION',
    contents: [
      {
        content: `Be creative! Be confident! Be calm! （CCB Slogan） 

\`\`\`javascript
    function successCareer() {
      const believeInYourself = true;
      while (believeInYourself) {
        console.log('You can do it!');
      }
    }
\`\`\`


    Believe in yourself! Wish you a fking successful career!`,
      }
    ]
  }
];

// Example is below, you can modify it with your own information. 

const _headerMetaData = {
  avatar: '/vite.svg',
  name: 'Milijan',
  secondName: 'Kovacevic',
  misc: [
    { key: 'EMAIL', value: 'milijan.k@techsphere.com' },
    { key: 'TEL', value: '+381 00 888 7777' },
    { key: 'GitHub', value: 'm-kovacevic' },
    { key: 'LinkedIn', value: 'm-kovacevic' }
  ],
  position: 'Senior Software Architect'
};

const _contentMetaDataList = [
  {
    title: 'PROFESSIONAL SUMMARY & SKILLS',
    contents: [
      {
        content: `With over a decade of experience in full-stack development, I specialize in designing and implementing highly available and high-performance distributed systems. I possess deep expertise in microservices architecture, cloud deployment (AWS/Azure/GCP), and comprehensive DevOps practices. I prioritize code quality and scalability, and excel at leading cross-functional teams to translate complex business requirements into robust technical solutions.

**Core Skills**:
- **Architecture Design**: Microservices, Domain-Driven Design (DDD), Serverless, Event-Driven Architecture.
- **Backend Technologies**: Java (Spring Boot), Node.js, Python, Golang.
- **Databases**: PostgreSQL, MongoDB, Redis, Cassandra.
- **Cloud & DevOps**: AWS/Azure/GCP, Docker, Kubernetes, CI/CD (GitLab CI/Jenkins).
- **Frontend Technologies**: React, Vue.js, Typescript.`
      }
    ]
  },
  {
    title: 'EDUCATION',
    contents: [
      {
        content: ` - Graduated with First-Class Honors.
- Thesis topic: Research on Elastic Microservice Deployment Strategies based on Kubernetes.
- Participated in multiple cutting-edge projects in Computer Science and Engineering, building a solid foundation in theory and practice.`,
        timeline: {
          start: '2008.09',
          end: '2013.06',
          className: 'bg-blue-100 text-blue-800',
          subTitle: 'University of Belgrade',
          endText: 'M.Sc. in Computer Science and Engineering'
        }
      }
    ]
  },
  {
    title: 'WORK EXPERIENCE',
    contents: [
      {
        content: `**Technical Achievement:** Led the design and implementation of a microservice architecture for the new core trading platform, successfully reducing system latency by 40% and supporting three times the previous concurrent user capacity.

**Responsibilities:** Provided technical guidance, conducted architecture reviews for cross-geographical teams, and selected emerging technologies. Developed the technical roadmap to ensure all systems met high-performance and high-security standards.`,
        timeline: {
          start: '2019.01',
          end: 'Present',
          subTitle: 'TechSphere Solutions, Berlin',
          endText: 'Principal Software Architect',
        
          className: 'bg-rose-100 text-rose-800',
        }
      },
      {
        content: `**Project Contribution:** Key developer in the construction of the big data analytics platform, responsible for designing and implementing real-time data processing modules (Kafka, Spark Streaming).

**Team Leadership:** Managed a five-person backend team, responsible for the development and maintenance of multiple critical API services, and successfully introduced Test-Driven Development (TDD) practices.`,
        timeline: {
          start: '2013.07',
          end: '2018.12',
          subTitle: 'Innovatech Corp, Munich',
          endText: 'Senior Full-Stack Developer',
          className: 'bg-teal-100 text-teal-800',
        }
      }
    ]
  },
  {
    title: 'SELF EVALUATION',
    contents: [
      {
        content: `I am a passionate, results-oriented architect. 
        
I believe that excellent code and elegant design are the cornerstones of business success. 

I possess exceptional communication skills and complex problem-solving abilities, effectively bridging the gap between technology and business. 

I am committed to continuous learning and technical innovation, constantly driving the team and the product to new heights.

> **Motto:** Architecture is the fusion of art and engineering, not only solving today's problems but also embracing tomorrow's challenges.
`,
      }
    ]
  }
];
</script>

<template>
  <div class="my-resume">
    <RHeader :data="_headerMetaData" />
    <main class="r-main">
      <RSection v-for="item in _contentMetaDataList" :key="item.title" :data="item" />
    </main>
  </div>
</template>

<style scoped>
@reference "./style.css";
.my-resume {

  /** Still developing */
  --a4-ratio-width: calc(100vh * 210 / 297);
  --max-content-width: min(calc(100vw - 3rem), var(--a4-ratio-width));

  @apply text-text-primary w-full  lg:mx-auto;
  
}

.r-main {
  @apply my-6 mx-6 flex flex-col gap-6;
}
</style>

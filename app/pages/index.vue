<script setup lang="ts">
useHead({
  title: 'AI Projects Portfolio',
  meta: [
    {
      name: 'description',
      content: 'AI portfolio showcasing retrieval systems, multimodal tooling, agent workflows, and product-focused implementation.'
    }
  ]
})

const projects = [
  {
    title: 'AI Mindmap Learning System',
    image: '/projects/ai-mindmap.svg',
    summary: 'AI-powered system that generates personalized learning mindmaps with adaptive quizzes based on student level.',
    problem: 'Students and tutors struggle to break down broad subjects into structured, level-appropriate learning paths.',
    solution: 'Built an AI system that generates structured, hierarchical mindmaps from a general subject and difficulty level, enabling guided learning and planning.',
    tech: 'Frontend: Vue / Nuxt, Backend: Node.js / Express, AI: LLM APIs, Database: MongoDB',
    features: [
      'Generate topic trees from high-level subjects',
      'Personalized based on student level',
      'Interactive mindmap visualization',
      'AI-generated quizzes for each topic',
      'Dynamic learning flow from topic to quiz to progress'
    ],
    details: [
      'Designed structured prompts to generate hierarchical topic trees.',
      'Enforced JSON schemas for consistent node relationships.',
      'Implemented a validation layer to ensure usable graph output.',
      'Built quiz generation prompts tied to specific topics.',
      'Controlled AI output to maintain difficulty alignment with user level.',
      'Combined AI generation with deterministic logic for stability.'
    ]
  },
  {
    title: 'AI Document Validation System',
    image: '/projects/ai-documents.svg',
    summary: 'AI-powered system for automated tutor document verification with confidence scoring and workflow orchestration.',
    problem: 'Verifying tutor credentials such as IDs, DBS checks, and academic records manually is time-consuming, inconsistent, and difficult to scale.',
    solution: 'Built an AI-driven validation system that analyzes uploaded documents, verifies authenticity and relevance, and assigns confidence scores based on predefined standards.',
    tech: 'Backend: Node.js / Express, AI: LLM APIs, Messaging: Amazon SQS, File handling: PDF/Image parsers, Database: MongoDB',
    features: [
      'Automated validation of ID documents, DBS checks, university proof, and exam results',
      'Confidence scoring based on validation criteria',
      'Subject eligibility verification based on exam performance',
      'Support for both PDF and image document formats',
      'Asynchronous processing pipeline for scalability'
    ],
    details: [
      'Designed prompt pipelines for document classification and validation.',
      'Implemented structured output schemas for consistent evaluation results.',
      'Built confidence scoring logic combining AI outputs with rule-based checks.',
      'Handled multi-format inputs with PDF and image preprocessing.',
      'Mitigated hallucinations via validation and fallback logic.',
      'Mapped extracted data to domain-specific requirements such as subject eligibility.',
      'System architecture: Document Upload -> Preprocessing -> SQS Queue -> AI Validation Pipeline -> Structured Output and Confidence Score -> Business Logic.'
    ]
  }
] as const

const aiAreas = [
  'Design structured prompt pipelines to produce predictable, context-aware outputs',
  'Enforce strict schemas and validation layers to ensure consistency and usability',
  'Combine AI generation with deterministic business logic for reliability',
  'Implement confidence scoring and fallback mechanisms to handle uncertainty',
  'Normalize and transform outputs into domain-specific, actionable data structures',
  'Handle edge cases and hallucinations through validation, retries, and constraints',
  'Build evaluation workflows to measure output quality and iterate on prompts',
  'Optimize prompts for performance, cost, and latency trade-offs',
  'Design systems for scalability using asynchronous processing (e.g., queues, background jobs)',
  'Integrate AI into end-to-end product workflows, not isolated features',
  'Continuously refine systems based on real-world usage and feedback loops'
] as const

const nonAiProjects = [
  {
    title: 'Silknet',
    image: '/images/silknet.png',
    summary: 'Silknet delivers various telecom services to more than one million customers across the whole country. Silknet is the largest telecommunication company in Georgia and the entire Caucasus region.',
    tech: 'Vue, REST APIs',
    href: 'https://silknet.com/en'
  },
  {
    title: 'BasisBank',
    image: '/images/bb.png',
    summary: 'BasisBank is a universal financial holding, with over 30 years of market presence, providing banking and financial services to our business and individual clients, with the 4th biggest Bank in the country as a core entity',
    tech: 'Nuxt.js, Vue.js, TypeScript',
    href: 'https://bb.ge/en'
  },
  {
    title: 'Telasi',
    image: '/images/telasi.png',
    summary: 'Telasi is an electricity distribution company of Tbilisi, Georgia.',
    tech: 'Vue.js, Nuxt.js, Auth, Tailwind',
    href: 'https://www.telasi.ge/en'
  },
  {
    title: 'Simetria',
    image: '/images/simetria.png',
    summary: 'A property discovery interface with advanced filtering, saved searches, and agent-friendly listing management for fast updates.',
    tech: 'Nuxt.js, Vue.js, Maps, CMS',
    href: 'https://simetria.ge/en'
  }
] as const

const skillGroups = [
  {
    title: 'Frontend',
    description: 'Vue, Nuxt, React'
  },
  {
    title: 'Backend',
    description: 'Node.js, Express'
  },
  {
    title: 'AI',
    description: 'LLMs, Prompt Engineering, LangChain'
  },
  {
    title: 'Infra',
    description: 'MongoDB, AWS'
  }
] as const

const contact = {
  email: 'iagugunava05@gmail.com',
  availability: 'Open to AI and fullstack opportunities',
  links: [
    { label: 'LinkedIn', href: 'https://www.linkedin.com/in/ia-gugunava-532799213/' }
  ]
} as const
</script>

<template>
  <div class="relative overflow-hidden">
    <div class="pointer-events-none absolute inset-x-0 top-0 -z-10 h-[42rem] bg-[radial-gradient(circle_at_top,rgba(93,26,186,0.26),transparent_46%)]"></div>
    <div class="pointer-events-none absolute right-0 top-24 -z-10 h-72 w-72 rounded-full bg-[#f8f5fc]/6 blur-3xl"></div>

    <Hero />

    <main class="mx-auto max-w-6xl space-y-24 px-6 pb-24 md:px-8">
      <section id="projects" class="space-y-8">
        <h2 class="text-3xl font-bold text-[#f8f5fc]">
          Projects
        </h2>

        <div class="space-y-6">
          <ProjectCard
            v-for="project in projects"
            :key="project.title"
            :details="project.details"
            :features="project.features"
            :image="project.image"
            :problem="project.problem"
            :summary="project.summary"
            :solution="project.solution"
            :tech="project.tech"
            :title="project.title"
          />
        </div>
      </section>

      <NonAIProjects :items="nonAiProjects" />

      <AISection :items="aiAreas" />
      <Skills :groups="skillGroups" />
      <Contact
        :availability="contact.availability"
        :email="contact.email"
        :links="contact.links"
      />
    </main>
  </div>
</template>

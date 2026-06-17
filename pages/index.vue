<template>
  <div ref="rootRef" class="root">
    <!-- WebGL canvas -->
    <canvas ref="canvasRef" class="webgl-canvas" />

    <!-- dot grid parallax overlay -->
    <div class="dot-grid" data-parallax="0.06" />

    <!-- NAV -->
    <nav class="nav">
      <a href="#top" class="nav-wordmark">
        <span class="nav-prompt">&gt;</span>
        <span class="nav-name">ghulam</span>
        <span class="nav-accent">.muzafar</span>
        <span class="nav-cursor" />
      </a>
      <div class="nav-right">
        <div class="nav-links">
          <a href="#about" class="nav-link"><span class="nav-num">01</span>About</a>
          <a href="#stack" class="nav-link"><span class="nav-num">02</span>Stack</a>
          <a href="#work" class="nav-link"><span class="nav-num">03</span>Work</a>
        </div>
        <a href="#contact" class="nav-contact">Contact<span>&#8594;</span></a>
      </div>
      <span class="nav-scanline" />
      <span class="nav-line" />
    </nav>

    <!-- HERO -->
    <section id="top" class="hero">
      <div data-parallax="-0.08" class="hero-eyebrow">
        <span class="hero-dot" />
        <span class="hero-role">// Versatile Software Engineer</span>
      </div>

      <h1 data-parallax="-0.04" class="hero-title">
        <span class="hero-name-solid">GHULAM</span>
        <span class="hero-name-outline">MUZAFAR</span>
      </h1>

      <div data-parallax="-0.02" class="hero-tags">
        <span class="tag">DevOps</span>
        <span class="tag">Infrastructure</span>
        <span class="tag">Backend</span>
        <span class="tag">AI</span>
      </div>

      <p data-parallax="-0.015" class="hero-bio">
        I build the systems behind the systems — servers, pipelines, services and the intelligence that runs on top of them.
      </p>

      <div class="hero-scroll">
        <span class="hero-scroll-label">SCROLL</span>
        <span class="hero-scroll-line" />
      </div>
    </section>

    <!-- ABOUT -->
    <section id="about" class="section">
      <div data-reveal class="section-label">01 / ABOUT</div>
      <div class="about-grid">
        <div>
          <h2 data-reveal class="section-heading">Engineer across<br>the whole stack.</h2>
          <p data-reveal class="about-p about-p--light">
            I'm a versatile software engineer who moves comfortably between infrastructure, operations, backend services and applied AI. I like owning a problem end to end — from the metal it runs on to the interface it speaks through.

          </p>
          <p data-reveal class="about-p about-p--muted">
            Most of my work lives in the unglamorous middle: replacing brittle manual workflows with reliable platforms, tightening deploys, and wiring intelligence into things that used to need a human.
          </p>
        </div>
        <div data-reveal data-tilt class="portrait-card">
          <span class="portrait-label">[ portrait ]</span>
          <span class="portrait-hint">drop a photo here</span>
        </div>
      </div>
    </section>

    <!-- STACK -->
    <section id="stack" class="section">
      <div data-reveal class="section-label">02 / STACK</div>
      <h2 data-reveal class="section-heading">Tools I reach for.</h2>
      <div class="stack-grid">
        <div
          v-for="(cat, i) in stack"
          :key="cat.key"
          data-reveal
          data-tilt
          class="glass-card"
          :style="{ transitionDelay: `${i * 0.06}s` }"
        >
          <h3 class="card-title">{{ cat.title }}</h3>
          <div class="tags-wrap">
            <span v-for="t in cat.tags" :key="t" class="pill">{{ t }}</span>
          </div>
        </div>
      </div>
    </section>

    <!-- TIMELINE -->
    <section id="timeline" class="section">
      <div data-reveal class="section-label">03 / TIMELINE</div>
      <h2 data-reveal class="section-heading">The path so far.</h2>
      <div class="timeline">
        <div
          v-for="(item, i) in visibleTimeline"
          :key="i"
          data-reveal
          class="timeline-item"
          :class="{ 'timeline-item--last': i === visibleTimeline.length - 1 && timelineExpanded }"
        >
          <span class="timeline-dot" :class="{ 'timeline-dot--active': i === 0 }" />
          <div class="timeline-date">{{ item.date }}</div>
          <h3 class="timeline-role">{{ item.role }}<span v-if="item.company"> · <span class="timeline-co">{{ item.company }}</span></span></h3>
          <p class="timeline-desc">{{ item.desc }}</p>
        </div>
      </div>
      <button class="timeline-toggle" @click="timelineExpanded = !timelineExpanded">
        <span>{{ timelineExpanded ? 'less' : 'more' }}</span>
        <span class="timeline-toggle-icon" :class="{ 'timeline-toggle-icon--open': timelineExpanded }">↓</span>
      </button>
    </section>

    <!-- WORK -->
    <section id="work" class="section">
      <div data-reveal class="section-label">04 / WORK</div>
      <h2 data-reveal class="section-heading">Selected work.</h2>

      <a
        data-reveal
        data-tilt
        href="https://github.com/ghulammuzz/zzpeo"
        target="_blank"
        rel="noopener"
        class="featured-card"
      >
        <div class="featured-glow" />
        <div class="featured-meta">
          <span class="featured-badge">FEATURED</span>
          <span class="pill">TypeScript</span>
        </div>
        <h3 class="featured-title">zzpeo</h3>
        <p class="featured-desc">An internal platform to manage servers, deployments, env vars and services — replacing manual SSH workflows with one reliable control plane.</p>
        <div class="featured-cta">View on GitHub <span>→</span></div>
      </a>

      <div class="work-grid">
        <div data-reveal data-tilt class="coming-card">
          <span class="coming-num">02</span>
          <div>
            <h3 class="coming-title">Coming soon</h3>
            <p class="coming-desc">A new project is in the works.</p>
          </div>
        </div>
        <div data-reveal data-tilt class="coming-card">
          <span class="coming-num">03</span>
          <div>
            <h3 class="coming-title">Coming soon</h3>
            <p class="coming-desc">More on the way — check back shortly.</p>
          </div>
        </div>
      </div>
    </section>

    <!-- CONTACT -->
    <section id="contact" class="section section--contact">
      <div data-reveal class="section-label">05 / CONTACT</div>
      <h2 data-reveal class="contact-heading">
        <span class="contact-heading-gradient">Let's build</span><br>something.
      </h2>
      <p data-reveal class="contact-sub">Have a system that needs building, scaling or fixing? I'm open to interesting problems.</p>
      <div data-reveal class="contact-links">
        <a href="mailto:ghulamxiaomi@gmail.com" class="contact-email">ghulamxiaomi@gmail.com <span>→</span></a>
        <a href="https://github.com/ghulammuzz" target="_blank" rel="noopener" class="contact-pill">GitHub</a>
        <a href="https://www.linkedin.com/in/ghulammuzafar/" target="_blank" rel="noopener" class="contact-pill">LinkedIn</a>
        <a href="https://www.instagram.com/ghulammuzz/" target="_blank" rel="noopener" class="contact-pill">Instagram</a>
      </div>
    </section>

    <!-- FOOTER -->
    <footer class="footer">
      <span class="footer-text">© 2026 GHULAM MUZAFAR</span>
    </footer>
  </div>
</template>

<script setup lang="ts">
import { ref, computed, onMounted, onUnmounted } from 'vue'
import * as THREE from 'three'

const rootRef = ref<HTMLElement | null>(null)
const canvasRef = ref<HTMLCanvasElement | null>(null)

const stack = [
  { key: 'devops', letter: 'A', title: 'DevOps', tags: ['Docker', 'Kubernetes', 'CI/CD', 'GitHub Actions', 'Terraform'] },
  { key: 'infra', letter: 'B', title: 'Infrastructure', tags: ['Linux', 'Reverse Proxy / API Gateway', 'AWS', 'GCP', 'DigitalOcean', 'Huawei Cloud', 'Monitoring', 'Networking'] },
  { key: 'backend', letter: 'C', title: 'Backend', tags: ['Go', 'Rust', 'TypeScript', 'Node.js', 'gRPC', 'REST', 'Event Driven'] },
  { key: 'ai', letter: 'D', title: 'AI', tags: ['Python', 'LLM Integration', 'RAG', 'Vector DBs', 'ML Pipelines'] },
]

const timeline = [
  { date: 'MAY 2026 — PRESENT', role: 'Site Reliability Engineer', company: 'Tada', desc: 'Ensuring platform reliability and uptime at scale — infrastructure observability, incident response, and service SLOs.' },
  { date: 'NOV 2025 — PRESENT', role: 'Software Engineer', company: 'Owlies', desc: 'Building Go workers and LLM aggregation pipelines for automation-first product features. Fully remote.' },
  { date: 'SEP 2025 — MAY 2026', role: 'DevOps Engineer', company: 'PT. Monarch Inti Teknologi', desc: 'Kubernetes, AWS, Huawei Cloud, Digital Ocean. Architected microservice infrastructure with EDA patterns, fast-paced deployment cycles, and full observability stack.' },
  { date: 'JUN 2025 — JUN 2026', role: 'Founding & Software Engineer', company: 'Mindra Solutions', desc: 'Go, Python, Celery workers, LLM integration, ffmpeg pipelines, and Agentic AI. Building the core platform from the ground up. Remote from Estonia.' },
  { date: 'FEB 2024 — JUL 2024', role: 'DevOps Engineer', company: 'Traveloka', desc: 'AWS, ECS, Terraform, Datadog. Managed microservice infrastructure and CI/CD for one of Southeast Asia\'s largest travel platforms. Spring-based service fleet.' },
  { date: 'JUL 2022 — JUN 2026', role: 'Freelance Software Engineer', company: 'Self Employed', desc: 'Kubernetes, GCP, AWS, IaC, EDA. Four years delivering platform, SaaS, and microservice projects for clients globally. Remote.' },
  { date: 'AUG 2023 — JAN 2024', role: 'Cloud Computing Cohort', company: 'Bangkit Academy · Google, Tokopedia, Gojek, Traveloka', desc: 'Intensive cloud engineering program led by Google and top Indonesian tech companies.' },
  { date: 'FEB 2023 — OCT 2023', role: 'Software Engineer', company: 'PT. Inovasi Utama Nusantara', desc: 'Part-time engineering role building and shipping product features. Hybrid — Malang, East Java.' },
  { date: 'JUL 2022 — JUN 2023', role: 'Software Engineer', company: 'PUI-PT DLI · Internship', desc: 'Internship at a research unit — built and maintained software systems. Malang, East Java.' },
]

const timelineExpanded = ref(false)
const visibleTimeline = computed(() => timelineExpanded.value ? timeline : timeline.slice(0, 4))

let raf: number | null = null
let renderer: THREE.WebGLRenderer | null = null
let observer: IntersectionObserver | null = null

const handlers: Record<string, EventListener> = {}

function initReveal() {
  const root = rootRef.value
  if (!root) return
  const els = [...root.querySelectorAll<HTMLElement>('[data-reveal]')]

  const play = (el: HTMLElement, delay: number) => {
    if (el.dataset.revealed) return
    el.dataset.revealed = '1'
    el.style.animation = `riseIn .85s cubic-bezier(.2,.7,.2,1) ${delay}s both`
    el.addEventListener('animationend', () => {
      el.style.animation = ''
      el.style.animationDelay = ''
    }, { once: true })
  }

  if ('IntersectionObserver' in window) {
    observer = new IntersectionObserver((entries) => {
      entries.forEach(en => {
        if (en.isIntersecting) {
          play(en.target as HTMLElement, 0.04)
          observer?.unobserve(en.target)
        }
      })
    }, { threshold: 0.04, rootMargin: '0px 0px -3% 0px' })
    els.forEach(e => observer?.observe(e))
  }

  const vh = window.innerHeight || 800
  let i = 0
  els.forEach(el => {
    const r = el.getBoundingClientRect()
    if (r.top < vh) { play(el, i++ * 0.06); observer?.unobserve(el) }
  })
}

function initParallax() {
  const root = rootRef.value
  if (!root) return
  const nodes = [...root.querySelectorAll<HTMLElement>('[data-parallax]')].map(n => ({
    n, s: parseFloat(n.getAttribute('data-parallax') || '0') || 0
  }))
  let ticking = false
  const update = () => {
    const y = window.scrollY || window.pageYOffset
    nodes.forEach(({ n, s }) => { n.style.transform = `translate3d(0,${y * s}px,0)` })
    ticking = false
  }
  handlers.scroll = () => { if (!ticking) { requestAnimationFrame(update); ticking = true } }
  window.addEventListener('scroll', handlers.scroll as EventListener, { passive: true })
  update()
}

function initTilt() {
  const root = rootRef.value
  if (!root) return
  root.querySelectorAll<HTMLElement>('[data-tilt]').forEach(card => {
    card.style.transformStyle = 'preserve-3d'
    card.style.willChange = 'transform'
    const move = (e: MouseEvent) => {
      const r = card.getBoundingClientRect()
      const px = (e.clientX - r.left) / r.width - 0.5
      const py = (e.clientY - r.top) / r.height - 0.5
      card.style.transition = 'transform .12s ease-out'
      card.style.transform = `perspective(900px) rotateX(${-py * 6}deg) rotateY(${px * 7}deg) translateZ(6px)`
    }
    const leave = () => {
      card.style.transition = 'transform .5s cubic-bezier(.2,.7,.2,1)'
      card.style.transform = 'perspective(900px) rotateX(0) rotateY(0)'
    }
    card.addEventListener('mousemove', move as EventListener)
    card.addEventListener('mouseleave', leave)
  })
}

function initWebGL() {
  const canvas = canvasRef.value
  if (!canvas) return

  try {
    renderer = new THREE.WebGLRenderer({ canvas, alpha: true, antialias: true })
  } catch (e) { return }

  const dpr = Math.min(window.devicePixelRatio || 1, 2)
  renderer.setPixelRatio(dpr)
  renderer.autoClear = false
  const W = () => window.innerWidth
  const H = () => window.innerHeight
  renderer.setSize(W(), H())

  // Nebula background shader
  const bgScene = new THREE.Scene()
  const bgCam = new THREE.OrthographicCamera(-1, 1, 1, -1, 0, 1)
  const uniforms = {
    uTime: { value: 0 },
    uMouse: { value: new THREE.Vector2(0, 0) },
    uScroll: { value: 0 },
    uRes: { value: new THREE.Vector2(W(), H()) },
    uColorA: { value: new THREE.Color('#8b5cf6') },
    uColorB: { value: new THREE.Color('#5b8def') },
    uColorC: { value: new THREE.Color('#1a1f55') },
  }

  const bgMat = new THREE.ShaderMaterial({
    uniforms,
    depthTest: false,
    depthWrite: false,
    vertexShader: `varying vec2 vUv; void main(){ vUv = uv; gl_Position = vec4(position.xy, 0.0, 1.0); }`,
    fragmentShader: [
      'precision highp float;',
      'varying vec2 vUv;',
      'uniform float uTime; uniform vec2 uMouse; uniform float uScroll; uniform vec2 uRes;',
      'uniform vec3 uColorA; uniform vec3 uColorB; uniform vec3 uColorC;',
      'float hash(vec2 p){ return fract(sin(dot(p, vec2(127.1,311.7)))*43758.5453); }',
      'float noise(vec2 p){ vec2 i=floor(p); vec2 f=fract(p); vec2 u=f*f*(3.0-2.0*f);',
      ' return mix(mix(hash(i+vec2(0.0,0.0)),hash(i+vec2(1.0,0.0)),u.x), mix(hash(i+vec2(0.1,1.0)),hash(i+vec2(1.0,1.0)),u.x), u.y); }',
      'float fbm(vec2 p){ float v=0.0; float a=0.5; for(int i=0;i<5;i++){ v+=a*noise(p); p*=2.0; a*=0.5; } return v; }',
      'void main(){',
      ' vec2 uv=vUv; vec2 p=uv*2.0-1.0; p.x*=uRes.x/uRes.y;',
      ' float t=uTime*0.05;',
      ' vec2 q=vec2(fbm(p+t), fbm(p+vec2(5.2,1.3)-t*0.8));',
      ' float n=fbm(p + q*1.6 + uMouse*0.35 + vec2(0.0, uScroll*0.0006));',
      ' vec3 col=mix(uColorA, uColorB, smoothstep(0.1,0.95,n));',
      ' col=mix(col, uColorC, pow(clamp(q.x,0.0,1.0),1.6)*0.6);',
      ' float glow=pow(clamp(n,0.0,1.0),3.0);',
      ' col += uColorA*glow*0.5;',
      ' float vig=smoothstep(1.5,0.15,length(p));',
      ' col*=vig;',
      ' col=mix(vec3(0.027,0.024,0.058), col, 0.42);',
      ' gl_FragColor=vec4(col,1.0);',
      '}'
    ].join('\n')
  })
  bgScene.add(new THREE.Mesh(new THREE.PlaneGeometry(2, 2), bgMat))

  // Particle field
  const scene = new THREE.Scene()
  const camera = new THREE.PerspectiveCamera(62, W() / H(), 0.1, 1000)
  camera.position.z = 70

  const N = 2800
  const pos = new Float32Array(N * 3)
  const scl = new Float32Array(N)
  const col = new Float32Array(N * 3)
  const cA = new THREE.Color('#8b5cf6')
  const cB = new THREE.Color('#5b8def')
  const cC = new THREE.Color('#a6e9ff')

  for (let i = 0; i < N; i++) {
    pos[i * 3]     = (Math.random() - 0.5) * 200
    pos[i * 3 + 1] = (Math.random() - 0.5) * 130
    pos[i * 3 + 2] = (Math.random() - 0.5) * 130
    scl[i] = Math.random() * 1.6 + 0.35
    const r = Math.random()
    const c = r < 0.55 ? cA : r < 0.9 ? cB : cC
    col[i * 3] = c.r; col[i * 3 + 1] = c.g; col[i * 3 + 2] = c.b
  }

  const geo = new THREE.BufferGeometry()
  geo.setAttribute('position', new THREE.BufferAttribute(pos, 3))
  geo.setAttribute('aScale', new THREE.BufferAttribute(scl, 1))
  geo.setAttribute('aColor', new THREE.BufferAttribute(col, 3))

  const pUniforms = { uTime: { value: 0 }, uSize: { value: 26.0 * dpr } }
  const pMat = new THREE.ShaderMaterial({
    uniforms: pUniforms,
    transparent: true,
    depthWrite: false,
    blending: THREE.AdditiveBlending,
    vertexShader: [
      'uniform float uTime; uniform float uSize;',
      'attribute float aScale; attribute vec3 aColor; varying vec3 vColor;',
      'void main(){ vColor=aColor; vec3 p=position;',
      ' p.x += sin(uTime*0.2 + position.y*0.04)*2.2;',
      ' p.y += cos(uTime*0.16 + position.x*0.04)*2.2;',
      ' vec4 mv=modelViewMatrix*vec4(p,1.0);',
      ' gl_PointSize = uSize*aScale*(1.0/ -mv.z)*8.0;',
      ' gl_Position = projectionMatrix*mv; }'
    ].join('\n'),
    fragmentShader: [
      'varying vec3 vColor;',
      'void main(){ float d=distance(gl_PointCoord, vec2(0.5)); if(d>0.5) discard;',
      ' float a=smoothstep(0.5,0.0,d); gl_FragColor=vec4(vColor, a*0.85); }'
    ].join('\n')
  })
  const points = new THREE.Points(geo, pMat)
  scene.add(points)

  const mouse = { x: 0, y: 0, tx: 0, ty: 0 }

  handlers.mouse = ((e: MouseEvent) => {
    mouse.tx = (e.clientX / window.innerWidth) * 2 - 1
    mouse.ty = -((e.clientY / window.innerHeight) * 2 - 1)
  }) as EventListener
  window.addEventListener('mousemove', handlers.mouse, { passive: true })

  handlers.resize = (() => {
    renderer?.setSize(W(), H())
    camera.aspect = W() / H()
    camera.updateProjectionMatrix()
    uniforms.uRes.value.set(W(), H())
  }) as EventListener
  window.addEventListener('resize', handlers.resize)

  const clock = new THREE.Clock()

  const animate = () => {
    raf = requestAnimationFrame(animate)
    const dt = clock.getDelta()
    const tEl = clock.elapsedTime
    mouse.x += (mouse.tx - mouse.x) * 0.05
    mouse.y += (mouse.ty - mouse.y) * 0.05
    uniforms.uTime.value = tEl
    uniforms.uMouse.value.set(mouse.x, mouse.y)
    uniforms.uScroll.value = window.scrollY || 0
    pUniforms.uTime.value = tEl
    points.rotation.y += dt * 0.02
    points.rotation.x = mouse.y * 0.08
    camera.position.x += (mouse.x * 14 - camera.position.x) * 0.04
    camera.position.y += (mouse.y * 9 - camera.position.y) * 0.04
    camera.position.z = 70 - (window.scrollY || 0) * 0.004
    camera.lookAt(0, 0, 0)
    renderer?.clear()
    renderer?.render(bgScene, bgCam)
    renderer?.render(scene, camera)
  }
  animate()
}

onMounted(() => {
  initReveal()
  initParallax()
  initTilt()
  initWebGL()
})

onUnmounted(() => {
  if (raf) cancelAnimationFrame(raf)
  window.removeEventListener('mousemove', handlers.mouse)
  window.removeEventListener('resize', handlers.resize)
  window.removeEventListener('scroll', handlers.scroll)
  observer?.disconnect()
  try { renderer?.dispose() } catch (e) {}
})
</script>

<style scoped>
/* ── variables ── */
.root {
  --va: #8b5cf6;
  --vb: #5b8def;
  --vc: #22d3ee;
  --ink: #ECECF6;
  --mut: #9b9bbd;
  --glass: rgba(22, 20, 42, 0.42);
  --line: rgba(160, 140, 255, 0.16);

  position: relative;
  min-height: 100vh;
  background:
    radial-gradient(1200px 820px at 72% 8%, rgba(91,141,239,0.12), transparent 60%),
    radial-gradient(1100px 760px at 16% 86%, rgba(139,92,246,0.14), transparent 62%),
    #07060f;
  color: var(--ink);
  font-family: 'Space Grotesk', system-ui, sans-serif;
  overflow-x: hidden;
}

/* ── webgl canvas ── */
.webgl-canvas {
  position: fixed;
  inset: 0;
  width: 100%;
  height: 100%;
  z-index: 0;
  pointer-events: none;
  display: block;
}

/* ── dot grid ── */
.dot-grid {
  position: fixed;
  inset: 0;
  z-index: 0;
  pointer-events: none;
  opacity: 0.5;
  background-image: radial-gradient(rgba(170,160,255,0.10) 1px, transparent 1px);
  background-size: 42px 42px;
  -webkit-mask-image: radial-gradient(circle at 50% 28%, #000 28%, transparent 76%);
  mask-image: radial-gradient(circle at 50% 28%, #000 28%, transparent 76%);
}

/* ── NAV ── */
.nav {
  position: fixed;
  top: 0; left: 0; right: 0;
  z-index: 50;
  display: flex;
  align-items: stretch;
  justify-content: space-between;
  font-family: 'JetBrains Mono', monospace;
  background: linear-gradient(180deg, rgba(7,6,15,0.88) 30%, rgba(7,6,15,0) 100%);
}

.nav-wordmark {
  display: flex;
  align-items: center;
  gap: 1px;
  text-decoration: none;
  padding: 0 clamp(20px, 5vw, 64px);
  height: 64px;
}

.nav-prompt {
  color: var(--vc);
  font-size: 15px;
  font-weight: 700;
  margin-right: 8px;
}

.nav-name {
  color: #ece9ff;
  font-size: 15px;
  font-weight: 700;
  letter-spacing: 0.01em;
}

.nav-accent {
  color: var(--va);
  font-size: 15px;
  font-weight: 700;
  letter-spacing: 0.01em;
}

.nav-cursor {
  width: 9px;
  height: 17px;
  margin-left: 7px;
  background: var(--vc);
  box-shadow: 0 0 12px var(--vc);
  animation: blink 1.1s steps(1) infinite;
}

.nav-right {
  display: flex;
  align-items: stretch;
}

.nav-links {
  display: flex;
  align-items: center;
  gap: clamp(14px, 2.4vw, 38px);
  padding: 0 clamp(18px, 2.6vw, 40px);
}

.nav-link {
  display: flex;
  align-items: baseline;
  gap: 6px;
  text-decoration: none;
  color: #b6b4d4;
  font-size: 12px;
  font-weight: 500;
  letter-spacing: 0.16em;
  text-transform: uppercase;
  transition: color 0.25s;
}

.nav-link:hover { color: #ffffff; }

.nav-num {
  color: var(--va);
  font-size: 10px;
  font-weight: 700;
}

.nav-contact {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 0 clamp(24px, 2.8vw, 46px);
  height: 64px;
  background: var(--va);
  color: #0a0815;
  font-size: 13px;
  font-weight: 700;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  text-decoration: none;
  transition: background 0.25s, gap 0.25s;
}

.nav-contact:hover { background: var(--vc); gap: 18px; }

.nav-scanline {
  position: absolute;
  left: 0; bottom: 0;
  height: 1.5px;
  width: 100%;
  background: linear-gradient(90deg, transparent, var(--va), var(--vc), transparent);
  animation: scan 6s ease-in-out infinite;
}

.nav-line {
  position: absolute;
  left: 0; bottom: 0;
  height: 1px;
  width: 100%;
  background: rgba(160, 140, 255, 0.1);
}

/* ── HERO ── */
.hero {
  position: relative;
  z-index: 1;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: 120px clamp(20px, 6vw, 90px) 80px;
  max-width: 1280px;
  margin: 0 auto;
}

.hero-eyebrow {
  display: flex;
  align-items: center;
  gap: 14px;
  margin-bottom: 26px;
}

.hero-dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: var(--vc);
  box-shadow: 0 0 14px var(--vc);
  animation: pulse 2.4s ease-in-out infinite;
}

.hero-role {
  font-family: 'JetBrains Mono', monospace;
  font-size: 13px;
  letter-spacing: 0.26em;
  text-transform: uppercase;
  color: var(--mut);
}

.hero-title {
  margin: 0;
  font-weight: 700;
  letter-spacing: -0.04em;
  line-height: 0.86;
}

.hero-name-solid {
  display: block;
  font-size: clamp(56px, 13.5vw, 210px);
  background: linear-gradient(100deg, #fff 8%, var(--va) 42%, var(--vb) 70%, var(--vc) 100%);
  background-size: 220% 100%;
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
  animation: shimmer 9s linear infinite;
}

.hero-name-outline {
  display: block;
  font-size: clamp(56px, 13.5vw, 210px);
  color: transparent;
  -webkit-text-stroke: 1.4px rgba(214, 210, 255, 0.55);
}

.hero-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin-top: 38px;
}

.tag {
  font-family: 'JetBrains Mono', monospace;
  font-size: 12px;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  padding: 9px 15px;
  border: 1px solid var(--line);
  border-radius: 999px;
  color: #cfcdf0;
  background: rgba(255, 255, 255, 0.025);
}

.hero-bio {
  margin: 34px 0 0;
  max-width: 560px;
  font-size: clamp(16px, 1.5vw, 20px);
  line-height: 1.6;
  color: #c4c2dd;
}

.hero-scroll {
  position: absolute;
  left: 50%;
  bottom: 34px;
  transform: translateX(-50%);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 10px;
  animation: bob 2.6s ease-in-out infinite;
}

.hero-scroll-label {
  font-family: 'JetBrains Mono', monospace;
  font-size: 10px;
  letter-spacing: 0.4em;
  color: var(--mut);
}

.hero-scroll-line {
  width: 1px;
  height: 46px;
  background: linear-gradient(var(--va), transparent);
}

/* ── SECTIONS ── */
.section {
  position: relative;
  z-index: 1;
  max-width: 1180px;
  margin: 0 auto;
  padding: clamp(80px, 12vh, 150px) clamp(20px, 6vw, 90px);
  scroll-margin-top: 90px;
}

.section--contact {
  padding: clamp(90px, 14vh, 180px) clamp(20px, 6vw, 90px) clamp(60px, 8vh, 100px);
}

.section-label {
  font-family: 'JetBrains Mono', monospace;
  font-size: 13px;
  letter-spacing: 0.24em;
  text-transform: uppercase;
  color: var(--va);
  margin-bottom: 18px;
}

.section-heading {
  margin: 0 0 46px;
  font-size: clamp(34px, 5vw, 72px);
  font-weight: 700;
  letter-spacing: -0.03em;
  line-height: 0.98;
}

/* ── ABOUT ── */
.about-grid {
  display: grid;
  grid-template-columns: 1.4fr 1fr;
  gap: clamp(28px, 5vw, 64px);
  align-items: start;
}

.about-p {
  margin: 0 0 18px;
  font-size: clamp(16px, 1.4vw, 19px);
  line-height: 1.7;
}

.about-p--light { color: #c8c6e0; }
.about-p--muted { color: #9b9abc; }

.portrait-card {
  position: relative;
  aspect-ratio: 3/4;
  border-radius: 22px;
  overflow: hidden;
  border: 1px solid var(--line);
  background: repeating-linear-gradient(48deg, rgba(139,92,246,0.10) 0 13px, rgba(91,141,239,0.05) 13px 26px);
  box-shadow: 0 40px 90px -50px rgba(0,0,0,0.9), inset 0 1px 0 rgba(255,255,255,0.05);
  display: grid;
  place-items: center;
}

.portrait-label {
  font-family: 'JetBrains Mono', monospace;
  font-size: 12px;
  letter-spacing: 0.2em;
  color: rgba(220, 216, 255, 0.55);
  text-transform: uppercase;
}

.portrait-hint {
  position: absolute;
  bottom: 16px;
  left: 16px;
  font-family: 'JetBrains Mono', monospace;
  font-size: 10px;
  letter-spacing: 0.16em;
  color: rgba(220, 216, 255, 0.4);
}

/* ── STACK ── */
.stack-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 18px;
}

.glass-card {
  padding: 28px;
  border-radius: 20px;
  background: var(--glass);
  border: 1px solid var(--line);
  backdrop-filter: blur(18px) saturate(140%);
  -webkit-backdrop-filter: blur(18px) saturate(140%);
  box-shadow: 0 30px 80px -50px rgba(0,0,0,0.85), inset 0 1px 0 rgba(255,255,255,0.05);
}

.card-letter {
  font-family: 'JetBrains Mono', monospace;
  font-size: 11px;
  letter-spacing: 0.2em;
  color: var(--vc);
  margin-bottom: 8px;
}

.card-title {
  margin: 0 0 16px;
  font-size: 22px;
  font-weight: 600;
}

.tags-wrap {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}

.pill {
  font-family: 'JetBrains Mono', monospace;
  font-size: 12px;
  padding: 6px 11px;
  border-radius: 8px;
  background: rgba(255, 255, 255, 0.04);
  border: 1px solid var(--line);
  color: #cdcbe8;
}

/* ── TIMELINE ── */
.timeline {
  position: relative;
  padding-left: 34px;
  border-left: 1px solid var(--line);
}

.timeline-item {
  position: relative;
  padding-bottom: 44px;
}

.timeline-item--last { padding-bottom: 0; }

.timeline-dot {
  position: absolute;
  left: -42px;
  top: 4px;
  width: 14px;
  height: 14px;
  border-radius: 50%;
  background: rgba(139, 92, 246, 0.4);
  border: 1px solid var(--va);
}

.timeline-dot--active {
  background: linear-gradient(135deg, var(--va), var(--vb));
  border: none;
  box-shadow: 0 0 18px rgba(139, 92, 246, 0.8);
}

.timeline-date {
  font-family: 'JetBrains Mono', monospace;
  font-size: 12px;
  letter-spacing: 0.16em;
  color: var(--vc);
  margin-bottom: 8px;
}

.timeline-role {
  margin: 0 0 8px;
  font-size: 24px;
  font-weight: 600;
}

.timeline-co { color: var(--mut); }

.timeline-desc {
  margin: 0;
  max-width: 620px;
  font-size: 16px;
  line-height: 1.65;
  color: #a4a3c4;
}

/* ── WORK ── */
.featured-card {
  display: block;
  text-decoration: none;
  color: inherit;
  position: relative;
  overflow: hidden;
  padding: clamp(28px, 4vw, 52px);
  border-radius: 24px;
  background: linear-gradient(135deg, rgba(139,92,246,0.16), rgba(91,141,239,0.07));
  border: 1px solid var(--line);
  backdrop-filter: blur(18px) saturate(140%);
  -webkit-backdrop-filter: blur(18px) saturate(140%);
  box-shadow: 0 40px 100px -55px rgba(0,0,0,0.9), inset 0 1px 0 rgba(255,255,255,0.06);
  margin-bottom: 18px;
}

.featured-glow {
  position: absolute;
  top: -40px; right: -40px;
  width: 220px; height: 220px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(139,92,246,0.5), transparent 70%);
  filter: blur(20px);
  animation: floaty 8s ease-in-out infinite;
}

.featured-meta {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 20px;
  position: relative;
}

.featured-badge {
  font-family: 'JetBrains Mono', monospace;
  font-size: 12px;
  letter-spacing: 0.16em;
  color: var(--vc);
}

.featured-title {
  margin: 0 0 14px;
  font-size: clamp(32px, 4.5vw, 58px);
  font-weight: 700;
  letter-spacing: -0.02em;
  position: relative;
}

.featured-desc {
  margin: 0;
  max-width: 640px;
  font-size: clamp(16px, 1.5vw, 20px);
  line-height: 1.6;
  color: #cbc9e6;
  position: relative;
}

.featured-cta {
  margin-top: 26px;
  display: inline-flex;
  align-items: center;
  gap: 8px;
  font-family: 'JetBrains Mono', monospace;
  font-size: 13px;
  letter-spacing: 0.1em;
  color: var(--ink);
  position: relative;
}

.work-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 18px;
}

.coming-card {
  padding: 36px;
  border-radius: 20px;
  background: var(--glass);
  border: 1px dashed var(--line);
  backdrop-filter: blur(14px);
  -webkit-backdrop-filter: blur(14px);
  min-height: 180px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.coming-num {
  font-family: 'JetBrains Mono', monospace;
  font-size: 11px;
  letter-spacing: 0.2em;
  color: var(--mut);
}

.coming-title {
  margin: 0 0 8px;
  font-size: 24px;
  font-weight: 600;
  color: #d8d6ee;
}

.coming-desc {
  margin: 0;
  font-size: 14px;
  color: var(--mut);
}

/* ── CONTACT ── */
.contact-heading {
  margin: 0 0 14px;
  font-size: clamp(44px, 9vw, 140px);
  font-weight: 700;
  letter-spacing: -0.04em;
  line-height: 0.9;
}

.contact-heading-gradient {
  background: linear-gradient(100deg, #fff, var(--va) 55%, var(--vb));
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
}

.contact-sub {
  margin: 0 0 38px;
  max-width: 520px;
  font-size: clamp(16px, 1.5vw, 20px);
  line-height: 1.6;
  color: #c4c2dd;
}

.contact-links {
  display: flex;
  flex-wrap: wrap;
  gap: 14px;
  align-items: center;
}

.contact-email {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  padding: 16px 26px;
  border-radius: 999px;
  background: linear-gradient(135deg, var(--va), var(--vb));
  color: #0a0815;
  text-decoration: none;
  font-weight: 600;
  font-size: 16px;
  box-shadow: 0 20px 50px -20px rgba(139, 92, 246, 0.8);
}

.contact-pill {
  padding: 15px 22px;
  border-radius: 999px;
  border: 1px solid var(--line);
  background: rgba(255, 255, 255, 0.03);
  color: var(--ink);
  text-decoration: none;
  font-family: 'JetBrains Mono', monospace;
  font-size: 13px;
  letter-spacing: 0.08em;
}

/* ── FOOTER ── */
.footer {
  position: relative;
  z-index: 1;
  max-width: 1180px;
  margin: 0 auto;
  padding: 30px clamp(20px, 6vw, 90px);
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  gap: 12px;
  border-top: 1px solid rgba(160, 140, 255, 0.1);
}

.footer-text {
  font-family: 'JetBrains Mono', monospace;
  font-size: 11px;
  letter-spacing: 0.14em;
  color: var(--mut);
}

/* ── TIMELINE TOGGLE ── */
.timeline-toggle {
  margin-top: 32px;
  display: inline-flex;
  align-items: center;
  gap: 10px;
  background: none;
  border: 1px solid var(--line);
  border-radius: 999px;
  color: #b6b4d4;
  font-family: 'JetBrains Mono', monospace;
  font-size: 12px;
  letter-spacing: 0.16em;
  text-transform: uppercase;
  padding: 10px 20px;
  cursor: pointer;
  transition: color 0.2s, border-color 0.2s;
}

.timeline-toggle:hover {
  color: var(--ink);
  border-color: var(--va);
}

.timeline-toggle-icon {
  display: inline-block;
  transition: transform 0.35s cubic-bezier(.2,.7,.2,1);
}

.timeline-toggle-icon--open {
  transform: rotate(180deg);
}

/* ── RESPONSIVE ── */
@media (max-width: 768px) {
  /* Nav: hide links, keep wordmark + contact */
  .nav-links { display: none; }

  .nav-wordmark {
    padding: 0 20px;
  }

  .nav-contact {
    padding: 0 18px;
    font-size: 11px;
    letter-spacing: 0.14em;
    gap: 8px;
  }

  /* Hero */
  .hero {
    padding: 88px 20px 60px;
    justify-content: flex-start;
    min-height: auto;
  }

  .hero-eyebrow {
    margin-bottom: 20px;
  }

  .hero-role {
    font-size: 10px;
    letter-spacing: 0.16em;
  }

  .hero-title {
    line-height: 0.88;
  }

  .hero-bio {
    max-width: 100%;
    font-size: 15px;
  }

  .hero-tags {
    margin-top: 24px;
    gap: 8px;
  }

  .tag {
    font-size: 10px;
    padding: 7px 12px;
  }

  .hero-scroll {
    display: none;
  }

  /* Sections */
  .section {
    padding: 64px 20px;
  }

  .section--contact {
    padding: 64px 20px 48px;
  }

  .section-heading {
    margin-bottom: 32px;
  }

  /* About: stack vertically, portrait below */
  .about-grid {
    grid-template-columns: 1fr;
  }

  .portrait-card {
    aspect-ratio: 4/3;
    max-height: 260px;
  }

  /* Stack: single col */
  .stack-grid {
    grid-template-columns: 1fr;
  }

  .glass-card {
    padding: 22px;
  }

  /* Timeline */
  .timeline {
    padding-left: 26px;
  }

  .timeline-dot {
    left: -34px;
    width: 12px;
    height: 12px;
  }

  .timeline-role {
    font-size: 18px;
  }

  .timeline-desc {
    font-size: 15px;
  }

  /* Work */
  .work-grid {
    grid-template-columns: 1fr;
  }

  .coming-card {
    padding: 24px;
    min-height: 140px;
  }

  /* Contact */
  .contact-heading {
    font-size: clamp(38px, 11vw, 80px);
    line-height: 0.92;
    margin-bottom: 20px;
  }

  .contact-links {
    flex-direction: column;
    align-items: flex-start;
    gap: 10px;
  }

  .contact-email {
    font-size: 13px;
    padding: 13px 18px;
    word-break: break-all;
  }

  .contact-pill {
    padding: 12px 18px;
    font-size: 12px;
  }

  /* Footer */
  .footer {
    padding: 24px 20px;
    flex-direction: column;
    gap: 6px;
  }
}

@media (max-width: 420px) {
  .hero-name-solid,
  .hero-name-outline {
    font-size: clamp(48px, 18vw, 80px);
  }

  .nav-cursor {
    display: none;
  }

  .nav-contact {
    padding: 0 14px;
    font-size: 10px;
  }

  .section-heading {
    font-size: clamp(28px, 7vw, 48px);
  }

  .timeline-role {
    font-size: 16px;
  }
}
</style>

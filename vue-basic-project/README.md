# vue-basic-project

created a project with Vite + Vue 3.

## Creating a Vue Application

npm create vue@latest
cd <your-project-name>
npm install
npm run dev

# Project Structure

    src
    ├── App.vue
    │   └── Demonstrates Composition API using `<script setup>`
    │
    └── components
        └── Demo.vue
            └── Demonstrates Vue Options API

## understanding API styles

- Vue 3 Options API vs Composition API

### Options API

- In Vue.js Options API, Vue automatically exposes certain properties to the template:
  data()
  methods
  computed
  props
- These properties are exposed to the template through the component instance (this).
- check Demo.vue component

- count and increment are accessible in the template because Vue attaches them to the component instance (this).

- So internally it works like:
  this.count
  this.increment
- The template can access them automatically.

### Composition API without <script setup>

- Variables defined inside setup() must be returned to make them accessible in the template.
- example:
    <script>
    import { ref } from 'vue'
  
    export default {
    setup() {
    const count = ref(0)
  
        function increment() {
          count.value++
        }
  
        return { count, increment }
  
    }
    }
    </script>

- If you don't return them, the template cannot access them.
  So this creates boilerplate.

### Composition API With <script setup>

- In Vue.js <script setup>, Vue automatically exposes top-level bindings declared inside <script setup> to the template.
- so we don't need:
  export default
  setup()
  return
- example check App.vue code.
- Vue automatically makes count and increment available to the template.
- Everything declared at the top level of <script setup> becomes available in the template automatically.

_With Composition API, we define a component's logic using imported API functions. In SFCs, Composition API is typically used with <script setup>. The setup attribute is a hint that makes Vue perform compile-time transforms that allow us to use Composition API with less boilerplate. For example, imports and top-level variables / functions declared in <script setup> are directly usable in the template._

- compile-time transform means,
- <script setup> is just a shorter syntax for setup() where Vue automatically returns variables to the template.
- What we write with <script setup>, Vue automatically converts it,So internally Vue adds the setup() and return for you.
- this is compile-time transform = conversion happens before the browser runs the code

- Composition API is the set of functions used to manage logic, such as:
  ref()
  reactive()
  computed()
  watch()
  onMounted()
- refer https://vuejs.org/guide/extras/composition-api-faq.html and https://vuejs.org/api/
- summary
  - Composition API Programming style using ref, reactive, computed, etc.
  - setup() Function where Composition API logic runs
  - <script setup> is a compiler macro that compiles into a setup() function internally.

Quick comparison

| Style            | Structure                     | Reactivity            | Boilerplate |
| ---------------- | ----------------------------- | --------------------- | ----------- |
| Options API      | `data`, `methods`, `computed` | Automatic             | Medium      |
| Composition API  | `setup()`                     | `ref()`, `reactive()` | High        |
| `<script setup>` | compiled `setup()`            | `ref()`, `reactive()` | Low         |

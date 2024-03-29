<script setup>
  // language
  import Button from "../components/elements/Button.vue";
  import PageAsideLinks from "../components/PageAsideLinks.vue";

  import { HighCode } from 'vue-highlight-code';
  import 'vue-highlight-code/dist/style.css';
  import ElementInCodeFormate from "../components/ElementInCodeFormate.vue";
  import Alert from "../components/elements/Alert.vue";
  import { ref, reactive } from "vue";
  
  // Button Overview
  const overviewValue = `
  // script
  import Alert from "@/components/Alert.vue";
  
  <template>
    <div>
      <Alert message="Default Alert" />
      <Alert message="Default Alert with Icon" icon  />
      <Alert 
        variant="success" 
        icon 
        iconClass="fa-check-circle" 
        message="Success Alert: Lorem ipsum dolor sit, amet consectetur adipisicing elit. Voluptates, laborum." />
    </div>    
  </template>`;

  const visibleStateValue = `
  // script
  import { ref } from "vue";
  import Alert from "@/components/Alert.vue";

  const dangerAlert = ref(true);
  const successAlert = ref(true);
  
  <template>
    <div>
      <Alert 
        variant="danger" 
        dismissible 
        v-model="dangerAlert"
        message="Danger Alert: Lorem ipsum dolor sit, amet consectetur adipisicing elit. Voluptates, laborum." />

      <Alert 
        variant="success" 
        dismissible 
        v-model="successAlert"
        message="Success Alert: Lorem ipsum dolor sit, amet consectetur adipisicing elit. Voluptates, laborum." />
    </div>    
  </template>`;

  const solidVariantsValue = `
  // script
  import { reactive } from "vue";
  import Alert from "@/components/Alert.vue";

  const solidVariants = reactive([
    { message: 'Primary Alert', variant: 'primary' },
    { message: 'Secondary Alert', variant: 'secondary' },
    { message: 'Danger Alert', variant: 'danger' },
    { message: 'Warning Alert', variant: 'warning' },
    { message: 'Info Alert', variant: 'info' },
    { message: 'Success Alert', variant: 'success' },
    { message: 'White Alert', variant: 'white' },
    { message: 'Light Alert', variant: 'light' },
    { message: 'Black Alert', variant: 'black' },
    { message: 'Dark Alert', variant: 'dark' },
  ]);
  
  <template>
    <div>            
      <Alert 
        v-for="alert in solidVariants" 
        :key="alert"
        :variant="alert.variant" 
        :message="alert.message" />
    </div>
  </template>`;

  const outlineVariantsValue = `
  // script
  import { reactive } from "vue";
  import Alert from "@/components/Alert.vue";

  const outlineVariants = reactive([
    { message: 'Primary Alert', variant: 'primary-outline' },
    { message: 'Secondary Alert', variant: 'secondary-outline' },
    { message: 'Danger Alert', variant: 'danger-outline' },
    { message: 'Warning Alert', variant: 'warning-outline' },
    { message: 'Info Alert', variant: 'info-outline' },
    { message: 'Success Alert', variant: 'success-outline' },
    { message: 'White Alert', variant: 'white-outline' },
    { message: 'Light Alert', variant: 'light-outline' },
    { message: 'Black Alert', variant: 'black-outline' },
    { message: 'Dark Alert', variant: 'dark-outline' },
  ]);
  
  <template>
    <div>            
      <Alert 
        v-for="alert in outlineVariants" 
        :key="alert"
        :variant="alert.variant" 
        :message="alert.message" />
    </div>
  </template>`;

    // Additional Content Inside
  const additionalContentInsideValue = `
  // script
  import Alert from "@/components/Alert.vue";
  
  <template>
    <div>            
      <Alert variant="success" contentClass="flex--column align-items--start pb--2">
        <h2 class="mb--2">Well done!</h2>
        <p>
          Aww yeah, you successfully read this important alert message. This example text is going to
          run a bit longer so that you can see how spacing within an alert works with this kind of
          content.
        </p>
        <hr>
        <p class="mb-0">
          Whenever you need to, be sure to use margin utilities to keep things nice and tidy.
        </p>
      </Alert>
    </div>    
  </template>`;

  // ========= [ Aside links ] ========= //
  const asideLinks = [
    { path: '#overview', name: 'overview' },
    { path: '#visible-state', name: 'Visible state' },
    { path: '#variants', name: 'Variants' },
    { path: '#variant-solid-color', name: 'Solid Color Variants' },
    { path: '#variants-outline-color', name: 'Outline Color Variants' },
    { path: '#additional-content', name: 'Additional Content Inside' },
    { path: '#dismissible', name: 'Dismissible' },
    { path: '#auto-dismissing', name: 'Auto dismissing' },
    { path: '#fading', name: 'Fading' },
    { path: '#accessibility', name: 'Accessibility' },
    { path: '#download', name: 'Download' },
  ];

  // https://coreui.io/vue/docs/forms/date-picker.html

  const dangerAlert = ref(true);
  const successAlert = ref(true);

  const autoDissmissble = ref(false);
  // const dismissSecs = 10;
  const dismissCountDown = ref(0);

  const showAlert = () => {
    autoDissmissble.value = true;
    dismissCountDown.value = 10;
    console.log(dismissCountDown.value);
  }

  const solidVariants = reactive([
    { message: 'Primary Alert', variant: 'primary' },
    { message: 'Secondary Alert', variant: 'secondary' },
    { message: 'Danger Alert', variant: 'danger' },
    { message: 'Warning Alert', variant: 'warning' },
    { message: 'Info Alert', variant: 'info' },
    { message: 'Success Alert', variant: 'success' },
    { message: 'White Alert', variant: 'white' },
    { message: 'Light Alert', variant: 'light' },
    { message: 'Black Alert', variant: 'black' },
    { message: 'Dark Alert', variant: 'dark' },
  ]);

  const outlineVariants = reactive([
    { message: 'Primary Alert', variant: 'primary-outline' },
    { message: 'Secondary Alert', variant: 'secondary-outline' },
    { message: 'Danger Alert', variant: 'danger-outline' },
    { message: 'Warning Alert', variant: 'warning-outline' },
    { message: 'Info Alert', variant: 'info-outline' },
    { message: 'Success Alert', variant: 'success-outline' },
    { message: 'White Alert', variant: 'white-outline' },
    { message: 'Light Alert', variant: 'light-outline' },
    { message: 'Black Alert', variant: 'black-outline' },
    { message: 'Dark Alert', variant: 'dark-outline' },
  ]);
</script>
<script>
export default { name: "AlertView", components: { ElementInCodeFormate } }
</script>

<template>
  <div class="inner-page__wrapper">
    <div class="inner-page__main">
      <h1>Vue Alert</h1>
      <h2 class="text--light"> 
        Provide contextual feedback messages for typical user actions with the handful of available and flexible alert messages.
      </h2>

      <!-- Overview Examples -->
      <section class="block-sec mb--4" id="overview">
        <div class="block-sec__header">
          <h2 class="text--white fs--h1 mb--4">Examples</h2>
          <h3 class="fw--regular">
            <ElementInCodeFormate label="Alerts /" class="text--primary fw--bold" />
            are available for any length of text, as well as in various variants. 
            e.g.: <span class="text--primary fw--bold">primary, success, danger...</span>
          </h3>
          <h3 class="fw--regular d--none">
            <Alert variant="warning" contentClass="flex--column align-items--start gap--2 pb--2">
              <span class="mb--0"><strong>Note:</strong> You may able to add the content in two ways. through:</span>
              <ul>
                <li>Passing a props as 
                  <code class="text--primary fw--bold">message</code> along with <code class="text--primary fw--bold">icon</code>. See example below
                </li>
                <li>Passing content just like a HTML tag. 
                  <ElementInCodeFormate label="Alert" class="text--primary fw--bold" />
                  your conent
                  <ElementInCodeFormate label="Alert /" class="text--primary fw--bold" />
                  See example below
                </li>
              </ul>
            </Alert>
          </h3>
        </div>
        <hr class="my--4" />
        <div class="block-sec__body pb--4">
          <div>            
            <Alert message="Default Alert" />
            <Alert message="Default Alert with Icon" icon  />
            <Alert variant="success" icon iconClass="fa-check-circle" message="Success Alert: Lorem ipsum dolor sit, amet consectetur adipisicing elit. Voluptates, laborum." />
          </div>
        </div>
        <div class="block-sec__footer">
          <HighCode class="code" :codeValue="overviewValue" theme="dark" lang="Vue" />
        </div>
      </section>

      <!-- Visible States -->
      <section class="block-sec mb--4" id="visible-state">
        <div class="block-sec__header">
          <h2 class="text--white fs--h1 mb--4">Visible state</h2>
          <h3 class="fw--regular">
            Use the <code class="text--primary">show/hide</code> prop to control the visibility state of the <ElementInCodeFormate label="Alerts /" class="text--primary fw--bold" />. 
          </h3>
          <h3 class="fw--regular">By default alerts are shown. Set the prop <code class="text--primary">show/hide</code> to explicitly display them.</h3>
          <h3 class="fw--regular">The show prop accepts boolean true or false to show and hide the alert respectively.</h3>
          <hr />
          <h3 class="fw--regular">
            <strong><code class="text--primary">v-model</code> support:</strong>
            <br />
            You can use the <code class="text--primary">v-model</code> <code class="text--warning">directive</code> to create two-way data bindings on the show prop as in 
            <code class="text--primary">v-model="{your variable name with value of true}"</code> above. 
            Useful when you use <code class="text--primary">dismissible</code> because when user closes the alert, your variable will be updated. 
            <Alert class="text--warning" variant="dark" message="Do not use the show prop when using v-model." icon />
          </h3>
        </div>
        <hr class="my--4" />
        <div class="block-sec__body pb--4">
          <div>            
            <Alert 
              variant="danger" 
              dismissible 
              v-model="dangerAlert"
              message="Danger Alert: Lorem ipsum dolor sit, amet consectetur adipisicing elit. Voluptates, laborum." />

            <Alert 
              variant="success" 
              dismissible 
              v-model="successAlert"
              message="Success Alert: Lorem ipsum dolor sit, amet consectetur adipisicing elit. Voluptates, laborum." />
          </div>
        </div>
        <div class="block-sec__footer">
          <HighCode class="code" :codeValue="visibleStateValue" theme="dark" lang="Vue" />
        </div>
      </section>

      <!-- Contextual Variants -->
      <section class="block-sec mb--4" id="variants">
        <div class="block-sec__header">
          <h2 class="text--white fs--h1 mb--4">Contextual Variants</h2>
          <h3 class="fw--regular">
            For proper styling of <ElementInCodeFormate class="text--primary fw--bold" label="Alert /" />, use one of the four required contextual variants by setting the variant prop to one of the following:
          </h3>
        </div>
        <hr class="my--4" />
        <div class="block-sec__body pb--4" id="variant-solid-color">
          <h2 class="text--warning flex-shrink--0">Solid color variants</h2>
          <Alert variant="dark" class="mb--3">
            <code class="fw--bold text--success">primary-outline, secondary-outline, success-outline, danger-outline, warning-outline, info-outline, white-outline, light-outline, black-outline, and dark.</code>
          </Alert>
          <div>            
            <Alert 
              v-for="alert in solidVariants" 
              :key="alert"
              :variant="alert.variant" 
              :message="alert.message" />
          </div>
        </div>
        <div class="block-sec__footer">
          <HighCode class="code" :codeValue="solidVariantsValue" theme="dark" lang="Vue" />
          <div class="px--4 py--2" id="variants-outline-color">
            <h2 class="text--warning mb--1 flex-shrink--0 mb--2 mt--4">Outline color variants</h2>
            <Alert variant="dark">
              <code class="fw--bold text--success">primary-outline, secondary-outline, success-outline, danger-outline, warning-outline, info-outline, white-outline, light-outline, black-outline, and dark.</code>
            </Alert>
            <hr />
            <div style="background-color: #bfbfbf; --border-radius: 0.5rem" class="p--3 mb--3 rounded">
              <Alert 
                v-for="alert in outlineVariants" 
                :key="alert"
                :variant="alert.variant" 
                :message="alert.message" />
            </div>
          </div>
          <HighCode class="code" :codeValue="outlineVariantsValue" theme="dark" lang="Vue" />
        </div>
      </section>

      <!-- Additional Content Inside -->
      <section class="block-sec mb--4" id="additional-content">
        <div class="block-sec__header">
          <h2 class="text--white fs--h1 mb--4">Additional Content Inside Alerts</h2>
          <h3 class="fw--regular">
            <ElementInCodeFormate label="Alerts /" class="text--primary fw--bold" /> can also contain additional 
            <ElementInCodeFormate label="HTML" class="text--primary fw--bold" /> elements like <u>headings</u> and <u>paragraphs</u>, 
            which will be styled with the appropriate color matching the variant.
          </h3>
          <h3 class="fw--regular d--none">
            <Alert variant="warning" contentClass="flex--column align-items--start gap--2 pb--2">
              <span class="mb--0"><strong>Note:</strong> You may able to add the content in two ways. through:</span>
              <ul>
                <li>Passing a props as 
                  <code class="text--primary fw--bold">message</code> along with <code class="text--primary fw--bold">icon</code>. See example below
                </li>
                <li>Passing content just like a HTML tag. 
                  <ElementInCodeFormate label="Alert" class="text--primary fw--bold" />
                  your conent
                  <ElementInCodeFormate label="Alert /" class="text--primary fw--bold" />
                  See example below
                </li>
              </ul>
            </Alert>
          </h3>
        </div>
        <hr class="my--4" />
        <div class="block-sec__body pb--4">
          <div>            
            <Alert variant="success">
              <h2 class="mb--2">Well done!</h2>
              <p>
                Aww yeah, you successfully read this important alert message. This example text is going to
                run a bit longer so that you can see how spacing within an alert works with this kind of
                content.
              </p>
              <hr>
              <p class="mb-0">
                Whenever you need to, be sure to use margin utilities to keep things nice and tidy.
              </p>
            </Alert>
          </div>
        </div>
        <div class="block-sec__footer">
          <HighCode class="code" :codeValue="additionalContentInsideValue" theme="dark" lang="Vue" />
        </div>
      </section>
      
      <!-- Dismissiable Variants -->
      <section class="block-sec mb--4" id="dismissible">
        <div class="block-sec__header">
          <h2 class="text--white fs--h1 mb--4">Dismissiable Alerts</h2>
          <h3 class="fw--regular">
            Using the <code class="text--primary fw--bold">dismissible</code> prop it's possible to dismiss any <ElementInCodeFormate label="Alerts /" class="text--primary fw--bold" /> inline. This will add a close <code class="text--primary fw--bold">&times;</code> button. Use the dismiss-label prop to change the hidden label text associated with the dismiss button.
          </h3>
          <hr />
          <h3 class="fw--regular">
            <strong><code class="text--primary">v-model</code>:</strong>            
            It's required to use the <code class="text--primary">v-model</code> <code class="text--warning">directive</code> to create two-way data bindings on the show prop as in 
            <code class="text--primary">v-model="{your variable name with value of true}"</code> above. 
            Useful when you use <code class="text--primary">dismissible</code> because when user closes the alert, your variable will be updated. 
          </h3>
          <Alert class="text--warning" variant="dark" message="Do not use the show prop when using v-model." icon />
        </div>
        <hr class="my--4" />
        <div class="block-sec__body pb--4">
          <div>            
            <Alert 
              variant="danger" 
              dismissible 
              v-model="dangerAlert"
              message="Danger Alert: Lorem ipsum dolor sit, amet consectetur adipisicing elit. Voluptates, laborum." />

            <Alert 
              variant="success" 
              dismissible 
              v-model="successAlert"
              message="Success Alert: Lorem ipsum dolor sit, amet consectetur adipisicing elit. Voluptates, laborum." />
          </div>
        </div>
        <div class="block-sec__footer">
          <HighCode class="code" :codeValue="visibleStateValue" theme="dark" lang="Vue" />
        </div>
      </section>

      <!-- Auto Dismissble -->
      <section class="block-sec mb--4" id="auto-dismissing">
        <div class="block-sec__header">
          <h2 class="text--white fs--h1 mb--4">Auto Dismissing Alerts</h2>
          <h3 class="fw--regular">
            To create a <ElementInCodeFormate label="Alerts /" class="text--primary fw--bold" /> that dismisses automatically after a period of time, set the show prop (or the v-model) to the number of seconds you would like the <ElementInCodeFormate label="Alerts /" class="text--primary fw--bold" /> to remain visible for. Only integer number of seconds are supported.
          </h3>
          <hr />
          <h3 class="fw--regular">
            <strong><code class="text--primary">v-model</code>:</strong>            
            It's required to use the <code class="text--primary">v-model</code> <code class="text--warning">directive</code> to create two-way data bindings on the show prop as in 
            <code class="text--primary">v-model="{your variable name with value of true}"</code> above. 
            Useful when you use <code class="text--primary">dismissible</code> because when user closes the alert, your variable will be updated. 
          </h3>
        </div>
        <hr class="my--4" />
        <div class="block-sec__body pb--4">
          <div>            
            <Alert
              v-model="autoDissmissble" 
              variant="success" 
              message="Auto Dismissble" 
              dismissCountDown="10" 
              dismissible />
            <Button variant="success" size="medium" label="Show Alert with count-down alert" @click="showAlert" />
          </div>
        </div>
        <div class="block-sec__footer">
          <HighCode class="code" :codeValue="visibleStateValue" theme="dark" lang="Vue" />
        </div>
      </section>




      


      <!-- Download Component -->
      <section class="block-sec mb--4 py--4" id="download">
        <div class="block-sec__body pb--0 d--flex justify-content--center">
          <Button block variant="primary" size="large" type="button" label="Download Component" iconClass="fa-download" icon iconDirection="end" />
        </div>
      </section>   

    </div>
    <div class="inner-page__aside">
      <PageAsideLinks :links="asideLinks" />
    </div>
  </div>

</template>

<style lang="scss"></style>
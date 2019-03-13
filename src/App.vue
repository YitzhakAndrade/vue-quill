<template>
  <div id="app">
    <div>
      <section class="s1-U__width--900px s1-U__pd16" style="margin: 0 auto;">
        <div>
          <div class="s1-U__mg--bt32">
            <div class="md-display-1 s1-U__text-color--dark-2 s1-U__align-children--center">
              <md-button class="md-dense md-icon-button s1-U__mg--rt16">
                <md-icon>arrow_back</md-icon>
              </md-button>
              <div>
                <h1 class="md-display-1 s1-U__text-color--dark-2 s1-U__align-children--center">
                  <span>Criação de serviço</span>
                </h1>
              </div>
            </div>
          </div>
          <md-card>
            <md-content class="md-scrollbar s1-U__pd0 s1-U__pd16" style="overflow: auto;">
              <h3 class="md-title s1-U__text-color--primary s1-U__fw--300 s1-U__mg--bt16">Descrição</h3>

              <link href="//cdn.quilljs.com/1.3.6/quill.snow.css" rel="stylesheet">
              <quill-editor v-model="Quill.model" :config="Quill.config"></quill-editor>

              <br>
              <p style="font-family: monospace; min-height: 200px;">{{ Quill.model }}</p>
            </md-content>
          </md-card>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
import QuillEditor from "./components/QuillEditor";

export default {
  name: "App",
  components: {
    QuillEditor
  },
  data: () => ({
    Quill: {
      model: "",
      config: {
        placeholder: "Compose an epic...",
        theme: "snow",
        modules: {
          toolbar: [
            ["bold", "italic", "underline", "strike"], // toggled buttons
            ["blockquote", "code-block"],

            [{ header: 1 }, { header: 2 }], // custom button values
            [{ list: "ordered" }, { list: "bullet" }],
            [{ script: "sub" }, { script: "super" }], // superscript/subscript
            [{ indent: "-1" }, { indent: "+1" }], // outdent/indent
            [{ direction: "rtl" }], // text direction

            [{ size: ["small", false, "large", "huge"] }], // custom dropdown
            [{ header: [1, 2, 3, 4, 5, 6, false] }],

            [{ color: [] }, { background: [] }], // dropdown with defaults from theme
            [{ font: [] }],
            [{ align: [] }],

            ["clean"] // remove formatting button
          ]
        }
      }
    }
  })
};
</script>

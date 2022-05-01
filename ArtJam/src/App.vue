<script>
import VPerfectSignature from 'v-perfect-signature'
  
export default {
  name: "ArtJam",
  components: {
    VPerfectSignature,
  },
  data() {
    return {
      width: '100%',
      height: '100%',
      penColor: "#000000",
      backgroundColor: "#D1CAE0"};
  },
  mounted() {},
  methods: {
  toDataURL() {
        const dataURL = this.$refs.signaturePad.toDataURL()
        console.log(dataURL)
  },
  download() {
    let link = document.createElement('a')
    link.download = 'artjam.png'
    link.href = this.$refs.signaturePad.toDataURL()
    document.body.appendChild(link)
    link.click()
    document.body.removeChild(link)
  },
  setBackgroundAndPenColor() {
    const canvas = this.$refs.signaturePad.getCanvasElement()
    const ctx = canvas.getContext('2d')
    ctx.fillStyle = this.backgroundColor
    ctx.fillRect(0, 0, canvas.width, canvas.height)
    ctx.fillStyle = this.penColor
  },
  resize(){
      const canvas = this.$refs.signaturePad.getCanvasElement()
      const rect = canvas.getBoundingClientRect()
      const dpr = window.devicePixelRatio || 1

      canvas.width = rect.width * dpr
      canvas.style.width = `${rect.width}px`
      
      canvas.height = rect.height * dpr
      canvas.style.height = `${rect.height}px`
      console.log(this.width, this.height)
      console.log(canvas.style.width, canvas.style.height)

      if(this.width !== "max"){
        canvas.style.width = `${this.width}px`
      }
      if(this.height !== "max"){
        canvas.style.height = `${this.height}px`
      }
      this.$refs.signaturePad.clear()
      this.setBackgroundAndPenColor() 
      }
  }
}
</script>

<template>
  <!-- Bootstrap Icons Starts -->
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.3.0/font/bootstrap-icons.css">
  <!-- Bootstrap Icons Ends -->
  <div class="container">
    <div class="titlebar"><p>ArtJAM</p></div>
    <div class="footerbar">
      <div class="export">
        <button title="Download ArtJam" @click="download">
          Download!<i class="bi bi-cloud-download"></i>
        </button>
      </div>
    </div>
    <div class="canvas">
      <v-perfect-signature
          ref="signaturePad"
          v-model:image="image"
          :width="width"
          :height="height"
          :penColor="penColor"
          :backgroundColor="backgroundColor"/>
    </div>
    <div class="toolbar">
      <div class="toolbar_btns">
        <div class="canvas_tools">
          <div class="btn-row"><p>Canvas</p></div>
          <div class="btn-row">
          <button title="canvas-width">
            <i class="bi bi-arrow-left-right"></i>
            <select v-model="width" @change="resize">
              <option>400</option>
              <option>600</option>
              <option>800</option>
              <option>1000</option>
              <option>1200</option>
              <option>max</option>
            </select>
          </button>
          <button title="canvas-height">
            <i class="bi bi-arrow-down-up"></i>
            <select v-model="height" @change="resize">
              <option>400</option>
              <option>600</option>
              <option>800</option>
              <option>1000</option>
              <option>1200</option>
              <option>max</option>
            </select>
          </button>
        </div>
        <div class="pen_tools">
          <div class="btn-row"><p>Pen</p></div>
        <div class="btn-row">
          <button title="Clear Canvas" @click="$refs.signaturePad.clear()">
            <i class="bi bi-eraser"></i>
          </button> 
          <input type="color" title="Pen Color" v-model="penColor"/>
        </div>
      </div>
    </div>
  </div>
</div>
</div>
</template>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Caveat+Brush");
body {
  font-family: "Caveat Brush";
  size: 30pt;
}

.container {  display: grid;
  grid-template-columns: 0.5fr 1fr 1fr;
  grid-template-rows: 0.1fr 2.4fr 0.25fr;
  gap: 0px 0px;
  grid-auto-flow: row;
  grid-template-areas:
    "titlebar titlebar titlebar"
    "toolbar canvas canvas"
    "footerbar footerbar footerbar";
}

.titlebar { grid-area: titlebar; 
  font-family: "Caveat Brush";
  font-size: 30px;
  padding: 0 15px;
  border-radius: 4px;
  color: rgb(243, 233, 233);
  background-color: rgb(41, 24, 77);}

.footerbar {  display: grid;
  grid-template-columns: 0.6fr 2.5fr 0.1fr;
  grid-template-rows: 0.3fr 2.4fr 0.3fr;
  gap: 0px 0px;
  grid-auto-flow: row;
  grid-template-areas:
    ". . ."
    ". . export"
    ". . .";
  grid-area: footerbar;
  background-color: rgb(41, 24, 77);
}

.canvas { grid-area: canvas; }

.toolbar {  display: grid;
  grid-template-columns: 0.3fr 2.6fr 0.3fr;
  grid-template-rows: 0.1fr 3fr 0.1fr;
  gap: 0px 0px;
  grid-auto-flow: row;
  grid-template-areas:
    ". . ."
    ". toolbar_btns ."
    ". . .";
  grid-area: toolbar;
}

.toolbar_btns {  display: grid;
  grid-template-columns: 1fr;
  grid-template-rows: 1fr 1fr 1fr;
  gap: 0px 0px;
  grid-auto-flow: row;
  grid-template-areas:
    "canvas_tools"
    "pen_tools"
    ".";
  grid-area: toolbar_btns;
}

.canvas_tools { grid-area: canvas_tools; }

.pen_tools { grid-area: pen_tools; }

.export { grid-area: export; }

.btn-row {
  font-family: "Caveat Brush";
  font-size: 24px;
  position: relative;
	margin-bottom: 5px;
	display: flex;
	justify-content: center;
	flex-wrap: wrap;
	padding: 0 15px;
	border-radius: 4px;
}

button { 
  font-family: "Caveat Brush";
  font-size: 20px;
  padding: 0 15px;
  border-radius: 4px;
  color: rgb(243, 233, 233);
  background-color: rgb(41, 24, 77);}

</style>
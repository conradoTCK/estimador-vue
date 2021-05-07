<template>
  <fieldset v-bind:id="'estimate-base-'+id">
    <div class="select-group">
      <select name="template" id="SelTemplate" @change="onChangeTemplate($event)">
        <option value="">Seleccione un Template</option>
        <option v-bind:value="esti.value" v-for="esti in item.estimatorSel" v-bind:key="esti.id">{{esti.title}}</option>
      </select>
      <select name="type" id="SelType" @change="onChangeType($event)">
        <option value="">Seleccione un Tipo</option>
        <option v-bind:class="type.parent !== item.classTemplateSelected ? 'hide' : ''" v-bind:value="type.value" v-bind:data-parent="type.parent" v-for="type in item.typesSel" v-bind:key="type.id">{{type.title}}</option>
      </select>
      <select name="complexity" id="SelComplexity" @change="onChangeComplexity($event)">
        <option value="">Seleccione un Complejidad</option>
        <option v-bind:class="comp.parent !== item.classComplexitySelected ? 'hide' : ''" v-bind:value="comp.value" v-for="comp in item.complexitySel" v-bind:data-parent="comp.parent" v-bind:key="comp.id">{{comp.title}}</option>
      </select>
    </div>
    <input class="inputEstimateLine" type="text" v-bind:value="item.valueIntput">
    <button type="button" @click="onClickRemoveline">Remover linea</button>
  </fieldset>
</template>

<script>
export default {
  name: 'LineEstimate',
  props: {
    item: Object,
    valueIntput: String,
    id: Number
  },

  methods: {
    onChangeTemplate(e) {
      this.$emit("onChangeTemplate", {
        e: e,
        id: this.id
      })
    },
    
    onChangeType(e) {
      this.$emit("onChangeType", {
        e: e,
        id: this.id
      })
    },

    onChangeComplexity(e) {
      this.$emit("onChangeComplexity", {
        e: e,
        id: this.id
      })
    },

    onClickRemoveline(e){
      const btn = e.target;
      btn.parentElement.remove();
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.hide {
  display: none;
}


form {

}

fieldset {
  width: 100%;
  display: flex;
  border: 0;;
}

select {
  width: 200px;
  height: 40px;
  border-radius: 0;
  border-left: 0;
  padding: 0 6px;
}

form select:first-child {
    border-left: 1px solid;
}

.select-group {
  min-width: 600px;
  display: inline-block;
}
</style>

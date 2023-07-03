<template>
    <h1 class="heading-text">Table of content</h1>
    <ul class="table">
        <li class="row">
            <h4 class="col table-headings">name</h4>
            <h4 class="col table-headings">value</h4>
        </li>
		<li class="row" v-for="item in data" :key="item.id">
            <div class="col data">{{ item.name }}</div>
            <div class="col data">{{ item.value }}</div>
		</li>
	</ul>

    <form class="form" @submit.prevent>
        <div class="form-container justify-content-center">

            <div class="col-auto row">
                <label class="col-sm-4 col-form-label" for="item-select">Chose the name</label>
                <div class="col-sm-8">
                    <select class="form-select form-select" v-model="selectedName" name="itmes" id="item-select">
                        <option value="">-- Choose line --</option>
                        <option v-for="item in data" :value="item">{{ item.name }}</option>
                    </select>
                </div> 
            </div>

            <div class="col-auto row">
                <label class="col-sm-4 col-form-label" for="newValue">Input new value</label>
                <div class="col-sm-8">
                    <input class="form-control" id="newValue" type="text" v-model="newValue" />
                </div>
            </div>
            
            <div class="col-auto">
                <button class="btn btn-primary col-4" @click="saveNewValue()">
                    Save
                </button>
            </div>
        </div>
    </form>

</template>
<script>
export default {
    emits: ['change'],
    data() {
        return {
            selectedName: null,
            newValue: null,
        }
    },
    props: ['data'],
    methods: {
        saveNewValue() {
            this.$emit('change', this.selectedName.name, this.newValue);
        }
    }
}
</script>
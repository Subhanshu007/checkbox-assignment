<template>
 <div id='myapp'>
			
			<!-- Check All -->
			<input type='checkbox' @click='checkAll()' v-model='isCheckAll'> Check All

			<!-- Checkboxes list -->
			<ul>
				<li v-for='(lang, index) in arr' :key="index">
					<input type='checkbox' v-bind:value='lang' v-model='selectedArr' @change='updateCheckall()'>{{ lang }}
				</li>
			</ul>

			<!-- Print -->
			<input type='button' @click='printValues()' value='Print Selected Values'>

			<br>
			Selected items : {{ selectedlang }}

		</div>
</template>

<script>
export default {
  data() {
    return {
      isCheckAll: false,
      arr: ["test1", "test2", "test3", "test4", "test5"],
      selectedArr: [],
      selectedlang: "",
    };
  },
  methods: {
    checkAll() {
      this.isCheckAll = !this.isCheckAll;
      this.selectedArr = [];
      if (this.isCheckAll) {
        // Check all
        for (var key in this.arr) {
          this.selectedArr.push(this.arr[key]);
        }
      }
    },
    updateCheckall() {
      if (this.selectedArr.length == this.arr.length) {
        this.isCheckAll = true;
      } else {
        this.isCheckAll = false;
      }
    },
    printValues() {
      this.selectedlang = "";
      for (var key in this.selectedArr) {
        this.selectedlang += this.selectedArr[key] + ", ";
      }
    },
  },
};
</script>
<style scoped>
.wrapper {
  display: flex;
}
</style>

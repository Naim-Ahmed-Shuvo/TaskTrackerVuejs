<template>
    <form @submit="handleSubmit" class="add-form">
    <div class="form-control">
      <label>Task</label>
      <input type="text" v-model="text" name="text" placeholder="Add Task" />
    </div>
    <div class="form-control">
      <label>Day & Time</label>
      <input
        type="date"
        v-model="date"
        name="day"
        placeholder="Add Day & Time"
      />
    </div>
    <div class="form-control form-control-check">
      <label>Set Reminder</label>
      <input type="checkbox" v-model="reminder" name="reminder" />
    </div>

    <input type="submit" :value="[saving?'Saving....':'Save Task']" class="btn btn-block" />
  </form>
</template>

<script>
 export default {
     name: "AddTask",
     data(){
         return{
             id: null,
             text:"",
             date:"",
             reminder: false,
             saving:false
         }
     },
     methods:{
         handleSubmit(e){
             e.preventDefault();
             this.saving = true
             if(!this.text || !this.date){
                 alert("Please Fill All The fields");
                 return;
             }

             
             setTimeout(()=>{

                 const task = {
                    id:Math.floor(Math.random()*100000),
                    text: this.text,
                    date:this.date,
                    reminder: this.reminder
                 }
    
                 //
                 this.id = null,
                 this.text="",
                 this.date="",
                 this.reminder=false
    
                 //
                 this.$emit('add-task',task);
                 this.saving=false
             },1000)

            //  console.log("submitting",task);
         }
     }
 }
</script>

<style scoped>
.add-form {
  margin-bottom: 40px;
}
.form-control {
  margin: 20px 0;
}
.form-control label {
  display: block;
}
.form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}
.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.form-control-check label {
  flex: 1;
}
.form-control-check input {
  flex: 2;
  height: 20px;
}
</style>
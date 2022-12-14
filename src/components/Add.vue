<template>
    <div>
        <div class="wrapper">        
            <div class="wrapad">
            <input class="inpp" type="text" v-model="value" placeholder="FirstName">
            <span class="sp"></span>
            </div>
            <div class="wrapad">
            <input class="inpp" type="text" v-model="value1" placeholder="LasttName">
            <span class="sp"></span>
            </div>
            <button class="btn" @click="add">Add</button>
        </div> 
        <div class="wrapper">
          <div v-if="list.length" class="list-of-list">
          <ol>
          <li v-for="(item,index) in list">
          <p>
          <span>{{ item.titleName }}</span><span>{{this.space}}</span><span>{{ item.title }}</span>
          </p>
          <div>
            <button class="btnofdone" @click="remove(index)">delete</button>
            <button class="btnofdone" @click="update(index)">
              
              <span class="btnofdone" v-if="!item.status">edit</span>
              <span class="btnofdone" v-else>save</span>
            </button>
          </div>
          <input class="inpu" type="text" v-if="item.status" v-model="list[index].title">
          </li>
          </ol>
        </div> 
        </div>  
    </div>
</template>

<script>
export default {

    watch: {
        count() {
            console.log('skdjcjd')
        }
    },
    data() {
      return {
        space: ' ',
        count: 0,
        value: '',
        list: [],
        tabs: [
            'home',
            'about',
            'contacts'
        ],
      }
    },
    methods: {
        add() {
        console.log(this.list)
        console.log(this.value1);
        if(this.value.length) {
          this.list.push({
            titleName: this.value,
            title: this.value1,
            status: false
          })
          this.value = ''
          this.value1  = ''
        }
      },
      update(i) {
        this.list[i].status = !this.list[i].status
      },
      remove(index) {
        console.log(index)
        this.list.splice(index, 1)
      }
    }
}

</script>

<style scoped>
.inpu{
  background: inherit;
  border:1px solid white;
  padding: 8px 15px;
  width:8rem;

}
.btnofdone{
  color: white;
  background: hsl(236, 32%, 26%);
  padding: 10px 15px;
  border: none ; 
  margin-right: 3px ;
}
.list-of-list{
  background: inherit;
  border: 1px solid white;
  display: flex;
  width: 500px ;
}
.wrapper {
    display: flex;
    justify-content: center;
    margin-top: 20px;
}
.btn {
  z-index: 1;
  position: relative;
  font-size: inherit;
  font-family: inherit;
  color: white;
  padding: 0.5em 1em;
  outline: none;
  border: none;
  background-color: hsl(236, 32%, 26%);
}

.btn:hover {
  cursor: pointer;
}

.btn::before {
  content: '';
  z-index: -1;
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  border: 4px solid hsl(236, 32%, 26%);
  transform-origin: center;
  transform: scale(1);
}

.btn:hover::before {
  transition: all 0.75s ease-in-out;
  transform-origin: center;
  transform: scale(1.75);
  opacity: 0;
}
.wrapad {
  position: relative;
  box-sizing: border-box;
  display: flex;
  width: 8%;
  margin-right: 10px;
}

.inpp {
  width: 7.5em;
  color: white;
    font-size: inherit;
  font-family: inherit;
  background-color: transparent;
  border: 1px solid transparent;
  border-bottom-color: hsla(185, 100%, 62%, 0.2);
}

.inpp:focus {
  outline: none;
}

.inpp::placeholder {
  color: hsla(0, 0%, 100%, 0.6);
}

.sp {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  height: 1px;
  background-color: #3cefff;
  transform-origin: bottom right;
  transform: scaleX(0);
  transition: transform 0.5s ease;
}

.inpp:focus ~ .sp {
  transform-origin: bottom left;
  transform: scaleX(1);
}
*{
    color: white;
}
</style>
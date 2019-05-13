<template>
  <div>
    <nav class="navbar fixed-top navbar-light bg-light">
      <strong >Fare Card System</strong>
      <strong v-if="balance">Card Balance: ${{balance}}</strong>
    </nav>
    <div class="row">
      <div class="card  container col-6" padding="20px">
        <h3>The Fare Card System</h3>
        <hr>
        <div class="card-body">
          <h5 class="card-title">Click the Button below to Load your Card with $30</h5>
          <button v-on:click="loadCard()" class="btn btn-primary">Load Card</button>
          <hr>

          <div class="card">
            <div class="card-body">
              <h5 class="card-title">Welcome to 5th Station (Zone 1)</h5> 
              <P>Click the Button Below to Check In</p>
              <button :disabled='disable' v-on:click="checkIn($event)" class="btn btn-primary" name="5th">Check In</button>
              <hr>
            </div>
          </div>

          <div class="card">
             <div class="card-body">
                <h5 class="card-title">Welcome to Pelham	Parkway Station (Zone 1)</h5>
                <p class="card-text">Click the Button Below to Check In</p>
                <button :disabled='disable' v-on:click="checkIn($event)"  class="btn btn-primary" name="pelham">Check In</button>
                <hr>
                <p class="card-text">Click the Button Below to Check Out</p>
                <button :disabled='disable2' v-on:click="checkOut($event)" class="btn btn-primary" name="pelham">Check Out</button>
                <hr>
              </div>
          </div>
          <hr>
          <div class="card">
             <div class="card-body">
                <h5 class="card-title">Welcome to Pelham	Parkway Station (Zone 2)</h5>
                <p class="card-text">Click the Button Below to Check In</p>
                <button :disabled='disable' v-on:click="checkIn($event)" class="btn btn-primary" name="pelham">Check In</button>
                <hr>
                <p class="card-text">Click the Button Below to Check Out</p>
                <button :disabled='disable2' v-on:click="checkOut($event)" class="btn btn-primary" name="pelham">Check Out</button>
                <hr>
              </div>
          </div>
          <hr>
          <div class="card">
             <div class="card-body">
                <h5 class="card-title">Welcome to Bronx Station (Zone 3)</h5>
                <p class="card-text">Click the Button Below to Check In</p>
                <button  :disabled='disable' v-on:click="checkIn($event)" class="btn btn-primary" name="bronx">Check In</button>
                <hr>
                <p class="card-text">Click the Button Below to Check Out</p>
                <button :disabled='disable2' v-on:click="checkOut($event)" class="btn btn-primary" name="bronx">Check Out</button>
                <hr>
              </div>
          </div>
          <hr>
           <div class="card">
             <div class="card-body">
                <h5 class="card-title">Welcome to Guns Hill Station (Zone 2)</h5>
                <p class="card-text">Click the Button Below to Check In</p>
                <button :disabled='disable' v-on:click="checkIn($event)" class="btn btn-primary" name="guns">Check In</button>
                <hr>
                <p class="card-text">Click the Button Below to Check Out</p>
                <button :disabled='disable2' v-on:click="checkOut($event)" class="btn btn-primary" name="guns">Check Out</button>
                <hr>
              </div>
          </div>

        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data(){
    return{
      startAt: '',
      stoppedAt:'',
      balance:'',
      disable: true,
      disable2: true
    }
  },
  methods:{
    loadCard(){
        this.disable = false;
        if(this.balance == ''){
        this.balance = 30;
        }else
        {
          this.balance = this.balance + 30;
        }
    },
    checkIn(event){
      this.disable = true
      this.disable2 = false
      this.startAt = event.target.name
      this.stoppedAt = ''
      this.balance = parseInt(this.balance) - 3.20;
    },
    checkOut(event){
      this.disable = false
      this.stoppedAt = event.target.name
      this.calculateBalance()
    },
    calculateBalance(){
      if(this.startAt == '5th' && this.stoppedAt == 'pelham'){
        this.balance = this.balance + (3.20 - 2.5);
      }
      if(this.startAt == 'pelham' && this.stoppedAt == 'bronx'){
        this.balance = this.balance + (3.20 - 1.80);
      }
      if(this.startAt == 'pelham' && this.stoppedAt == 'guns'){
        this.balance = this.balance + (3.20 - 2.0);
      }
        
    }
  }
}
</script>

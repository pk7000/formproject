<template>
  <div>
    <v-form ref="form" v-model="valid" lazy-validation>
      <p>เพศ</p>
      <v-row >
        <v-checkbox
        v-model="sex"
        value="ชาย"
        label="ชาย"
        required
      ></v-checkbox>
      <v-checkbox
        v-model="sex"
        value="หญิง"
        label="หญิง"
        required
      ></v-checkbox></v-row>
      <p>อายุ</p>
      <v-row>
        <v-checkbox
        v-model="age"
        value="teen"
        label="น้อยกว่า 20 ปี"
        required
      ></v-checkbox>
      <v-checkbox
        v-model="age"
        value="working"
        label="20-40"
        required
      ></v-checkbox>
      <v-checkbox
        v-model="age"
        value="midle"
        label="41-60 ปี"
        required
      ></v-checkbox>
      <v-checkbox
        v-model="age"
        value="aged"
        label="61 ปีขึ้นไป"
        required
      ></v-checkbox></v-row>
      <v-col>
        <p>พนักงานมีความเป็นกันเอง</p>
        <v-checkbox v-model="s1" value="4" label="ดีมาก" required></v-checkbox>
        <v-checkbox v-model="s1" value="3" label="ดี" required></v-checkbox>
        <v-checkbox v-model="s1" value="2" label="พอใช้" required></v-checkbox>
        <v-checkbox v-model="s1" value="1" label="แย่" required></v-checkbox>
        <v-checkbox v-model="s1" value="0" label="แย่มาก" required></v-checkbox>
      </v-col>
      <v-col>
        <p>พนักงานทำงานอย่างมีประสิทธิภาพ</p>
        <v-checkbox v-model="s2" value="4" label="ดีมาก" required></v-checkbox>
        <v-checkbox v-model="s2" value="3" label="ดี" required></v-checkbox>
        <v-checkbox v-model="s2" value="2" label="พอใช้" required></v-checkbox>
        <v-checkbox v-model="s2" value="1" label="แย่" required></v-checkbox>
        <v-checkbox v-model="s2" value="0" label="แย่มาก" required></v-checkbox>
        </v-col>
      <v-col>
        <p>ความสะอาดของสถานที่</p>
        <v-checkbox v-model="s3" value="4" label="ดีมาก" required></v-checkbox>
        <v-checkbox v-model="s3" value="3" label="ดี" required></v-checkbox>
        <v-checkbox v-model="s3" value="2" label="พอใช้" required></v-checkbox>
        <v-checkbox v-model="s3" value="1" label="แย่" required></v-checkbox>
        <v-checkbox v-model="s3" value="0" label="แย่มาก" required></v-checkbox>
        </v-col>
      <v-col>
        <p>สิ่งอำนวยความสะดวก</p>
        <v-checkbox v-model="s4" value="4" label="ดีมาก" required></v-checkbox>
        <v-checkbox v-model="s4" value="3" label="ดี" required></v-checkbox>
        <v-checkbox v-model="s4" value="2" label="พอใช้" required></v-checkbox>
        <v-checkbox v-model="s4" value="1" label="แย่" required></v-checkbox>
        <v-checkbox v-model="s4" value="0" label="แย่มาก" required></v-checkbox>
        </v-col>
      <v-col>
        <p>ความปลอดภัย</p>
        <v-checkbox v-model="s5" value="4" label="ดีมาก" required></v-checkbox>
        <v-checkbox v-model="s5" value="3" label="ดี" required></v-checkbox>
        <v-checkbox v-model="s5" value="2" label="พอใช้" required></v-checkbox>
        <v-checkbox v-model="s5" value="1" label="แย่" required></v-checkbox>
        <v-checkbox v-model="s5" value="0" label="แย่มาก" required></v-checkbox>
        </v-col>
      <v-col>
        <p>มีการแจ้งข่าวสารที่เป็นประโยชน์</p>
        <v-checkbox v-model="s6" value="4" label="ดีมาก" required></v-checkbox>
        <v-checkbox v-model="s6" value="3" label="ดี" required></v-checkbox>
        <v-checkbox v-model="s6" value="2" label="พอใช้" required></v-checkbox>
        <v-checkbox v-model="s6" value="1" label="แย่" required></v-checkbox>
        <v-checkbox v-model="s6" value="0" label="แย่มาก" required></v-checkbox>
        </v-col>
      <v-col>
        <p>ข้อเสนอแนะเพิ่มเติม</p>
        <v-text-field></v-text-field>
        </v-col>
      <v-btn :disabled="!valid" color="success" class="mr-4" @click="validate">
        Submit
      </v-btn>
      <v-btn color="error" class="mr-4" @click="reset"> Reset Form </v-btn>
      <v-btn class="mr-4" @click="page">See all</v-btn>
    </v-form>
  </div>
</template>

<script>
export default {
  data: () => ({
    valid: true,
    sex: "",
    age:"",
    s1: 0,
    s2: 0,
    s3: 0,
    s4: 0,
    s5: 0,
    s6: 0,
    score: 0,
  }),
  methods: {
    validate() {
        let payload = {
          score: this.s1/1+this.s2/1+this.s3/1+this.s4/1+this.s5/1+this.s6/1,
          sex: this.sex,
          age: this.age
        };
        this.$store.dispatch("setItem", payload);     
    },
    reset() {
      this.$refs.form.reset();
    },
    page() {
      this.$store.state.page = 2;
    },
  },
};
</script>

<style>
</style>
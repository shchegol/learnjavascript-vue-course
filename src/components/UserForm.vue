<template>
  <div>
    <div class="row">
      <div class="col form-group">
        <label for="firstName">Name</label>
        <input type="text" v-model="user.firstName" id="firstName" name="firstName" class="form-control">
      </div>

      <div class="col form-group">
        <label for="lastName">Last Name</label>
        <input type="text" v-model="user.lastName" id="lastName" name="lastName" class="form-control">
      </div>
    </div>

    <div class="row">
      <div class="col form-group">
        <label for="email">Email</label>
        <input type="text" v-model="user.email" id="email" name="email" class="form-control">
      </div>

      <div class="col form-group">
        <label for="age">Date of Birth</label>
        <datepicker v-model="user.age" id="age" class="form-control"></datepicker>
      </div>
    </div>

    <div class="row">
      <div class="col form-group">
        <label>Avatar</label>
        <avatar-uploader v-model="user.picture" />
      </div>
    </div>

    <div class="row">
      <div class="col form-group">
        <label for="accessLevel">Access level</label>
        <select v-model="user.accessLevel" id="accessLevel" name="accessLevel" class="form-control">
          <option v-for="item in accessList" :key="item">
            {{ item }}
          </option>
        </select>
      </div>

      <div class="col form-group">
        <label for="isActive">Active</label>
        <div class="checkbox-inline">
          <input type="checkbox" v-model="user.isActive" id="isActive" name="isActive"/> Yes
        </div>
      </div>
    </div>

    <div class="row">
      <div class="col form-group">
        <label for="phone">Phone</label>
        <input type="text" v-model="user.phone" id="phone" name="phone" class="form-control">
      </div>

      <div class="col form-group">
        <label for="address">Address</label>
        <input type="text" v-model="user.address" id="address" name="address" class="form-control">
      </div>
    </div>

    <div class="row">
      <div class="col form-group">
        <label for="company">Company</label>
        <input type="text" v-model="user.company" id="company" name="company" class="form-control">
      </div>

      <div class="col form-group">
        <label for="registered">Registered</label>
        <input type="text" v-model="user.registered" id="registered" name="registered" class="form-control"/>
      </div>

      <div class="col form-group">
        <label for="balance">Balance</label>
        <input type="text" v-model="user.balance" id="balance" name="balance" class="form-control"/>
      </div>
    </div>

    <div class="row">
      <div class="col form-group">
        <label for="about">About</label>
        <TextEditor v-model="user.about" id="about" name="about" class="form-control"></TextEditor>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    components: {
      AvatarUploader: () => import('@/components/common/AvatarUploader.vue'),
      Datepicker: () => import('@/components/common/Datepicker.vue'),
      TextEditor: () => import('@/components/common/TextEditor.vue'),
    },
    name: 'UserForm',
    model: {
      prop: 'user'
    },
    props: {
      user: {
        type: Object,
        required: true
      }
    },
    data () {
      return {
        accessList: [
          'guest', 'user', 'admin'
        ]
      }
    }
  }
</script>

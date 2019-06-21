<template>
    <div class="test">
        <!--
        <form-helper>
            <div slot="form-controls">
                <label class="label" for="">Enter Git Repo:</label>
                <input type="text" v-model="repo.name" placeholder="Enter https git repo url or repo name.." size="70">
                <label class="label" for="" >Email Recipient</label>
                <input type="text">
            </div>
        </form-helper>
        -->
        <div class="form">
          <div class="repo-field">
            <div class="field has-addons">
              <label class="label">Git Repo</label>
              <div class="control">
                <a href="#" class="button is-static">{{repo.protocol}}</a>
              </div>
              <div class="control">
                <!--<input class="input" type="text" v-model="repo.path" value="Enter Git project name" size=50>-->
                <input class="input" type="text" v-model="repo.path" value="Enter Git project name" size=50>
              </div>
            </div>
          </div>
          <div class="email-field">
            <div class="field has-addons">
              <label class="label">Email ID</label>
              <div class="control has-icons-left">
                <input class="input" type="email" placeholder="vnakka" v-model="email.username">
                <span class="icon is-small is-left">
                  <i class="fas fa-envelope"></i>
                </span>
              </div>
              <div class="control">
                <a href="#" class="button is-static">{{email.suffix}}</a>
              </div>
            </div>
          </div>
          <div class="form-controls">
            <div class="field is-grouped">
              <div class="control">
                <button class="button submit-btn" @click="submitData()">Submit</button>
              </div>
              <div class="control">
                <button class="button clear-btn" @click="clearForm()">Clear</button>
              </div>
            </div>
          </div>
          <div v-show="submitted">
            <!--
            <ui-modal ref="modal" :active="submitted" :cancellable="1" @close="hideModal">
               <ui-modal-form @close="hideModal" :result="result"></ui-modal-form>
            </ui-modal>
            -->
            <bs-ui-modal :result="result" :errors="errors" :active="submitted" @close="hideModal"></bs-ui-modal>
          </div>
      </div>
    </div>
</template>

<script>
import FormHelper from './FormHelper'
import UiModal from './UiModal'
import UiModalForm from './UiModalForm'
import BsUIModal from './BSUiModal'
import axios from 'axios'
import { webserver } from '../config/config'

export default {
  components: {
    'form-helper': FormHelper,
    'ui-modal': UiModal,
    'ui-modal-form': UiModalForm,
    'bs-ui-modal': BsUIModal
  },
  data () {
    return {
      repo: {
        path: '',
        protocol: 'https://',
        prefix: 'https://github.factset.com',
        fullpath: ''
      },
      email: {
        username: '',
        suffix: '@factset.com',
        fullname: ''
      },
      submitted: false,
      errors: [],
      result: {}
    }
  },
  methods: {
    submitData () {
      this.submitted = true
      this.result = {}
      console.log(webserver.url)
      this.postData()
    },
    clearForm () {
      this.submitted = false
      this.repo.path = ''
      this.email.username = ''
    },
    hideModal () {
      this.submitted = false
    },
    async postData () {
      try {
        console.log(this.repo.fullpath, this.email.fullname)
        await axios.post(webserver.url, {'gitrepo': this.repo.fullpath, 'emailaddress': this.email.fullname})
          .then((response) => {
            console.log(response)
            console.log(typeof (response.data))
            this.result = response.data
            console.log(this.result)
          })
      } catch (e) {
        this.errors.push(e)
        console.log(this.errors)
        // this.errors['message'] = e.message
        // this.errors['stack'] = e.stack
        // console.log(this.errors)
      }
    }
  },
  watch: {
    'repo.path': function (newvalue) {
      let pathname = this.repo.path.match(this.repo.protocol)
      console.log(pathname)
      if (pathname) {
        console.log(this.repo.protocol, this.repo.path)
        this.repo.path = this.repo.path.split(this.repo.protocol)[1]
      }
      this.repo.fullpath = this.repo.protocol + this.repo.path
      console.log(this.repo.fullpath)
    },
    'email.username': function (new2) {
      let usermatch = this.email.username.match(this.email.suffix)
      if (typeof (usermatch) === 'object') {
        this.email.username = this.email.username.split(this.email.suffix)[0]
      }
      this.email.fullname = this.email.username + this.email.suffix
      console.log(this.email.fullname)
    }
  }
}
</script>

<style scoped>
.form{
  max-width: 900px;
  width: 620px;
  padding: 20px;
  display: inline-block;
  border: 0.5px solid grey;
  box-sizing: border-box;
  margin-top: 20px;
  margin-left: 33%;
}
label{
  font-family:sans-serif;
  font-size: 14px;
  padding-right: 10px;
  text-align:start;
}
.form-controls{
  display: inline-block;
  padding: 10px;
  margin-left: 33%;
}
.email-field{
  margin-top: 10px;
}
.has-icons-left{
  width: 60%;
}
.clear-btn {
  background-color:#a93149;
  color: aliceblue;
}
.submit-btn {
  background-color:#3363ca;
  color: aliceblue;
}
p{
  color: red;
}
/*
form-helper {
  width: 720px;
  display: inline-block;
}

form-helper > label {
  display: none;
}
.form{
  maxWidth: 630px;
  borderWidth: 1px solid grey;
}
.label{
  display: inline-block;
}
input{
  display: inline-block;
}
*/
</style>

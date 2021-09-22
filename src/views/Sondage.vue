<template>
  <div id="sondage">
    <form>
      <div class="form-group row">
        <label for="inputEmail3" class="col-sm-2 col-form-label">Email</label>
        <div class="col-sm-10">
          <input type="email" class="form-control" id="inputEmail3" placeholder="Email">
        </div>
      </div>
      <fieldset class="form-group">
        <div class="row">
          <legend class="col-form-label col-sm-2 pt-0">Vous préferez :</legend>
          <div class="col-sm-10">
            <div class="form-check">
              <input class="form-check-input" type="radio" name="viennoiserie" id="pain" value="1" v-model="picked">
              <label class="form-check-label" for="pain">
                les pains au chocolat
              </label>
            </div>
            <div class="form-check">
              <input class="form-check-input" type="radio" name="viennoiserie" id="croissant" value="2" v-model="picked">
              <label class="form-check-label" for="croissant">
                les croissants
              </label>
            </div>
            <div class="form-check disabled">
              <input class="form-check-input" type="radio" name="viennoiserie" id="aucun" value="3" v-model="picked">
              <label class="form-check-label" for="aucun">
                aucun des deux
              </label>
              <div class="container-radio">
              <p>{{ pickedtxt }}</p>
                <img v-if="picked === '1'" src="../assets/pain-au-chocolat.png" class="img-fluid viennoiserie">
                <img v-else-if="picked === '2'" src="../assets/croissant.png" class="img-fluid viennoiserie">
              </div>
            </div>
          </div>
        </div>
      </fieldset>
      <div class="form-group row">
        <div class="col-sm-2">Checkbox</div>
        <div class="col-sm-10">
          <div class="form-check">
            <input class="form-check-input" type="checkbox" id="gridCheck1">
            <label class="form-check-label" for="gridCheck1">
              Example checkbox
            </label>
          </div>
        </div>
      </div>
      <div class="form-group row">
        <div class="col-sm-10">
          <button type="submit" class="btn btn-primary">Sign in</button>
        </div>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      picked: ''
    }
  },
  computed: {
    pickedtxt () {
      switch (this.picked) {
        case '1':
          return 'Hmmmm Pain au chocolat'

        case '2':
          return 'Hmmmm croissant'

        case '3':
          return 'Ah !'

        default:
          return "Vous n'avez rien choisi"
      }
    }
  }
}
</script>

<style scoped>
.container-radio{
  display: flex;
}
.viennoiserie{
  max-width: 8rem;
  flex-basis: 40%;
}

</style>>

<template>
  <div class="container">
    <div class="col-md-4"></div>
    <div class="col-md-4">
      <form>
        <div class="form-group">
          <input
            v-model="nom"
            name="nom"
            type="text"
            class="form-control"
            placeholder="Nom"
          />
         
        </div>
        <br />
        <div class="form-group">
          <input
            v-model="prenom"
            name="prenom"
            type="text"
            class="form-control"
            placeholder="Prenom"
          />
           <span class="text-danger">{{ isAlpha(prenom) }}</span>
        </div>
        <br />
        <div class="form-group">
          <input type="text"  v-model="email" name="email" class="form-control" placeholder="Email" />
        <span class="text-danger">{{ isEmail() }}</span>
        </div>
        <br />
        <div class="form-group">
          <input
            v-model="dateNaissance"
            name="dateNaissance"
            type="date"
            class="form-control"
            placeholder="Année de naissance"
          />
              <span class="text-danger">{{ calculAge() }}</span>
        </div>
        <br />
        <div class="form-group">
          <input
            v-model="matricule"
            name="matricule"
            type="text"
            class="form-control"
            placeholder="Matricule"
          />
           <span class="text-danger">{{ isMatricule() }}</span>
        </div>
        <br />
        <div class="form-group">
          <input
            v-model="motPass"
            name="motPass"
            type="text"
            class="form-control"
            placeholder="Mot de passe"
          />
           <span class="text-danger">{{ passwordSame() }}</span>
        </div>
        <br />
        <div class="form-group">
          <input
            v-model="veryfMotPass"
            name="verifMotPass"
            type="text"
            class="form-control"
            placeholder="Vérification mot de passe"
          />
            <span class="text-danger">{{ passwordSame() }}</span>
        </div>
        <br />
        <div class="col-auto">
          <button type="submit" class="btn btn-primary">
          S'inscrire
        </button></div>
        
      </form>
    </div>
    <div class="col-md-4"></div>
  </div>
</template>

<script>
export default {
  name: "Register",
  data() {
   return{
    
    nom: "",
    prenom: "",
    email: "",
    matricule: "",
    dateNaissance: "",
    motPass: "",
    veryfMotPass: "",
   }
  },
  methods: {
    isAlpha: function (word) {
      if (word!=""&&/[^a-zA-Z]/.test(word)) {
        return "Le prenom doit contenir que des lettres";
      }else{
        return "";
      }
    },

    isEmail: function () {
      if (this.email!=""&&!/[a-z0-9]+@[a-z]+\.[a-z]{2,3}/.test(this.email)) {
        return "Email saisi est invalide";
      }else{
        return "";
      }
    },

     passwordSame: function () {
      if ((this.motPass!=""&&this.veryfMotPass!="")&&this.motPass!=this.veryfMotPass) {
        return "Les mots de passe doivent être identiques";
      }else{
        return "";
      }
    },

     isMatricule: function () {
      if (this.matricule!=""&&/[^a-zA-Z0-9]/.test(this.matricule)) {
        return "Le matricule ne doit pas contenir de caractères spéciaux";
      }else{
        return "";
      }
    },
     calculAge: function () {
      if (this.dateNaissance!="") {
        let newDate = new Date();
        let date=new Date(this.dateNaissance);
        if((newDate.getFullYear()-date.getFullYear())<16){
             return "Interdit à toute personne de moins de 16 de s’inscrire sur la plateforme";
      }else{
        return "";
      
        }
      
      }
    
    },
  },
};
</script>

<style scoped>
</style>

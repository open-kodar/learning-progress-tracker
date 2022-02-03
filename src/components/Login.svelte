<script>
  import Storage from '../services/storage';
  const storage = new Storage();

  let name = null;
  let email = null;
  let passcode = null;

  const Login = () => {
    if(name && email){
      let storage_key = email + passcode;
      let res = storage.get(storage_key);
      let _storage_obj = {
        name, email,
        datetime: new Date(),
      }
      if(res){
        console.log(res)
      }else{
        storage.set(storage_key, _storage_obj);
      }
    }

  }

</script>

  <div class="card w-25">
    <div class="card-body">
      <div class="form-group">
        <label for="exampleFormControlInput1">Full Name</label>
        <input type="text" class="form-control" bind:value={name} placeholder="...">
      </div>
      <div class="form-group">
        <label for="exampleFormControlInput1">Email address</label>
        <input type="email" class="form-control" bind:value={email} required placeholder="name@example.com">
      </div>

      <div class="form-group">
        <label for="exampleFormControlInput1">Passcode</label>
        <input type="password" class="form-control" required bind:value={passcode}>
      </div>

    </div>
    <div class="card-footer">
      <button type="button" class="btn btn-primary float-end" on:click={Login}>Login</button>
    </div>
  </div>

<style>
</style>
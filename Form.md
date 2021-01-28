# Form

### TextBox
```html
@php
$email_value = $variable->email;
if(old('email')){
  $email_value = old('email');
}
@endphp
<div class="col-lg-12">
  <div class="form-group">
    <label for="">Email<span class="required">*</span></label>
    <div class="input-group">
      <input type="text" class="form-control" name="email" placeholder="Write your email" value="{{ $email_value }}">
    </div>
  </div>
  <div class="text-danger">{{$errors->first('first_name') }}</div>
</div>
```

### SelectBox

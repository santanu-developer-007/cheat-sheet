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
  <div class="text-danger">{{$errors->first('email') }}</div>
</div>
```

### RadioGroup
```html
@php
$gender_value = $variable->gender;
if(old('gender')){
  $gender_value = old('gender');
}
@endphp
<div class="col-lg-12">
  <div class="form-group">
    Gender
    <div class="form-radio">
      <input name="gender" id="radio1" type="radio" value="Male" {{ ($gender_value == 'Male') ? 'checked': '' }}>
      <label for="radio1">Male</label>
    </div>
    <div class="form-radio">
      <input name="gender" id="radio2" type="radio" value="Female" {{ ($gender_value == 'Female') ? 'checked' : '' }}>
      <label for="radio2">Female</label>
    </div>											
  </div>
  <div class="text-danger">{{$errors->first('gender') }}</div>
</div>
```

### SelectBox
```html
@php
  $selected_country = $variable->country_id;
  if(old('country_id')){
    $selected_country = old('country_id');
  }
@endphp
<div class="col-lg-12">
  <div class="form-group">
    <label class="form-label">Country<span class="required">*</span></label>
    <select name="country_id" class="form-control">
      <option value="">--Select--</option>
      @if(count($countries) > 0)
        @foreach($countries as $country)
          <option value="{{ $country->id }}" {{ $selected_country == $country->id ? 'selected' : '' }}>{{ $country->name }}</option>
        @endforeach
      @endif
    </select>
  </div>
  <div class="text-danger">{{$errors->first('country_id') }}</div>
</div>
```

### MultiSelect Select2
```html
<link href="https://cdn.jsdelivr.net/npm/select2@4.1.0-beta.1/dist/css/select2.min.css" rel="stylesheet" />
<script src="https://cdn.jsdelivr.net/npm/select2@4.1.0-beta.1/dist/js/select2.min.js"></script>
```
```html
@php
  $selected_countries = $variable->selected_countries;
  if(old('country_id') && count(old(country_id))>0 ){
    $selected_countries = old('country_id');
  }
@endphp
<div class="col-lg-12">
  <div class="form-group">
    <label class="form-label">Country<span class="required">*</span></label>
    <select name="country_id[]" class="form-control select2" multiple>
      <option value="">--Select--</option>
      @if(count($countries) > 0)
        @foreach($countries as $country)
          <option value="{{ $country->id }}" {{ (in_array($country->id, $selected_countries)) ? 'selected' : '' }}>{{ $country->name }}</option>
        @endforeach
      @endif
    </select>
  </div>
  <div class="text-danger">{{$errors->first('country_id') }}</div>
</div>
```

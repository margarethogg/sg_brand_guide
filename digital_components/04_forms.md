# FORMS
We have styled our forms to be legible, clear and inviting. Active elements use Shiftgig Green (#C6E979) to indicate focus and maintain accessibility standards. We use a lightened Gray (#E2E2E2) for disabled elements. For messaging and hierarchy rules around form submit buttons, please refer to the [Buttons](digital_components/02_buttons.md) section of this guide.

<!--clean below to show one example of each form element-->
<form>
  First name:<br>
  <input type="text" name="firstname"><br>
  Last name:<br>
  <input type="text" name="lastname" disabled>
</form>
<form>
  User name:<br>
  <input type="text" name="username"><br>
  User password:<br>
  <input type="password" name="psw">
</form>
<form action="action_page.php">
  First name:<br>
  <input type="text" name="firstname" value="Mickey"><br>
  Last name:<br>
  <input type="text" name="lastname" value="Mouse"><br><br>
  <input type="submit" value="Submit">
</form>
<form>
  <input type="radio" name="gender" value="male" checked> Male<br>
  <input type="radio" name="gender" value="female"> Female<br>
  <input type="radio" name="gender" value="other"> Other
</form>
<form>
  <input type="checkbox" name="vehicle1" value="Bike"> I have a bike<br>
  <input type="checkbox" name="vehicle2" value="Car"> I have a car 
</form>
<form>
  Birthday:
  <input type="date" name="bday">
</form>
<form>
  <input type="range" name="points" min="0" max="10">
</form>
<form>
  E-mail:
  <input type="email" name="email">
</form>
<select name="cars">
  <option value="volvo">Volvo</option>
  <option value="saab">Saab</option>
  <option value="fiat">Fiat</option>
  <option value="audi">Audi</option>
</select>

<textarea name="message" rows="10" cols="30">
The cat was playing in the garden.
</textarea>
# js-AutoCompleteCity

<!DOCTYPE html>
<html>
  <head>
    <title>autocompletecityname</title>
    <meta name="viewport" content="initial-scale=1.0, user-scalable=no">
    <meta charset="utf-8">
  </head>
  <body>


	<pre>
		<input id="autocomplete" placeholder="Enter your address" type="text" />

		locality
		<input id="field_locality" disabled="true"/>

		administrative_area_level_1
		<input id="field_administrative_area_level_1" disabled="true" />

		postal_code
		<input id="field_postal_code" disabled="true" />

		country
		<input id="field_country" disabled="true" />
	</pre>

	<script>

		function cityA(){
		 var e=document,$id=e.getElementById.bind(e),h={locality:'long',administrative_area_level_1:'short',country:'long',postal_code:'short'};
		 e=new google.maps.places.Autocomplete(($id('autocomplete')),{types: ['geocode']});
		 e.addListener('place_changed',function(){
			var g=h,f=$id;
			for(var p in g){f('field_'+p).value='';};
			for(var m=g,o,n,$=f,i=0,c=e.getPlace().address_components,j=c.length>>>0;i<j;i++){
				o=c[i];
				n=o.types[0];
				if(n in m){$('field_'+n).value=o[m[n]+'_name'];}
			};
		 });
		}

	</script>
	<script src="https://maps.googleapis.com/maps/api/js?libraries=places&callback=cityA" async defer></script>

  </body>
</html>

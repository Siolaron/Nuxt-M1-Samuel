<template>
  <div>
    <p>Title: {{ title }}</p>
    <p>Description: {{ description }}</p>
    <p>Surface: {{ surface }}</p>
    <p>Nombre de chambres: {{ rooms }}</p>
    <p>Prix: {{ price }}</p>
    <p>Meublé : {{meuble}}</p>
  </div>
</template>
<script>
export default {
  async asyncData({ params }) {
    const realestate = await fetch("http://localhost:1337/api/real-estates/" + params.id).then((res) =>
      res.json()
    );
    return {
      title: realestate.data.attributes.Title,
      description: realestate.data.attributes.Description,
      surface: realestate.data.attributes.Area,
      rooms: realestate.data.attributes.Number_of_rooms,
      price: realestate.data.attributes.Price + " €",
      meuble : realestate.data.attributes.Furnished
    }
  },
};
</script>
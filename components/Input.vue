<template>
  <div>
    <label :for="id">{{ label }}</label>
    <input
      @input="$emit('input', type === 'checkbox' ? $event.target.checked : $event.target.value)"
      :id="id"
      :type="type"
      :name="name"
      :value="value"
      :required="required"
    />
  </div>
</template>

<script>
export default {
  props: {
    label: String,
    id: String,
    type: String,
    name: String,
    required: Boolean,
    value: [String,Boolean],
  },
};
</script>
<template>
  <transition v-if="visible" name="modal">
    <div class="modal-mask">
      <div class="modal-wrapper">
        <div class="modal-container">
          <div class="modal-body">
            <div class="inner">
              <button class="close" @click="$emit('close')">×</button>
              <slot></slot>
            </div>
          </div>
        </div>
      </div>
    </div>
  </transition>
</template>
<style lang="scss">
.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: table;
  transition: opacity 0.3s ease;
}
.modal-wrapper {
  display: table-cell;
  vertical-align: middle;
}
.modal-container {
  max-width: 575px;
  margin: 0px auto;
  max-height: 675px;
  overflow-y: auto;
  padding: 10px;
  background-color: #fff;
  border-radius: 2px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
  transition: all 0.3s ease;
  .inner {
    padding: 30px 35px 30px 30px;
  }
}
.modal-body {
  position: relative;
  .close {
    position: absolute;
    top: 0px;
    right: 5px;
    font-size: 25px;
    border: 0;
    &:hover {
      cursor: pointer;
    }
  }
  p {
    color: #4b4f54;
    font-size: 11px;
    line-height: 18px;
  }
  p:last-of-type {
    margin-bottom: 0;
  }
  strong {
    display: block;
  }
}
.modal-enter .modal-container,
.modal-leave-active .modal-container {
  -webkit-transform: scale(1.05);
  transform: scale(1.05);
}
h5 {
  font-size: 20px;
  font-weight: 600;
  line-height: 30px;
  margin-bottom: 10px;
}
</style>
<script>
export default {
  props: ['visible']
}
</script>

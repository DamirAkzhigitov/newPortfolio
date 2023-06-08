<template>
  <section class='avatar-container'>
    <div class='avatar-soft-skill'>
      <div class='avatar-soft-skill__item'>
        <div class='item-icon'>🎨</div>
        <div class='item-title'>UI Kit</div>
      </div>
      <div class='avatar-soft-skill__item'>
        <div class='item-icon'>🎨</div>
        <div class='item-title'>UI Kit</div>
      </div>
      <div class='avatar-soft-skill__item'>
        <div class='item-icon'>🎨</div>
        <div class='item-title'>UI Kit</div>
      </div>
    </div>
    <div class='profile-container'>
      <figure class='profile-picture__container'>
        <img src='/Pic.png' class='profile-picture__image' alt='' />
        <figcaption class='profile-picture__tag'>Frontend Engineer</figcaption>
      </figure>
      <div class='profile__name'>
        Damir Akzhigitov
      </div>
      <div class='profile__location'>
        Limassol, Cyprus
      </div>
    </div>
    <div class='avatar-soft-skill'>
      <div class='avatar-soft-skill__item'>
        <div class='item-icon'>🎨</div>
        <div class='item-title'>UI Kit</div>
      </div>
      <div class='avatar-soft-skill__item'>
        <div class='item-icon'>🎨</div>
        <div class='item-title'>UI Kit</div>
      </div>
      <div class='avatar-soft-skill__item'>
        <div class='item-icon'>🎨</div>
        <div class='item-title'>UI Kit</div>
      </div>
    </div>
    <div class='avatar-hard-skills'>
      <div class='avatar-hard-skills__item'>
        <img src='/logos/figma-logo.png' class='hard-skills__logo'/>
      </div>
    </div>
  </section>
</template>

<script setup lang='ts'>

</script>

<style lang='scss'>
.avatar-container {
  display: grid;
  grid-template-rows: 1fr 60px;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 15px;

  max-width: 700px;
  width: 100%;
  margin: 0 auto;

  .profile-container {
    box-shadow: 10px 10px 100px -20px rgba(0,0,0, 0.2);
    border-radius: 20px;
    padding: 20px;
    display: flex;
    justify-content: center;
    flex-flow: column;
    align-items: center;


    .profile-picture {
      &__image {
        height: 200px;
        width: auto;
      }
      &__container {
        position: relative;
      }
      &__tag {
        position: absolute;
        bottom: 0;
        right: 50%;
        transform: translate(50%,-50%);
        background: linear-gradient(135deg, #26CBFF 0%, #1B67D9 64.06%, #0F44FF 100%);
        box-shadow: 0px 5px 20px rgba(250, 118, 96, 0.2);
        border-radius: 5px;
        font-style: normal;
        font-weight: 700;
        font-size: 16px;
        text-align: center;
        color: #FFFFFF;
        padding: 0 5px;
      }
    }
  }

  .avatar-hard-skills {
    grid-column: 1/4;

    &__item {
      width: 60px;
      height: 60px;
      background: #F4EEFB;
      border-radius: 40%;
      display: flex;
      align-items: center;
      justify-content: center;
    }
  }
}
</style>
<template>
  <section
    id="classsection"
    class="container container-custom"
    style="background: #a36d49"
  >
    <ClassContent
      v-for="content in contents"
      :item="content"
      :key="content.id"
    ></ClassContent>
    <div class="row justify-content-center">
      <ClassButtons
        v-for="(button, i) in buttons"
        :index="i"
        :item="button"
        :key="button.id"
        :data-id="button.id"
        v-on:active_classs="activeClass"
      ></ClassButtons>
    </div>
  </section>
</template>

<script>
import ClassButtons from "./ClassButtons.vue";
import ClassContent from "./ClassContent.vue";

export default {
  data() {
    return {
      buttons: [
        {
          id: 1,
          classname: "Mage",
          targetId: 0,
          img: "12.png",
          shadowBoxColor: "#00eaff",
          imgactive: "12_c.png",
          active: true,
        },
        {
          id: 2,
          classname: "Stalker",
          targetId: 1,
          img: "13.png",
          shadowBoxColor: "#709f34",
          imgactive: "13_c.png",
          active: false,
        },
        {
          id: 3,
          classname: "Hunter",
          targetId: 2,
          img: "15.png",
          shadowBoxColor: "#921f80",
          imgactive: "15_c.png",
          active: false,
        },
        {
          id: 4,
          classname: "Knight",
          targetId: 3,
          img: "17.png",
          shadowBoxColor: "#bd3232",
          imgactive: "17_c.png",
          active: false,
        },
      ],
      contents: [
        {
          id: 1,
          idbutton: 0,
          classname: "Mage",
          videoclass: "mago/magonew.mp4",
          imgclass: "Mago.png",
          imgAttrClass: "Mage",
          imgAttrStyle: { transform: "scale(1.5)" },
          classdesc:
            "Mages base their power on the elements and are able to channel them in order to increase their secondary effects. They can attack from a short distance, nevertheless each hit deals a lot of damage.",
          active: true,
        },
        {
          id: 2,
          idbutton: 1,
          classname: "Stalker",
          videoclass: "acechador/acechadornew.mp4",
          imgAttrClass: "Stalker",
          imgAttrStyle: { transform: "scale(1.5)" },
          imgclass: "stalker_image.png",
          classdesc:
            "Stalkers are shadow assassins, they use their basic attacks to poise enemies and then finish them with daggers. Stalkers also count on the support of “Battle Masters”, who grant an additional effect to each hit.",
          active: false,
        },
        {
          id: 3,
          idbutton: 2,
          classname: "Hunter",
          videoclass: "cazador/cazadornew.mp4",
          imgclass: "Cazador.png",
          imgAttrClass: "Hunter",
          classdesc:
            "Hunters focus their damage on long distance shots, they faster compared to the other classes and can detect enemies even if they are behind them. Hunters carry a quiver where they store arrows and some handy items such as bombs and traps.",
          active: false,
        },
        {
          id: 4,
          idbutton: 3,
          classname: "Knight",
          videoclass: "caballero/caballeronew.mp4",
          imgclass: "knight_image.png",
          imgAttrClass: "Knight",
          classdesc:
            "Knights use light and darkness to their favor, they are able to create attack combinations at will, making each combination deal a different effect on the opponent. Most of the Knight's attacks are melee.",
          active: false,
        },
      ],
      currentSelected: 0,
    };
  },
  components: {
    ClassButtons,
    ClassContent,
  },
  methods: {
    activeClass(index) {
      this.currentSelected = index;
      this.buttons.forEach((el) => {
        el.active = false;
      });
      this.contents.forEach((el) => {
        el.active = false;
      });
      this.buttons[index].active = true;
      this.contents[this.buttons[index].targetId].active = true;
    },
  },
};
</script>
<template>
  <div>
    <div class="top-row">
      <div class="top part">
        <img :src="availableParts.heads[selectedHeadIndex].src" title="head" />
        <button @click="selectPreviousHead()" class="prev-selector">&#9668;</button>
        <button @click="selectnextHead()" class="next-selector">&#9658;</button>
      </div>
    </div>
    <div class="middle-row">
      <div class="left part">
        <img :src="availableParts.arms[selectedLeftArmIndex].src" title="left arm" />
        <button @click="selectPreviousLeftArm()" class="prev-selector">&#9650;</button>
        <button @click="selectNextLeftArm()" class="next-selector">&#9660;</button>
      </div>
      <div class="center part">
        <img :src="availableParts.torsos[selectedTorsoIndex].src" title="left arm" />
        <button @click="selectPreviousTorso()" class="prev-selector">&#9668;</button>
        <button @click="selectNextTorso()" class="next-selector">&#9658;</button>
      </div>
      <div class="right part">
        <img :src="availableParts.arms[selectedRightArmIndex].src" title="left arm" />
        <button @click="selectPreviousRightArm()" class="prev-selector">&#9650;</button>
        <button @click="selectNextRightArm()" class="next-selector">&#9660;</button>
      </div>
    </div>
    <div class="bottom-row">
      <div class="bottom part">
        <img :src="availableParts.bases[selectedBottomIndex].src" title="left arm" />
        <button @click="selectPreviousBottom()" class="prev-selector">&#9668;</button>
        <button @click="selectNextBottom()" class="next-selector">&#9658;</button>
      </div>
    </div>
  </div>
</template>

<script>
import availableParts from "../data/parts";

function getPreviousValidIndex(index, length) {
  const deprectedIndex = index - 1;
  return deprectedIndex < 0 ? length - 1 : deprectedIndex;
}

function getNextValidIndex(index, length) {
  const incrementedIndex = index + 1;
  return incrementedIndex > length - 1 ? 0 : incrementedIndex;
}

export default {
  name: "RobotBuilder",
  data() {
    return {
      availableParts,
      selectedHeadIndex: 0,
      selectedLeftArmIndex: 0,
      selectedRightArmIndex: 0,
      selectedTorsoIndex: 0,
      selectedBottomIndex: 0
    };
  },
  methods: {
    selectnextHead() {
      this.selectedHeadIndex = getNextValidIndex(
        (this.selectedHeadIndex += 1),
        availableParts.heads.length
      );
    },
    selectPreviousHead() {
      this.selectedHeadIndex = getPreviousValidIndex(
        (this.selectedHeadIndex -= 1),
        availableParts.heads.length
      );
    },
    selectPreviousLeftArm() {
      this.selectedLeftArmIndex = getNextValidIndex(
        (this.selectedLeftArmIndex += 1),
        availableParts.arms.length
      );
    },
    selectNextLeftArm() {
      this.selectedLeftArmIndex = getPreviousValidIndex(
        (this.selectedLeftArmIndex -= 1),
        availableParts.arms.length
      );
    },
    selectPreviousTorso() {
      this.selectedTorsoIndex = getNextValidIndex(
        (this.selectedTorsoIndex += 1),
        availableParts.torsos.length
      );
    },
    selectNextTorso() {
      this.selectedTorsoIndex = getPreviousValidIndex(
        (this.selectedTorsoIndex -= 1),
        availableParts.torsos.length
      );
    },
    selectPreviousRightArm() {
      this.selectedRightArmIndex = getNextValidIndex(
        (this.selectedRightArmIndex += 1),
        availableParts.arms.length
      );
    },
    selectNextRightArm() {
      this.selectedRightArmIndex = getPreviousValidIndex(
        (this.selectedRightArmIndex -= 1),
        availableParts.arms.length
      );
    },
    selectPreviousBottom() {
      this.selectedBottomIndex = getNextValidIndex(
        (this.selectedBottomIndex += 1),
        availableParts.bases.length
      );
    },
    selectNextBottom() {
      this.selectedBottomIndex = getPreviousValidIndex(
        (this.selectedBottomIndex -= 1),
        availableParts.bases.length
      );
    }
  }
};
</script>

<style>
.part {
  position: relative;
  width: 165px;
  height: 165px;
  border: 3px solid #aaa;
}
.part img {
  width: 165px;
}
.top-row {
  display: flex;
  justify-content: space-around;
}
.middle-row {
  display: flex;
  justify-content: center;
}
.bottom-row {
  display: flex;
  justify-content: space-around;
  border-top: none;
}
.head {
  border-bottom: none;
}
.left {
  border-right: none;
}
.right {
  border-left: none;
}
.left img {
  transform: rotate(-90deg);
}
.right img {
  transform: rotate(90deg);
}
.bottom {
  border-top: none;
}
.prev-selector {
  position: absolute;
  z-index: 1;
  top: -3px;
  left: -28px;
  width: 25px;
  height: 171px;
}
.next-selector {
  position: absolute;
  z-index: 1;
  top: -3px;
  right: -28px;
  width: 25px;
  height: 171px;
}
.center .prev-selector,
.center .next-selector {
  opacity: 0.8;
}
.left .prev-selector {
  top: -28px;
  left: -3px;
  width: 144px;
  height: 25px;
}
.left .next-selector {
  top: auto;
  bottom: -28px;
  left: -3px;
  width: 144px;
  height: 25px;
}
.right .prev-selector {
  top: -28px;
  left: 24px;
  width: 144px;
  height: 25px;
}
.right .next-selector {
  top: auto;
  bottom: -28px;
  left: 24px;
  width: 144px;
  height: 25px;
}
.right .next-selector {
  right: -3px;
}
</style>
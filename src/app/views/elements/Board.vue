<template>
  <div class="board-container">
    <div class="board">

      <div class="clear-button">
        <ui-button :disabled="lists.length === 0" @click="reset">Reset</ui-button>
      </div>

      <div class="lists-container">

        <Container 
          lock-axis="x"
          orientation="horizontal"
          drag-handle-selector=".list-drag-handle"
          @drop="onListDrop"
        >
          <Draggable v-for="(list, listIndex) in lists" :key="list.id">
            <section class="list-container" id="each-card" ref="list" :data-id="list.id">

              <div class="list-header">
                <span class="list-drag-handle">
                  <svg width="439px" height="439px" viewBox="0 0 439 439" style="max-width:100%;" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
                    <g id="Page-1" stroke="none" stroke-width="1" fill="none" fill-rule="evenodd">
                      <g id="Healthcare">
                        <path id="white2" d="M145.4,0 L293.7,0 C302.1,0 309,6.8 309,15.3 L309,423 C309,431.4 302.2,438.3 293.7,438.3 L145.4,438.3 C137,438.3 130.1,431.5 130.1,423 L130.1,15.2 C130.2,6.8 137,0 145.4,0 Z" fill="#FFFFFF"></path>
                        <path id="white1" d="M0.4,290.3 L0.4,142.1 C0.4,133.7 7.2,126.8 15.7,126.8 L423.5,126.8 C431.9,126.8 438.8,133.6 438.8,142.1 L438.8,290.4 C438.8,298.8 432,305.7 423.5,305.7 L15.7,305.7 C7.2,305.6 0.4,298.8 0.4,290.3 Z" fill="#FFFFFF"></path>
                        <path id="path13" d="M276.5,217.1 L276.5,220.7" stroke="#142D52" stroke-width="2" stroke-linecap="round" stroke-dasharray="3.5999908447265625" style="stroke-dashoffset: 0px;"></path>
                        <path id="path12" d="M266.9,210.3 L266.9,401.7 C266.9,407 262.6,411.3 257.3,411.3 C257.3,411.3 257.3,411.3 257.3,411.3 L180.7,411.3 C175.4,411.3 171.1,407 171.1,401.7 L171.1,277.3 C171.1,272 166.8,267.7 161.5,267.7 L37.2,267.7 C31.9,267.7 27.6,263.4 27.6,258.1 L27.6,181.5 C27.6,176.2 31.9,171.9 37.1,171.9 C37.1,171.9 37.1,171.9 37.1,171.9 L75.4,171.9" stroke="#142D52" stroke-width="2" stroke-linecap="round" stroke-dasharray="706.9166259765625" style="stroke-dashoffset: 0px;"></path>
                        <path id="path11" d="M257.8,195.9 L257.3,219.9" stroke="#142D52" stroke-width="2" stroke-linecap="round" stroke-dasharray="24.005207061767578" style="stroke-dashoffset: 0px;"></path>
                        <path id="path10" d="M247.8,191.2 L247.8,219.9" stroke="#142D52" stroke-width="2" stroke-linecap="round" stroke-dasharray="28.699996948242188" style="stroke-dashoffset: 0px;"></path>
                        <path id="path9" d="M238.2,195.9 L238.2,219.9" stroke="#142D52" stroke-width="2" stroke-linecap="round" stroke-dasharray="24" style="stroke-dashoffset: 0px;"></path>
                        <path id="path8" d="M228.6,210.3 L228.6,219.9" stroke="#142D52" stroke-width="2" stroke-linecap="round" stroke-dasharray="9.599990844726562" style="stroke-dashoffset: 0px;"></path>
                        <path id="path7" d="M219,217.5 L219,222.3" stroke="#142D52" stroke-width="2" stroke-linecap="round" stroke-dasharray="4.8000030517578125" style="stroke-dashoffset: 0px;"></path>
                        <path id="path6" d="M209.5,219.9 L209.5,229.4" stroke="#142D52" stroke-width="2" stroke-linecap="round" stroke-dasharray="9.5" style="stroke-dashoffset: 0px;"></path>
                        <path id="path5" d="M199.9,219.9 L199.9,243.8" stroke="#142D52" stroke-width="2" stroke-linecap="round" stroke-dasharray="23.900009155273438" style="stroke-dashoffset: 0px;"></path>
                        <path id="path4" d="M190.3,219.9 L190.3,248.6" stroke="#142D52" stroke-width="2" stroke-linecap="round" stroke-dasharray="28.70001220703125" style="stroke-dashoffset: 0px;"></path>
                        <path id="path3" d="M180.8,219.9 L180.8,243.8" stroke="#142D52" stroke-width="2" stroke-linecap="round" stroke-dasharray="23.900009155273438" style="stroke-dashoffset: 0px;"></path>
                        <path id="path2" d="M171.2,229.4 L171.2,38 C171.2,32.7 175.5,28.4 180.8,28.4 C180.8,28.4 180.8,28.4 180.8,28.4 L257.4,28.4 C262.7,28.4 267,32.7 267,38 L267,162.4 C267,167.7 271.3,172 276.6,172 L401,172 C406.3,172 410.6,176.3 410.6,181.6 L410.6,258.2 C410.6,263.5 406.3,267.8 401,267.8 C401,267.8 401,267.8 401,267.8 L362.7,267.8" stroke="#142D52" stroke-width="2" stroke-linecap="round" stroke-dasharray="707.1048583984375" style="stroke-dashoffset: 0px;"></path>
                        <path id="path1" d="M161.6,219.5 L161.6,223.1" stroke="#142D52" stroke-width="2" stroke-linecap="round" stroke-dasharray="3.600006103515625" style="stroke-dashoffset: 0px;"></path>
                        <path id="bg2" d="M170.2,81.9 C170.5,92.8 168.3,103.6 167.3,114.4 C166.4,124 166.5,133.6 166.5,143.2 L166.6,178.4 L166.9,253.2 C167.1,299.1 167.2,345 168.2,390.9 C168.3,396.5 168.5,402.4 171.6,407.1 C175.4,412.8 182.5,415.2 189.3,415.6 C196.1,416 202.9,414.7 209.7,414.8 C219,414.9 228.1,417.5 237.4,418.1 C246.7,418.7 256.9,416.9 263.1,410 C269.5,402.8 269.9,392.2 269.9,382.5 C270,369.5 270,356.3 267.2,343.5 C265.9,337.7 264.1,332 263.8,326.1 C263.4,317.1 266.7,308.4 268.2,299.6 C271.5,279.7 265.3,259.5 264.6,239.3 C264.2,226.5 266,213.8 266.3,201 C266.9,172.8 260.3,144.2 266.4,116.8 C269,105 274,93 271.3,81.1 C270.3,76.6 268.1,72.3 266.8,67.9 C264.6,60.1 265,51.9 265.6,43.9 C266,38.9 266,32.9 261.9,30 C259.8,28.5 257,28.2 254.4,28 C239.8,27 225.3,25.9 210.7,24.9 C199.9,24.1 186.5,22.1 176.6,27.8 C158.2,38.4 169.8,65.4 170.2,81.9 Z" fill="#2EBBC4" opacity="0.2"></path>
                        <path id="bg1" d="M31.2,170.8 C26.2,174 24.8,176.7 25,182.6 C25.2,188.5 26.9,194.3 26.9,200.3 C26.9,206.9 24.8,213.3 23.7,219.8 C21,236 24.4,252.4 28.2,268.4 C28.7,270.5 30.7,271.8 32.8,271.5 C51.3,268.5 70.1,265.9 88.7,268.5 C96.1,269.5 103.4,271.4 110.8,272.2 C120.2,273.2 129.6,272.5 139,271.9 L215.5,266.4 C225.1,265.7 234.8,265 244.4,266.2 C252.1,267.1 261,266.8 268.8,266.8 C277.8,266.9 286.8,266.4 295.8,265.3 C312.2,263.4 328.7,267.3 345.2,269 C364.3,271 383.6,270.3 402.4,266.7 C405.1,266.2 408,265.5 409.8,263.5 C414.6,258.1 408.5,250.2 406.8,243.2 C405.5,237.6 407.2,231.9 408.5,226.3 C411.2,215.2 412.4,203.7 412,192.3 C411.8,184.8 410.3,176.4 404.1,172.3 C398.7,168.8 391.8,169.8 385.4,170.3 C355.8,172.8 326,163 296.4,166.2 C286,167.3 275.8,170.2 265.4,170.6 C250,171.1 259.3,161.4 212.6,167.1 C198.1,168.9 184.5,171 170,169.3 C140.6,165.9 111,166.7 81.5,166.5 C67.2,166.5 52.9,167.5 38.8,169.3 C35.5,169.7 32,170.2 29.3,172.2 C26.6,174.2 25.4,178.5 27.7,181" fill="#7AC145" opacity="0.2"></path>
                      </g>
                    </g>
                  </svg>
                </span>
                {{ list.title }}
                <span class="list-drag-handle delete-icon" @click="removecard">
                  <svg width="226" height="224" viewBox="0 0 226 224" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M87.898 81.0816C84.5306 81.0816 81.7755 83.8367 81.7755 87.2041V170.163C81.7755 173.531 84.5306 176.286 87.898 176.286C91.2653 176.286 94.0204 173.531 94.0204 170.163V87.2041C94.0204 83.8367 91.2653 81.0816 87.898 81.0816Z" fill="#707070"/>
                    <path fill-rule="evenodd" clip-rule="evenodd" d="M79.7755 87.2041C79.7755 82.7321 83.426 79.0816 87.898 79.0816C92.3699 79.0816 96.0204 82.7321 96.0204 87.2041V170.163C96.0204 174.635 92.3699 178.286 87.898 178.286C83.426 178.286 79.7755 174.635 79.7755 170.163V87.2041ZM81.7755 87.2041C81.7755 83.8367 84.5306 81.0816 87.898 81.0816C91.2653 81.0816 94.0204 83.8367 94.0204 87.2041V170.163C94.0204 173.531 91.2653 176.286 87.898 176.286C84.5306 176.286 81.7755 173.531 81.7755 170.163V87.2041Z" fill="#707070"/>
                    <path d="M138.102 81.0816C134.735 81.0816 131.98 83.8367 131.98 87.2041V170.163C131.98 173.531 134.735 176.286 138.102 176.286C141.469 176.286 144.225 173.531 144.225 170.163V87.2041C144.225 83.8367 141.469 81.0816 138.102 81.0816Z" fill="#707070"/>
                    <path fill-rule="evenodd" clip-rule="evenodd" d="M129.98 87.2041C129.98 82.7321 133.63 79.0816 138.102 79.0816C142.574 79.0816 146.225 82.7321 146.225 87.2041V170.163C146.225 174.635 142.574 178.286 138.102 178.286C133.63 178.286 129.98 174.635 129.98 170.163V87.2041ZM131.98 87.2041C131.98 83.8367 134.735 81.0816 138.102 81.0816C141.469 81.0816 144.225 83.8367 144.225 87.2041V170.163C144.225 173.531 141.469 176.286 138.102 176.286C134.735 176.286 131.98 173.531 131.98 170.163V87.2041Z" fill="#707070"/>
                    <path d="M139.939 2.40814H86.0612C74.1225 2.40814 64.6327 11.8979 64.6327 23.8367V35.7755H8.61226C5.24491 35.7755 2.48981 38.5306 2.48981 41.8979C2.48981 45.2653 5.24491 48.0204 8.61226 48.0204H27.898L37.6939 201.388C38.3061 212.714 47.7959 221.592 59.1225 221.592H166.878C178.204 221.592 187.694 212.714 188.306 201.388L198.102 48.0204H217.388C220.755 48.0204 223.51 45.2653 223.51 41.8979C223.51 38.5306 220.755 35.7755 217.388 35.7755H161.367V23.8367C161.367 11.8979 151.878 2.40814 139.939 2.40814ZM76.8776 23.8367C76.8776 18.6326 80.8572 14.653 86.0612 14.653H139.939C145.143 14.653 149.122 18.6326 149.122 23.8367V35.7755H76.8776V23.8367ZM176.061 200.775C175.755 205.673 171.776 209.347 166.878 209.347H59.1225C54.2245 209.347 50.2449 205.673 49.9388 200.775L40.1429 48.0204H185.857L176.061 200.775Z" fill="#707070"/>
                    <path fill-rule="evenodd" clip-rule="evenodd" d="M174.065 200.651L174.065 200.648L183.725 50.0204H42.2752L51.9349 200.651C52.174 204.477 55.2626 207.347 59.1225 207.347H166.878C170.737 207.347 173.826 204.477 174.065 200.651ZM49.9388 200.775C50.2449 205.673 54.2245 209.347 59.1225 209.347H166.878C171.776 209.347 175.755 205.673 176.061 200.775L185.857 48.0204H40.1429L49.9388 200.775ZM86.0612 0.408142H139.939C152.982 0.408142 163.367 10.7934 163.367 23.8367V33.7755H217.388C221.86 33.7755 225.51 37.426 225.51 41.8979C225.51 46.3699 221.86 50.0204 217.388 50.0204H199.978L190.303 201.496C190.303 201.499 190.303 201.502 190.303 201.505C189.628 213.901 179.25 223.592 166.878 223.592H59.1225C46.7499 223.592 36.3727 213.902 35.6973 201.506C35.6972 201.502 35.697 201.499 35.6968 201.496L26.0216 50.0204H8.61226C4.14034 50.0204 0.489807 46.3699 0.489807 41.8979C0.489807 37.426 4.14034 33.7755 8.61226 33.7755H62.6327V23.8367C62.6327 10.7934 73.0179 0.408142 86.0612 0.408142ZM27.898 48.0204L37.6939 201.388C38.3061 212.714 47.7959 221.592 59.1225 221.592H166.878C178.204 221.592 187.694 212.714 188.306 201.388L198.102 48.0204H217.388C220.755 48.0204 223.51 45.2653 223.51 41.8979C223.51 38.5306 220.755 35.7755 217.388 35.7755H161.367V23.8367C161.367 11.8979 151.878 2.40814 139.939 2.40814H86.0612C74.1225 2.40814 64.6327 11.8979 64.6327 23.8367V35.7755H8.61226C5.24491 35.7755 2.48981 38.5306 2.48981 41.8979C2.48981 45.2653 5.24491 48.0204 8.61226 48.0204H27.898ZM86.0612 16.653C81.9617 16.653 78.8776 19.7372 78.8776 23.8367V33.7755H147.122V23.8367C147.122 19.7372 144.038 16.653 139.939 16.653H86.0612ZM86.0612 14.653C80.8572 14.653 76.8776 18.6326 76.8776 23.8367V35.7755H149.122V23.8367C149.122 18.6326 145.143 14.653 139.939 14.653H86.0612Z" fill="#707070"/>
                  </svg>
                </span>
              </div>

              <Container
                group-name="list"
                drag-class="card-ghost"
                drop-class="card-ghost-drop"
                non-drag-area-selector=".icon"
                :animation-duration="100"
                @drop="e => onCardDrop(e, list, listIndex)"
              >
                <Draggable v-for="item in list.items" :key="item.id">
                  <Card :item="item" @edit="editItem"/>
                </Draggable>

              </Container>

              <div class="item-entry">
                <ui-item-entry :list-id="list.id"
                               placeholder="Add new card"
                               icon="ellipsis-h"
                               @enter="onAddItem"/>
              </div>

            </section>

          </Draggable>

        </Container>

        <div class="new-list">
          <ui-item-entry placeholder="Add new list" @enter="onAddList"/>
        </div>
      </div>

    </div>

    <ui-modal ref="modal"
              :active="modal"
              :cancellable="1"
              @close="hideModal"
    >
      <UiItemForm ref="form"
                  @submit="onAddFullItem"
                  @cancel="hideModal"/>
    </ui-modal>

  </div>

</template>

<script>
import { Container, Draggable } from 'vue-smooth-dnd'

import Card from './Card'
import UiItemForm from '../ui/UiItemForm'
import UiItemEntry from '../ui/UiItemEntry'
import { makeDropHandler } from '../../utils/plugins'

export default {
  components: {
    Container,
    Draggable,
    UiItemEntry,
    UiItemForm,
    Card,
  },

  data: function () {
    return {
      modal: false,
      activeListId: null,
    }
  },

  computed: {
    lists () {
      return this.$store.state.board.lists
    }
  },

  methods: {
    onAddList ({ text }) {
      this.$store.commit('addList', { title: text })
      this.$nextTick(() => {
        const lists = this.$refs.list
        lists[lists.length - 1]
          .querySelector('input')
          .focus()
      })
    },

    onAddItem ({ id, text, more }) {
      if (more) {
        this.activeListId = id
        this.modal = true
        this.showModal({ title: text })
        return
      }
      this.addItem(id, text)
    },

    onAddFullItem (item) {
      item.id
        ? this.$store.commit('updateItem', { itemId: item.id, item })
        : this.addItem(this.activeListId, item.title, item.description, item.date)
      this.hideModal()
    },

    addItem (listId, title, description, date) {
      this.$store.commit('addItem', { listId, title, description, date })
    },

    editItem (item) {
      this.showModal(item)
    },

    onListDrop: makeDropHandler('onListDropComplete'),

    onListDropComplete: function (src, trg) {
      this.$store.commit('moveList', [src.index, trg.index])
    },

    onCardDrop: makeDropHandler('onCardDropComplete'),

    onCardDropComplete (src, trg, element, payload) {
      this.$store.commit('moveItem', [
        src.params[1],
        src.index,
        trg.params[1],
        trg.index,
      ])
    },

    showModal (item) {
      this.modal = true
      this.$nextTick(() => {
        this.$refs.form.show(item)
      })
    },

    hideModal () {
      this.focusInput(this.activeListId)
      this.modal = false
    },

    focusInput (listId) {
      const index = this.lists.findIndex(list => list.id === listId)
      if (index > -1) {
        this.$refs.list[index].querySelector('input').focus()
      }
    },

    reset () {
      if (confirm('Are you sure you want to reset the board?')) {
        this.$store.commit('reset')
      }
    },

    removecard () {
      document.getElementById("each-card").remove();
    }
  }
}
</script>

<style lang="scss">
  .board {
    margin-top: 20px;
    white-space: nowrap;
    > * {
      display: inline-block;
    }

    .new-list {
      margin-top: 10px;
    }
  }

  $column-width: 320px;

  .list-container {
    width: 290px;
    padding: 10px;
    margin: 5px;
    margin-right: 2rem;
    background-color: #29bbc4;
    box-shadow: 0 1px 1px rgba(0, 0, 0, 0.12), 0 1px 1px rgba(0, 0, 0, 0.24);
  }

  .lists-container {
    > * {
      display: inline-block;
      vertical-align: top;
    }
  }

  .list-header {
    margin-bottom: 5px;
    font-size: 18px;
    color: #FFFF;
    font-weight: bold;
  }

  .card {
    margin: 5px;
    background-color: #ffff;
    box-shadow: 0 1px 1px rgba(0, 0, 0, 0.12), 0 1px 1px rgba(0, 0, 0, 0.24);
    padding: 10px;
  }

  .card-ghost {
    transition: 0.25s all;
    box-shadow: 0 5px 10px rgba(0, 0, 0, 0.12);
    transform: scale(1.1);
  }

  .card-ghost-drop {
    transform: scale(1);
  }

  .list-drag-handle {
    cursor: move;
    padding: 5px;
    svg {
      width: 25px;
      height: 25px;
      display: inline-block;
      vertical-align: middle;
    }
  }
  .delete-icon {
    float: right;
    padding: 0;
    cursor: pointer;
  }
  .item-entry {
    padding-top: 10px;
    margin-top: 10px;
    border-top: 1px solid #DDD;
  }

  .new-list {
    width: 290px;
    margin-left: -10px;
  }

  .clear-button {
    position: absolute;
    top: 20px;
    right: 20px;
    z-index: 1;
    .control {
      position: fixed;
      right: 0;
      padding-right: 1rem;
    }
    button {
      color: #CC0000;
      border: 1px solid #CC0000;
    }
  }
</style>

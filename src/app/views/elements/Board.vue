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
                <div class="list-head-outer">
                  <span class="list-drag-handle">
                    <img src="../../../../docs/doodle-logo.png" alt="logo">
                  </span>
                  {{ list.title }}
                </div>
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
    background-color: #006ada;
    box-shadow: 0 1px 1px rgba(0, 0, 0, 0.12), 0 1px 1px rgba(0, 0, 0, 0.24);
  }

  .lists-container {
    > * {
      display: inline-block;
      vertical-align: top;
    }
  }
  .list-head-outer {
    flex: 1 1 0;
    display: flex;
    justify-content: flex-start;
    align-items: center;
  }
  .list-header {
    margin-bottom: 5px;
    font-size: 18px;
    color: #FFFF;
    font-weight: bold;
    display: flex;
    align-items: center;
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

<template>
  <div class="d-flex align-items-center justify-content-between w-100">
    <span class="mr-2">{{ bot.botName || bot.botId }}</span>

    <div class="align-items-center d-flex">
      <span class="ml-2 mr-1 align-middle">{{
        allIsBotOnline[bot.botId] ? '&#128994;' : '&#128308;'
      }}</span>
      <b-form-checkbox
        v-model="autoRefreshLoc"
        class="ml-auto float-right mr-2 my-auto"
        title="AutoRefresh"
        variant="secondary"
        @change="changeEvent"
      >
        R
      </b-form-checkbox>
      <div v-if="!noButtons" class="d-flex flex-align-cent">
        <!-- <b-button class="ml-1" size="sm" title="Edit bot">
          <EditIcon :size="16" title="Edit Button" />
        </b-button> -->
        <b-button class="ml-1" size="sm" title="Delete bot" @click.prevent="clickRemoveBot(bot)">
          <DeleteIcon :size="16" title="Delete Bot" />
        </b-button>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import { namespace } from 'vuex-class';
import { MultiBotStoreGetters } from '@/store/modules/botStoreWrapper';
import LoginModal from '@/views/LoginModal.vue';
import EditIcon from 'vue-material-design-icons/Cog.vue';
import DeleteIcon from 'vue-material-design-icons/Delete.vue';
import { BotDescriptor, BotDescriptors } from '@/types';
import StoreModules from '@/store/storeSubModules';

const ftbot = namespace(StoreModules.ftbot);

@Component({ components: { LoginModal, DeleteIcon, EditIcon } })
export default class BotList extends Vue {
  @Prop({ default: false, type: Object }) bot!: BotDescriptor;

  @Prop({ default: false, type: Boolean }) noButtons!: boolean;

  @ftbot.Getter [MultiBotStoreGetters.allIsBotOnline];

  @ftbot.Getter [MultiBotStoreGetters.allAutoRefresh];

  @ftbot.Getter [MultiBotStoreGetters.allAvailableBots]: BotDescriptors;

  @ftbot.Action removeBot;

  @ftbot.Action selectBot;

  get autoRefreshLoc() {
    return this.allAutoRefresh[this.bot.botId];
  }

  set autoRefreshLoc(v) {
    // Dummy setter - Set via change event to avoid bouncing
  }

  changeEvent(v) {
    this.$store.dispatch(`ftbot/${this.bot.botId}/setAutoRefresh`, v);
  }

  clickRemoveBot(bot: BotDescriptor) {
    //
    this.$bvModal
      .msgBoxConfirm(`Really remove (logout) from '${bot.botName}' (${bot.botId})?`)
      .then((value: boolean) => {
        if (value) {
          this.removeBot(bot.botId);
        }
      });
  }
}
</script>

<style scoped></style>

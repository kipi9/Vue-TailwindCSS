<template>
    <div class="flex justify-between py-6">
        <div class="flex">
            <div class="w-12 h-12 relative mr-3">
                <img src="/images/avatars/avatar_user_default.png" class="w-12 h-auto max-w-12" />
                <img :src="statusIconUrl" class="absolute bottom-0 right-0"/>
            </div>
            <div class="flex flex-col">
                <p>
                    <span class="text-light text-sm mr-3">@{{name}} placed a bet on</span>
                    <span class="text-dark text-sm">{{title}}</span>
                </p>
                <div class="mt-2" v-if="isCommentVisible">
                    <p class="text-sm text-dark mb-2">{{comment}}</p>
                     <div class="text-dark text-sm flex items-center mr-6">
                        <img src="/images/icons/icon_message.svg" class="mr-2" />
                        <span>Comment</span>
                    </div>
                </div>
                <div class="flex items-center mt-1" v-if="!isCommentVisible">
                    <div class="text-dark text-sm flex items-center mr-6">
                        <img src="/images/icons/icon_expand.svg" class="mr-2" />
                        <span>Bet Now</span>
                    </div>
                    <div class="text-dark text-sm flex items-center" v-if="isCopyable">
                        <img src="/images/icons/icon_copy.svg" class="mr-2" />
                        <span>Copy trade</span>
                    </div>
                </div>
            </div>
        </div>
        <div class="text-dark text-sm w-20 text-right">2m ago</div>
    </div>
</template>

<script lang="ts">
import { defineComponent, PropType } from "vue"

export default defineComponent({
    props: {
        name: {
            type: String as PropType<string>,
            required: true
        },
        title: {
            type: String as PropType<string>,
            required: true
        },
        isCopyable: {
            type: Boolean as PropType<boolean>,
            default: true
        },
        isCommentVisible: {
            type: Boolean as PropType<boolean>,
            default: false
        },
        comment: {
            type: String as PropType<string | null>
        },
        statusIconUrl: {
            type: String as PropType<string>,
            default: "status1.svg"
        }
    }
})
</script>
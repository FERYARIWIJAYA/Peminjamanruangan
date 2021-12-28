<template>
    <KTCard ref="preview" v-bind:title="title" v-bind:example="true">
        <template v-slot:title v-if="hasTitleSlot">
        <h3 class="card-title">
            <slot name="title"></slot>
        </h3>
        </template>

        <template v-slot:body>
        <!--begin::Code example-->

        <div role="group" class="mt-5">
            <div class="row">
            <div class="col-xxl-12">
                <ListPeminjaman></ListPeminjaman>
            </div>
            </div>
        </div>

        <!--end::Code example-->

        <slot name="preview"></slot>
        </template>
    </KTCard>
    </template>
    <script>
    import KTCard from "@/view/content/Card.vue";
    import ListPeminjaman from "@/view/content/widgets/peminjaman/listpeminjaman.vue";
    import { SET_BREADCRUMB } from "@/core/services/store/breadcrumbs.module";

    export default {
    name: "peminjaman",
    mounted() {
        this.$store.dispatch(SET_BREADCRUMB, [{ title: "Peminjaman" }]);
    },
    props: {
        title: String,
    },
    components: {
        KTCard,
        ListPeminjaman,
    },
};
</script>
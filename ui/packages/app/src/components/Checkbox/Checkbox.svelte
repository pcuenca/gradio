<script lang="ts">
	import { Checkbox } from "@gradio/form";
	import { Block } from "@gradio/atoms";
	import StatusTracker from "../StatusTracker/StatusTracker.svelte";
	import type { LoadingStatus } from "../StatusTracker/types";

	export let elem_id: string = "";
	export let visible: boolean = true;
	export let value: boolean = false;
	export let label: string = "Checkbox";
	export let mode: "static" | "dynamic";
	export let form_position: "first" | "last" | "mid" | "single" = "single";
	export let show_label: boolean;
	export let style: Record<string, any> = {};

	export let loading_status: LoadingStatus;
</script>

<Block {form_position} {elem_id} {visible} {style}>
	<StatusTracker {...loading_status} />

	<Checkbox
		{label}
		{show_label}
		{style}
		bind:value
		on:change
		disabled={mode === "static"}
	/>
</Block>

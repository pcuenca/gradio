<script lang="ts">
	import { CheckboxGroup } from "@gradio/form";
	import { Block } from "@gradio/atoms";
	import StatusTracker from "../StatusTracker/StatusTracker.svelte";
	import type { LoadingStatus } from "../StatusTracker/types";

	export let elem_id: string = "";
	export let visible: boolean = true;
	export let value: Array<string> = [];
	export let choices: Array<string>;
	export let style: Record<string, any> = {};

	export let mode: "static" | "dynamic";
	export let label: string = "Checkbox Group";
	export let form_position: "first" | "last" | "mid" | "single" = "single";
	export let show_label: boolean;

	export let loading_status: LoadingStatus;
</script>

<Block {form_position} {elem_id} {visible} {style} type="fieldset">
	<StatusTracker {...loading_status} />

	<CheckboxGroup
		bind:value
		{choices}
		{label}
		{style}
		{show_label}
		on:change
		disabled={mode === "static"}
	/>
</Block>

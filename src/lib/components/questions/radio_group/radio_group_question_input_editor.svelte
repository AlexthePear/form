<script lang="ts">
	import type { RadioGroupQuestion } from '$lib/form';
	import RadioGroupQuestionInput from './radio_group_question_input.svelte';
	import BaseEditor from '../base/base_editor.svelte';
	import ChoiceEditor from '../base/choice_editor.svelte';
	// import { AuditLogOptionsType } from 'discord-api-types/v10';

	export var data = $$props as RadioGroupQuestion;
</script>

<BaseEditor bind:data>
	<fieldset>
		<legend>allow custom choice</legend>
		<input
			name="form[questions][data][{data.position}][allowCustomChoice]"
			type="checkbox"
			bind:value={data.allowCustomChoice}
		/>
	</fieldset>
	<fieldset>
		<legend>default choice index</legend>
		<input
			name="form[questions][data][{data.position}][choiceIndex]"
			type="number"
			bind:value={data.choiceIndex}
		/>
	</fieldset>
	<fieldset>
		<legend>defualt custom choice string</legend>
		<input
			name="form[questions][data][{data.position}][customChoice]"
			type="text"
			bind:value={data.customChoice}
		/>
	</fieldset>
	<fieldset>
		<legend>defualt value</legend>
		<input
			name="form[questions][data][{data.position}][value]"
			type="text"
			bind:value={data.value}
		/>
	</fieldset>
	<h4>Edit Choices</h4>
	<ChoiceEditor
		prefix={`form[questions][data][${data.position}][choices]`}
		bind:data={data.choices}
	/>
	<svelte:fragment slot="preview">
		<div class="question">
			<RadioGroupQuestionInput {data} />
		</div>
	</svelte:fragment>
</BaseEditor>

<script>
    import { notes, currentPage, currentChapter } from '../store.js';
    import { Button, buttonVariants } from "$lib/components/ui/button"
    import * as Dialog from "$lib/components/ui/dialog";

    let newNote = '';
  
    // Function to add a new note
    function addNote() {
        if (newNote.trim() !== '') {
            notes.update(n => [...n, { page: $currentPage, text: newNote }]);
            newNote = '';
        }
    }
  
    // Function to remove a note by its index
    function removeNote(index) {
        notes.update(n => n.filter((_, i) => i !== index));
    }
</script>
  
<style>
    .note-item {
      margin-bottom: 10px;
    }
  
    .add-note {
      display: flex;
      margin-top: 20px;
    }
  
    .add-note input {
      flex: 1;
      padding: 8px;
      border-radius: 5px;
      border: none;
    }
  
    .add-note button {
      padding: 8px 12px;
      border-radius: 5px;
      background-color: #ffdd57;
      color: #000;
      border: none;
      cursor: pointer;
    }

    .remove-button {
      margin-left:15px;
      padding: 6px;
      border-radius: 5px;
      background-color: #ffdd57;
      color: #000;
      border: none;
      cursor: pointer;
    }

</style>
  
<div class="main">
    <h2 class="">Your Notes</h2>
    <div class="mb-4">
      <Dialog.Root>
        <Dialog.Trigger class={buttonVariants({ variant: "outline" })}
          >Add Note</Dialog.Trigger
        >
        <Dialog.Content class="sm:max-w-[425px]">
          <Dialog.Header>
            <Dialog.Title>Add Note</Dialog.Title>
            <Dialog.Description>
              Create any notes or annotations for the current page here. Click add when you're done.
            </Dialog.Description>
          </Dialog.Header>
          <div class="add-note">
            <input type="text" bind:value={newNote} placeholder="Write a note..." />
            <button on:click={addNote}>Add</button>
          </div>
        </Dialog.Content>
      </Dialog.Root>
    </div>
    

    <p class="positionMarking">Current Chapter: {$currentChapter}, Current Page: {$currentPage}</p>
    {#if $notes.length === 0}
      <p>No notes yet. Add some!</p>
    {/if}
    <ul>
      {#each $notes as note, index}
        <li class="note-item">
            <strong>Page {note.page}:</strong> {note.text}
            <button class="remove-button" on:click={() => removeNote(index)}>Remove</button>
        </li>
      {/each}
    </ul>
</div>

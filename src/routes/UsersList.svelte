<script lang="ts">
    import { Table, TableBody, TableBodyCell, TableBodyRow, TableHead, TableHeadCell, Checkbox, TableSearch } from 'flowbite-svelte';
    
    import { createEventDispatcher } from 'svelte'; 

    const dispatch = createEventDispatcher();

    export let users: User[];

    function rowClickHandler(event: any) {
        console.log("row clicked", event.target.parentNode.parentNode.id);
        dispatch('select', { id: event.target.parentNode.parentNode.id });
    }
</script>

<!-- display a list of users only display their Id, name and username -->
<!-- when the select button is clicked the selected User table updates to show their details -->

<div class="relative overflow-x-auto">
    <Table>
        <TableHead>
            <TableHeadCell scope="col" class="px-6 py-3">
                ID
            </TableHeadCell>
            <TableHeadCell scope="col" class="px-6 py-3">
                Name
            </TableHeadCell>
            <TableHeadCell scope="col" class="px-6 py-3">
                Username
            </TableHeadCell>
        </TableHead>
        <TableBody>
            {#each users as user}
                <TableBodyRow id={user.id} class="bg-white border-b dark:bg-gray-800 dark:border-gray-700">
                    <TableHeadCell scope="row" class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap dark:text-white">
                        {user.id}
                    </TableHeadCell>
                    <TableBodyCell class="px-6 py-4">
                        {user.name}
                    </TableBodyCell>
                    <TableBodyCell class="px-6 py-4">
                        {user.username}
                    </TableBodyCell>
                    <TableBodyCell class="px-6 py-4">
                        <button type="button" class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 me-2 mb-2 dark:bg-blue-600 dark:hover:bg-blue-700 focus:outline-none dark:focus:ring-blue-800" on:click={rowClickHandler}>Select</button>
                    </TableBodyCell>
                </TableBodyRow>
            {/each}
        </TableBody>
    </Table>
</div>

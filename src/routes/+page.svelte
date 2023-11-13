<script lang="ts">
    import { Heading, Label, Input } from 'flowbite-svelte';
    import { onMount } from "svelte";
    import UsersList from "./UsersList.svelte";

    let users: User[] = [];
    let selectedUser: User;

    onMount(async () => {
        users = await getUsers();
    });

async function getUsers() {
        return await fetch('https://jsonplaceholder.typicode.com/users')
            .then(response => response.json())
            .then(json => json)
    }
</script>
  

<div class="md:container md:mx-auto px-4 bg-gray-50 dark:bg-gray-700">
    <!-- The Selected User section needs to go into a seperate component -->
    <Heading>Selected User:</Heading>
    <br>
    <form>
        <div class="grid gap-6 mb-6 md:grid-cols-2 ">
            <div>
                <Label for="id">ID</Label>
                <Input type="number" id="id" />
            </div>
            <div>
                <Label for="name">Name</Label>
                <Input type="text" id="name" />
            </div>
            <div>
                <Label for="username">Username</Label>
                <Input type="text" id="username" />
            </div>
            <div>
                <Label for="phone">Phone</Label>
                <Input type="text" id="phone" />
            </div>
            <div>
                <!-- This is an example of what things look like as TailwindCSS.  Convert the below to Flowbite -->
                <label for="website" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Website</label>
                <input type="text" id="website" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500">
            </div>
        </div>
    </form>

    <hr>
    {#if users}
    <UsersList {users} />
    {/if}
</div>





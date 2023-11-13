<script lang="ts">
    import { Heading, Input, Label } from 'flowbite-svelte';
    export let selectedUser: User;
    console.log("selectedUser", selectedUser);
    console.log("selectedUser ID", selectedUser.id);

</script>


<Heading>Selected User:</Heading>
    <br>
    <form>
        <div class="grid gap-6 mb-6 md:grid-cols-2 ">
            <div>
                <Label for="id">ID</Label>
                <Input bind:value={selectedUser.id} type="number" id="id" />
            </div>
            <div>
                <Label for="name">Name</Label>
                <Input bind:value={selectedUser.name} type="text" id="name" />
            </div>
            <div>
                <Label for="username">Username</Label>
                <Input bind:value={selectedUser.username} type="text" id="username" />
            </div>
            <div>
                <Label for="phone">Phone</Label>
                <Input bind:value={selectedUser.phone} type="text" id="phone" />
            </div>
            <div>
                <Label for="website">Website</Label>
                <Input bind:value={selectedUser.website} type="text" id="website" />
            </div>
        </div>
    </form>
<script lang="ts">
    
    import { onMount } from "svelte";
    import UsersList from "./UsersList.svelte";
    import SelectedUser from './SelectedUser.svelte';
  

    let users: User[] = [];
    let selectedUser: User = {
        id: 0,
        name: "",
        username: "",
        // email: "",
        // address: {
        //     street: "",
        //     suite: "",
        //     city: "",
        //     zipcode: "",
        //     geo: {
        //         lat: "",
        //         lng: ""
        //     }
        // },
        phone: "",
        website: "",
        // company: {
        //     name: "",
        //     catchPhrase: "",
        //     bs: ""
        // }
    };

    onMount(async () => {
        users = await getUsers();
    });

    
    async function getUsers() {
            return await fetch('https://jsonplaceholder.typicode.com/users')
                .then(response => response.json())
                .then(json => json)
        }
    
    function handleSelect(event: any) {
        console.log("handleSelect", event.detail.id);
        console.log(users.find(user => user.id == event.detail.id));

        
        // selectedUser = users.find(user => user.id == event.detail.id);//typescript error
        let testSelectedUser: User | undefined;
        testSelectedUser = users.find(user => user.id == event.detail.id);
        if (testSelectedUser===undefined){
            throw new TypeError("selectedUser is undefined");
        } else {
            selectedUser = testSelectedUser;
        }  
    }
</script>
  

<div class="md:container md:mx-auto px-4 bg-gray-50 dark:bg-gray-700">
    <!-- The Selected User section needs to go into a seperate component -->
    
    <SelectedUser selectedUser={selectedUser} />


    <hr>
    {#if users}
        <UsersList {users} on:select={handleSelect}/>
    {/if}
</div>





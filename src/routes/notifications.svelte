<script context="module">
    import axios from 'axios';
    export async function preload(page,session){
        let args = '';
        if (session.token){
            args = '?t=' + session.token + '&ex=true';
        }else{
            this.redirect(302, '/');
        }
        const res = await axios.get('https://newapp.nl/api/notifications' + args).then(function (response) {
                return response.data;
            });
        const json = await res;
        return { notifications: json };
    }
</script>
<script>
import Notifications from '../components/Notifications.svelte';

export let notifications;

</script>

<Notifications not={notifications}/>
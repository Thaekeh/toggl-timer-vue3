<template>
    <tr>
        <td>
            {{ session.title }}
        </td>
        <td>
            {{ session.id }}
        </td>
        <td>
            {{ formatDate(session.startTime) }}
        </td>
    </tr>
</template>

<script>
export default {
    name: "SessionRow",
    props: ['session'],
    methods: {
        formatDate(time) {
            const dateObj = new Date(time);
            const hours = dateObj.getHours();
            const minutes = dateObj.getMinutes();
            const seconds = dateObj.getSeconds();
            return `${hours}:${minutes}:${seconds}`;
            // return new Date(time).getUTCHours();
            // new Date(val[0].value).toLocaleFormat('%m/%d/%Y')
        }
    }
}
</script>

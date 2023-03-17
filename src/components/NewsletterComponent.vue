<template>
    <section class="newsletter">
        <h2>Subscribe to our newsletter!</h2>
        <form>
            <div class="field">
                <input id="email" type="email" v-model=subscriberEmail placeholder="Your email address" required >
            </div>
            <div class="field">
                <input id="accept" type="checkbox" required>
                <label for="accept">I accept sharing my email and receiving emails periodically</label>
            </div>
            <button type="button" @click="sendNewsletter">Subscribe</button>
        </form>
    </section>
</template>

<script>
// this component has a bug, inspect it carefully and test it on the browser
export default {
    name: "NewsletterComponent",
    data() {
        return {
            subscriberEmail: ""
        }
    },
    methods: {
        sendNewsletter: function () {
            var form = document.querySelector("form")
            console.log("Check if information is correct before sending")
            if (form.reportValidity()) {
                var options = {
                    cache: "no-cache",
                    method: "GET",
                    referrerPolicy: "no-referrer",
                    headers: {
                        'Content-Type': 'application/json',
                    },
                    body: JSON.stringify({email: this.subscriberEmail})
                }
                fetch("/api/newsletters/add", options)
                    .then(function (response) {
                        return response.json()
                    })
                    .then(function (data) {
                        console.log(data)
                        alert(data.message)
                    })
                    .catch(function (error) {
                        console.log("Some error happened: " + error)
                    });
            }
        }
    }
}
</script>

<style lang="scss">
.newsletter {
    width: 70%;
    padding: 0 20px 20px 20px;
    margin: auto;
    margin-bottom: 50px;
    border-radius: 10px;
    background-color: #f1f6fb;
    border: 2px solid #E7F1FA;

    form {
        .field {
            margin-bottom: 10px;

            label {
                margin-right: 10px;
            }

            input[type=checkbox] {
                margin: 0 10px 20px 0;
            }
        }
    }
}
</style>
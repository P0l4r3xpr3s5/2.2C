<template>
    <div class="container mt-5">
        <div class="row justify-content-center">
            <div class="col-md-6">
                <form class="p-4 border rounded">
                    <h2 class="form-h2">Registration Form</h2>

                    <div class="mb-3">
                        <label for="name" class="form-label">Name:</label>
                        <input v-model="name" id="name" class="form-control" />
                    </div>

                    <div class="mb-3">
                        <label for="email" class="form-label">Email:</label>
                        <input v-model="email" id="email" class="form-control" type="email" />
                    </div>

                    <div class="mb-3">
                        <label for="password" class="form-label">Password:</label>
                        <input v-model="password" id="password" class="form-control" type="password" />
                    </div>

                    <div class="mb-3">
                        <label for="address" class="form-label">Address:</label><br>
                        <textarea v-model="address" id="address" class="form-control" rows="3"></textarea>
                    </div>

                    <div class="mb-3">
                        <label for="shippingAddress" class="form-label">Shipping Address:</label><br>
                        <textarea v-model="shippingAddress" id="shippingAddress" class="form-control" rows="3"></textarea>
                    </div>
    
                    <div class="mb-3">
                        <label for="creditCard" class="form-label">Credit Card Number:</label>
                        <input v-model="creditCard" id="creditCard" class="form-control" />
                    </div>

                    <div class="form-check mb-3">
                        <input v-model="termsAgreed" class="form-check-input" type="checkbox" id="termsAgreed" />
                        <label class="form-check-label" for="termsAgreed">I agree to the terms of service</label>
                    </div>
                    
                    <br>
                    <button @click="register" :disabled="!isValid" class="btn btn-primary">Register</button>
                </form>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            name: "",
            email: "",
            password: "",
            address: "",
            shippingAddress: "",
            creditCard: "",
            termsAgreed: false
        };
    },
    computed: {
        isValid() {
            return this.name && this.email && this.password && this.address && this.shippingAddress && this.creditCard && this.termsAgreed;
        }
    },
    methods: {
        register() {
            if (this.isValid) {
                if (window.confirm("Are you sure all your information is correct?")) {
                    this.$emit("user-registered", {
                        name: this.name,
                        email: this.email,
                        password: this.password,
                        address: this.address,
                        shippingAddress: this.shippingAddress,
                        creditCard: this.creditCard
                    });
                }
            }
        }
    }
};
</script>

<style scoped>
    .container {
        font-family: Arial, sans-serif;
        background-color: #f4f4f4;
        padding: 2rem;
    }
    .form-h2 {
        background-color: #333;
        color: white;
        text-align: center;
        padding: 1rem;
        font-size: 24px;
        margin-bottom: 1rem;
    }
    .form-label {
        color: #333;
        font-size: 20px;
        margin-bottom: 0.5rem;
    }
    .form-control {
        color: #777;
        font-size: 16px;
        line-height: 1.5;
        margin-bottom: 1rem;
    }
    .btn-primary {
        background-color: #333;
        color: white;
    }
</style>

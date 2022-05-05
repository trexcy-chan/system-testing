<template>
<content class="bg">
<div  v-if="fillup" class="grid min-h-screen place-items-center">
    <div class="w-full p-12 bg-white sm:w-8/12 md:w-1/2 lg:w-5/12">
     <h1 class="text-xl font-semibold">Hello there 👋, <span class="font-normal">Please fill in your information to register</span></h1>
     <form class="">
        <div class="flex w-full">
            <div class="grid grid-cols-1 px-3 w-1/2 text-left">
                <label class="block mt-2 text-xs font-semibold text-gray-600 uppercase ml-2">First Name 
                    <span class="text-red-500">*</span></label>
                <input v-model="first" class="py-2 px-3 rounded-lg border-2 border-teal-400 mt-1 focus:outline-none focus:ring-2 focus:ring-purple-600 focus:border-transparent" type="text" placeholder="First Name" />
            </div>
            <div class="grid grid-cols-1 px-3 w-1/2 text-left">
                <label class="block mt-2 text-xs font-semibold text-gray-600 uppercase ml-2">Middle Name 
                    <span class="text-red-500">*</span></label>
                <input v-model="middle" class="py-2 px-3 rounded-lg border-2 border-teal-400 mt-1 focus:outline-none focus:ring-2 focus:ring-purple-600 focus:border-transparent" type="text" placeholder="Middle Name" />
            </div>
        </div>
        <div class="flex w-full">
            <div class="grid grid-cols-1 px-3 w-1/2 text-left">
                <label class="block mt-2 text-xs font-semibold text-gray-600 uppercase ml-2">Last Name 
                    <span class="text-red-500">*</span></label>
                <input v-model="last" class="py-2 px-3 rounded-lg border-2 border-teal-400 mt-1 focus:outline-none focus:ring-2 focus:ring-purple-600 focus:border-transparent" type="text" placeholder="Last Name" />
            </div>
            <div class="grid grid-cols-1 px-3 w-1/2 text-left">
                <label class="block mt-2 text-xs font-semibold text-gray-600 ml-2">SUFFIX (n/a if none)</label>
                <input v-model="suffix" class="py-2 px-3 rounded-lg border-2 border-teal-400 mt-1 focus:outline-none focus:ring-2 focus:ring-purple-600 focus:border-transparent" type="text" placeholder="Suffix" />
            </div>
        </div>
        <div class="grid grid-cols-1 px-3 w-1/2 text-left">
            <label class="block mt-2 text-xs font-semibold text-gray-600 uppercase ml-2">Purok 
                <span class="text-red-500">*</span></label>
            <select v-model="purok"
             class="py-2 px-3 rounded-lg border-2 border-teal-400 mt-1 focus:outline-none focus:ring-2 focus:ring-purple-600 focus:border-transparent">
                <option value= "purok1">Purok 1</option>
                <option value= "purok2">Purok 2</option>
                <option value= "purok3">Purok 3</option>
            </select>
        </div>
        <div class="grid grid-cols-1 px-3 w-3/5 text-left">
            <label class="block mt-2 text-xs font-semibold text-gray-600 uppercase ml-2">Email Address 
                <span class="text-red-500">*</span></label>
            <input v-model="email" class="py-2 px-3 rounded-lg border-2 border-teal-400 mt-1 focus:outline-none focus:ring-2 focus:ring-purple-600 focus:border-transparent" type="text" placeholder="Email Address" />
        </div>
        
        <div class="grid grid-cols-1 px-3 w-3/5 text-left">
            <label class="block mt-2 text-xs font-semibold text-gray-600 uppercase ml-2">Password 
                <span class="text-red-500">*</span></label>
            <input v-model="password" class="py-2 px-3 rounded-lg border-2 border-teal-400 mt-1 focus:outline-none focus:ring-2 focus:ring-purple-600 focus:border-transparent" type="password" placeholder="Password" />
        </div>
        
        <div class="grid grid-cols-1 px-3 w-3/5 text-left">
            <label class="block mt-2 text-xs font-semibold text-gray-600 uppercase ml-2">Confirm Password 
                <span class="text-red-500">*</span></label>
            <input v-model="password2" class="py-2 px-3 rounded-lg border-2 border-teal-400 mt-1 focus:outline-none focus:ring-2 focus:ring-purple-600 focus:border-transparent" type="password" placeholder="Confirm Password" />
        </div>
        <div class="w-full grid place-items-center">
         <p @click="register" class="w-3/4 h-10 rounded-full bg-amber-500 hover:bg-amber-300 mt-3 text-center cursor-pointer text-xl text-white font-medium py-1">Sign Up</p>         
         <p @click="gtlogin" class="flex justify-between inline-block mt-2 text-xs text-blue-500 cursor-pointer hover:text-gray-500">Already registered?</p>
        </div>
        
     </form>
    </div>
</div>
<div  v-if="termscond" class="grid min-h-screen place-items-center">
    <div class="w-full p-12 bg-white sm:w-8/12 md:w-1/2 lg:w-5/12">
     <form @submit.prevent="signup">
     <h1 class="text-2xl font-semibold">Terms and Conditions</h1>

     <p class="font-normal text-justify ml-6">
            The application for a barangay certificate request may be forfeited if
             the information provided is incorrect or inaccurate. 
        </p>
        <br>
         <p class="font-normal text-justify ml-6">
            As such, by using the Barangay Certificate Issuance System for barangay certificate requests and 
            by using our services, you acknowledge and agree that the information you provide will be used and 
            disclosed by the BCIS Web App in accordance with any legal and regulatory standards and compliance
             with the <span class="font-semibold text-cyan-500">Data Privacy Act of 2012. </span>

        </p>
        <br>
        <p class="font-normal text-justify ml-6">
        Upon clicking the <span class="font-semibold text-red-500">“Accept”</span> button, users agree to 
        furnish, check, and verify the authenticity and correctness of the 
        information they provide on this system in connection with their application.</p>

        <div class="w-full flex justify-evenly">
         <input type="submit"  value="Accept" class="w-2/5 h-10 rounded-full bg-amber-500 hover:bg-amber-300 mt-3 text-center cursor-pointer text-xl text-white font-medium py-1"/>   
         <div @click="disagree" class="w-2/5 h-10 rounded-full bg-amber-500 hover:bg-amber-300 mt-3 text-center cursor-pointer text-xl text-white font-medium py-1">Disagree</div>   
        </div>
        
     </form>
    </div>
</div>
</content>  
</template>

<script>
import {createUserWithEmailAndPassword,} from "firebase/auth";
import { app } from "../firebase";
import { auth } from "../firebase";
import { getFirestore, setDoc, doc } from "firebase/firestore";
export default {
    data(){
        return{
            first:'',
            middle:'',
            last:'',
            suffix:'',
            purok:'',
            email:'',
            password:'',
            password2:'',
            fillup: true,
            termscond: false,
        }
    },
    methods:{
        async signup() {
        try {
            await createUserWithEmailAndPassword(auth, this.email, this.password);            
            const email =this.email; const first = this.first; const middle = this.middle;
            const last = this.last; const suffix = this.suffix; const purok = this.purok;
            const db = getFirestore(app);
            const userID = auth.currentUser.uid;
            console.log("Creating Data");
            const addedDocs = await setDoc(doc(db, "residents",userID ),{ userID, email, first, middle, last, suffix, purok, })
            this.$toast.success("Registered!", {position: "top"});
            console.log(addedDocs);
            this.$router.push(`/homepage/${auth.currentUser.uid}`);
        } catch (error) {
            switch (error.code) {
            case "auth/email-already-in-use":
                this.$toast.error("Email already in use", {
                    position: "top"
                });
                break;
            case "auth/operation-not-allowed":
                this.$toast.error("Operation not allowed", {
                    position: "top"
                });
                break;
            default:
                this.$toast.error("Something went wrong",{
                    position: "top"
                });
            }

        return;
      }            
        },
        register(){
            if(this.first==''){
                this.$toast.warning("Enter First Name", {
                    position: "top"
                });
            } else if(this.middle==''){
                this.$toast.warning("Enter Middle Name", {
                    position: "top"
                });
            }else if(this.last==''){
                this.$toast.warning("Enter Last Name", {
                    position: "top"
                });
            }else if(this.purok==''){
                this.$toast.warning("Choose Purok", {
                    position: "top"
                });
            }else if(this.email==''){
                this.$toast.warning("Enter Email Address", {
                    position: "top"
                });
            }else if(!this.validEmail(this.email)){
                this.$toast.error("Invalid Email Address", {
                    position: "top"
                });
            }else if(this.password.length < 7){
                this.$toast.warning("Please use at least 7 characters", {
                    position: "top"
                });
            }else if(this.password==''){
                this.$toast.warning("Enter Password", {
                    position: "top"
                });
            }else if(this.password2==''){
                this.$toast.warning("Confirm password", {
                    position: "top"
                });
            }else if(this.password!=this.password2){
                this.$toast.warning("Passwords do not Match", {
                    position: "top"
                });
            }
            else{
                this.fillup = false;
                this.termscond = true;
            }
            
        },
        disagree(){
            this.fillup = true;
            this.termscond = false;
        },
        gtlogin(){
        this.$router.push("/loginpage");
        },
        validEmail(email){
           const re = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
           return re.test(email)
       }
    }

}
</script>

# circom

# Step-by-Step Instructions for Setting Up and Generating Proofs
1. Setting Up the Keys

To generate the proving and verification keys from the .r1cs file, use the following commands:

    Run the setup (replace identity with the name of your circuit if it's different):

    bash

    $ snarkjs setup identity.r1cs

    If you encounter an error, ensure you're using the command correctly and you're in the directory where identity.r1cs is located.

2. Generate the Proving and Verification Keys

If the previous command didn’t work, use the correct approach with snarkjs as follows:

    Generate the keys with the following command:

    bash

 $ snarkjs r1cs export json identity.r1cs identity.json

This converts your .r1cs file to JSON format.

Next, use the groth16 protocol to set up the keys:

# bash

    $snarkjs groth16 setup identity.r1cs pot12_final.ptau proving_key.json verification_key.json

    Make sure you have a file named pot12_final.ptau in the same directory or provide the path to it.

3. Generate the Proof

After successfully generating the keys, you can then calculate the witness and generate the proof:

    Calculate the witness (make sure you have your input JSON file ready):

    # bash

 $snarkjs wtns calculate identity.wasm input.json witness.wtns

Generate the proof:

# bash

    $snarkjs groth16 prove proving_key.json witness.wtns proof.json public.json

4. Verify the Proof

Finally, verify the generated proof:

    Use the verification key to verify the proof:

    # bash

    $snarkjs groth16 verify verification_key.json public.json proof.json

Summary of Commands

    Set Up Keys:

    bash

snarkjs r1cs export json identity.r1cs identity.json
snarkjs groth16 setup identity.r1cs pot12_final.ptau proving_key.json verification_key.json

Calculate the Witness:

bash

snarkjs wtns calculate identity.wasm input.json witness.wtns

Generate the Proof:

bash

snarkjs groth16 prove proving_key.json witness.wtns proof.json public.json

Verify the Proof:

bash

    snarkjs groth16 verify verification_key.json public.json proof.json

Important Note

Ensure that all commands are executed in the directory containing the required files (like identity.r1cs, identity.wasm, and any input JSON files). If you encounter any issues, please share the specific error messages you get, and we can troubleshoot further.


Now that the powers of tau ceremony is complete, you can proceed with the next steps in your zero-knowledge proof setup. Here’s what you should do next:
Next Steps

    Contribute to the Powers of Tau: Use the command to contribute to the initial powers of tau file you generated:

    bash

C:\Users\p'c\AppData\Roaming\npm\snarkjs ptc powersoftau_0000.ptau new_powersoftau.ptau

You've already done this step. Make sure to take note of the output for your records.

Prepare Phase 2 (if applicable): If you're setting up for Phase 2, run the following command:

bash

C:\Users\p'c\AppData\Roaming\npm\snarkjs pt2 new_powersoftau.ptau final_powersoftau.ptau

Setup the Circuit: Once you've generated the final powers of tau file, you can set up your circuit using the r1cs file:

bash

C:\Users\p'c\AppData\Roaming\npm\snarkjs g16s identity.r1cs final_powersoftau.ptau circuit_0000.zkey

Generate Proof: After setting up the circuit, you can generate a proof:

bash

C:\Users\p'c\AppData\Roaming\npm\snarkjs g16p circuit_0000.zkey witness.wtns proof.json public.json

Verify the Proof: Finally, you can verify the generated proof:

bash

    C:\Users\p'c\AppData\Roaming\npm\snarkjs g16v verification_key.json public.json proof.json

Key Points to Remember

    Make sure to follow each step sequentially and check for any errors.
    Take note of the output files generated at each step, as you'll need them for the next commands.
    If you encounter any issues, refer back to the documentation or let me know, and I can help troubleshoot.

Let me know how it goes!

# Next Steps

Now that you have successfully contributed to the powers of tau, you can proceed with the following steps:

    Prepare Phase 2 (if applicable): If you're setting up for Phase 2, run this command:

    bash

C:\Users\p'c\AppData\Roaming\npm\snarkjs pt2 new_powersoftau.ptau final_powersoftau.ptau

Setup the Circuit: Use the r1cs file to set up your circuit. Run:

bash

C:\Users\p'c\AppData\Roaming\npm\snarkjs g16s identity.r1cs final_powersoftau.ptau circuit_0000.zkey

Generate Proof: After setting up the circuit, generate a proof:

bash

C:\Users\p'c\AppData\Roaming\npm\snarkjs g16p circuit_0000.zkey witness.wtns proof.json public.json

Verify the Proof: Finally, verify the generated proof:

bash

    C:\Users\p'c\AppData\Roaming\npm\snarkjs g16v verification_key.json public.json proof.json

Important Notes

    Ensure you follow these commands in order, as each step relies on the output from the previous one.
    If you encounter any errors at any step, please share the error message, and I can assist you with troubleshooting.

Let me know how it goes!

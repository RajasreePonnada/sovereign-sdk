### 1.Polygon CDK files:

    1.state/state.go
    2.txprocessor/processor.go
    3.batch/manager.go
    4.lightclient/client.go
    5.contracts/Identity.sol


### 2.RISC0 files:

    1. zkp/prover.go
    2. zkp/verifier.go
    3. risc0/identity_circuit.rs


3.Avail DA files:

    1.availda/client.go

### Interactions:

    1. state/state.go interacts with:

        txprocessor/processor.go: Provides state access for   transaction processing
        batch/manager.go: Provides state updates for batch commits


    2. txprocessor/processor.go interacts with:

        state/state.go: Reads and writes state
        zkp/verifier.go: Verifies ZK proofs for identity operations
        availda/client.go: Stores transaction data


    3. batch/manager.go interacts with:

        state/state.go: Commits state changes
        availda/client.go: Stores batch data


    4. zkp/prover.go interacts with:

        risc0/identity_circuit.rs: Generates ZK proofs
        availda/client.go: Stores proof data


    5. zkp/verifier.go interacts with:

        risc0/identity_circuit.rs: Verifies ZK proofs


    6. lightclient/client.go interacts with:

        state/state.go: Syncs light client state
        availda/client.go: Retrieves data for verification

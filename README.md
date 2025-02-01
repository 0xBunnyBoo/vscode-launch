{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Init local devnet",
            "type": "go",
            "request": "launch",
            "preLaunchTask": "build",
            "mode": "exec",
            "program": "${workspaceFolder}/build/bin/beacond",
            "args": [
                "init",
                "localtestnet",
                "--chain-id=beacond-2061",
                "--home=${workspaceFolder}/.tmp/beacond",
            ],
            "env": {
                "CHAIN_SPEC": "devnet"
            },
            "internalConsoleOptions": "openOnSessionStart",
            "presentation": {
                "group": "initialize",
                "order": 1
            },
        },
        {
            "name": "Add premined deposit",
            "type": "go",
            "request": "launch",
            "mode": "exec",
            "program": "${workspaceFolder}/build/bin/beacond",
            "preLaunchTask": "build",
            "args": [
                "genesis",
                "add-premined-deposit",
                "32000000000",
                "0x20f33ce90a13a4b5e7697e3544c3083b8f8a51d4",
                "--home=${workspaceFolder}/.tmp/beacond",
            ],
            "env": {
                "CHAIN_SPEC": "devnet"
            },
            "internalConsoleOptions": "openOnSessionStart",
            "presentation": {
                "group": "initialize",
                "order": 2
            },
        },
        {
            "name": "Collect premined deposit",
            "type": "go",
            "request": "launch",
            "preLaunchTask": "build",
            "mode": "exec",
            "program": "${workspaceFolder}/build/bin/beacond",
            "args": [
                "genesis",
                "collect-premined-deposits",
                "--home=${workspaceFolder}/.tmp/beacond",
            ],
            "env": {
                "CHAIN_SPEC": "devnet"
            },
            "internalConsoleOptions": "openOnSessionStart",
            "presentation": {
                "group": "initialize",
                "order": 3
            },
        },
        {
            "name": "Genesis execution payload",
            "type": "go",
            "request": "launch",
            "preLaunchTask": "build",
            "mode": "exec",
            "program": "${workspaceFolder}/build/bin/beacond",
            "args": [
                "genesis",
                "execution-payload",
                "${workspaceFolder}/testing/files/eth-genesis.json",
                "--home=${workspaceFolder}/.tmp/beacond",
            ],
            "env": {
                "CHAIN_SPEC": "devnet"
            },
            "internalConsoleOptions": "openOnSessionStart",
            "presentation": {
                "group": "initialize",
                "order": 4
            },
        },
        {
            "name": "Start beacond",
            "type": "go",
            "request": "launch",
            "preLaunchTask": "build",
            "mode": "exec",
            "program": "${workspaceFolder}/build/bin/beacond",
            "args": [
                "start",
                "--pruning=nothing",
                "--beacon-kit.logger.log-level=info",
                "--home=${workspaceFolder}/.tmp/beacond",
                "--beacon-kit.engine.jwt-secret-path=${workspaceFolder}/testing/files/jwt.hex",
                "--beacon-kit.block-store-service.enabled",
                "--beacon-kit.node-api.enabled",
                "--beacon-kit.node-api.logging",
            ],
            "internalConsoleOptions": "openOnSessionStart",
            "env": {
                "CHAIN_SPEC": "devnet"
            },
            "presentation": {
                "group": "run",
                "order": 1
            },
            "suppressMultipleSessionWarning": true,
        }
    ]
}

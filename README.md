# BNBTCminer
All-in-one mixed multi-GPU (nVidia, AMD, Intel) & CPU miner solves proof of work to mine supported EIP918 tokens in a single instance (with API).

Current latest public release version: [1.1.0](https://github.com/Mineions/BNBTCminer/releases/latest)

Runs on Windows x64

Built with .NET 5.0, VC++ 19.28.29914, nVidia CUDA SDK 10.2 64-bit, and AMD APP SDK v3.0.130.135 (OpenCL)

- .NET Core 5.0 can be downloaded from https://dotnet.microsoft.com/download/dotnet/thank-you/runtime-5.0.5-windows-x64-installer

- VC++ 2019 can be downloaded from https://aka.ms/vs/16/release/vc_redist.x64.exe (https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads)

- CUDA 9.2 requires a minimum nVidia driver version of 396 [https://www.nvidia.com/drivers/beta]

If you are looking for a GUI version, refer to this link [https://github.com/lwYeo/SoliditySHA3MinerUI/releases]

### Releases can be found [here](https://github.com/Mineions/BNBTCminer/releases).


## LICENSE

BNBTCminer is licensed under the [Apache License, Version 2.0 (the "License")](http://www.apache.org/licenses/LICENSE-2.0);

Libraries are included in the Software under the following license terms:
    
    libkeccak-tiny [https://github.com/coruus/keccak-tiny/]
    
    Nethereum [https://github.com/Nethereum/Nethereum/blob/master/LICENSE.md]
    
    Json.NET [https://github.com/JamesNK/Newtonsoft.Json/blob/master/LICENSE.md]
    
    Common Infrastructure Libraries for .NET [http://netcommon.sourceforge.net/license.html]
    
    Bouncy Castle [https://www.bouncycastle.org/licence.html]
    

### Donation addresses

    ETH (or any ERC 20/918 tokens)  : 0x9172ff7884CEFED19327aDaCe9C470eF1796105c
    BTC                             : 3GS5J5hcG6Qcu9xHWGmJaV5ftWLmZuR255
    LTC                             : LbFkAto1qYt8RdTFHL871H4djendcHyCyB
    

Usage: BNBTCminer [OPTIONS]

Options:

    help                    Display this help text and exit

    allowCPU                Allow to use CPU, may slow down system (default: false)

    cpuAffinity             Comma separated list of CPU affinity ID to use (default: all odd number logical processors)

    allowIntel              Allow to use Intel GPU (OpenCL) (default: true)

    allowAMD                Allow to use AMD GPU (OpenCL) (default: true)

    allowCUDA               Allow to use Nvidia GPU (CUDA) (default: true)

    intelIntensity          GPU (Intel OpenCL) intensity (default: 17, decimals allowed)

    listAmdDevices          List of all AMD (OpenCL) devices in this system and exit (device ID: GPU name)

    amdDevice               Comma separated list of AMD (OpenCL) devices to use (default: all devices)

    amdIntensity            GPU (AMD OpenCL) intensity (default: 24.056, decimals allowed)

    listCudaDevices         List of all CUDA devices in this system (device ID: GPU name)

    cudaDevice              Comma separated list of CUDA devices to use (default: all devices)

    cudaIntensity           GPU (CUDA) intensity (default: auto, decimals allowed)

    minerJsonAPI            'http://IP:port/' for the miner JSON-API (default: http://127.0.0.1:4078 [0 disabled])

    minerCcminerAPI         'IP:port' for the ccminer-style API (default: 127.0.0.1:4068 [0 disabled])

    overrideMaxTarget       (Pool only) Use maximum target and skips query from web3

    customDifficulty        (Pool only) Set custom difficulity (check with your pool operator)

    maxScanRetry            Number of retries to scan for new work (default: 3)

    pauseOnFailedScans      Pauses mining after number of connection fails, including secondary and retries (default: 3)

    submitStale             Submit stale jobs, may create more rejected shares (default: false)

    abiFile                 Token abi in a file (default: 'BNBTC.abi' in the same folder as this miner)

    web3api                 User-defined web3 provider URL (default: Infura mainnet provider [dev account, for TESTING PURPOSE only])

    contract                Token contract address (default: 0xbtc contract address)

    hashrateUpdateInterval  Interval (miliseconds) for GPU hashrate logs (default: 30000)

    networkUpdateInterval   Interval (miliseconds) to scan for new work (default: 15000)

    masterMode              Enable Master mode that virtually acts as a \"pool\" for slave miners connecting to it (default: false [requires admin/sudo mode])

    masterURL               Master instance IP:port, slave mode if 'masterMode' is false (default: none [if 'masterMode' is true, default: http://{localIP}:4080/])

    slaveUpdateInterval     (Slave only)Interval (miliseconds) to scan for new work (default: 5000)

    kingAddress             Add MiningKing address to nonce, only CPU mining supported (default: none)

    address                 (Pool only) Miner's ethereum address (default: developer's address)

    privateKey              (Solo only) Miner's private key

    gasToMine               (Solo only) Gas price to mine in GWei (default: 5, decimals allowed; note: will override lower dynamic gas price)

    gasLimit                (Solo only) Gas limit to submit proof of work (default: 1704624))

    gasApiURL               (Solo only) Get dynamic gas price to mine from this JSON API URL (note: leave empty to disable)

    gasApiPath              (Solo only) JSON path expression to retrieve dynamic gas price value from 'gasApiURL'

    gasApiMultiplier        (Solo only) Multiplier to dynamic gas price value from 'gasApiURL' => 'gasApiPath' (note: use 0.1 for EthGasStation API)

    gasApiOffset            (Solo only) Offset to dynamic gas price value from 'gasApiURL' => 'gasApiPath' (after 'gasApiMultiplier', decimals allowed)

    gasApiMax               (Solo only) Maximum gas price to mine in GWei from API (default: 5, decimals allowed)

    pool                    (Pool only) URL of pool mining server (default: http://bnbtcpool.crnx.org:8080)

    secondaryPool           (Optional) URL of failover pool mining server

    logFile                 Enables logging of console output to '{appPath}\\Log\\{yyyy-MM-dd}.log' (default: false)

    devFee                  Set developer fee in percentage (default: 2.0%)


### NOTES

Do refer to [GuideForPoolMining.txt](https://github.com/lwYeo/SoliditySHA3Miner/blob/master/SoliditySHA3Miner/MiningGuide/GuideForPoolMining.txt) on how to get started.

Configuration is based on CLI (similar to ccminer), except ".abi" files are required for new tokens (You can manually create one and copy from etherscan.com -> Contract -> Code -> Contract ABI).

Note that there is a configuration file "SoliditySHA3Miner.conf" that saves previous CLI parameters/settings, delete it prior to changing CLI parameters.

You will have to supply your own Ethereum address (or Private key if you solo mine). It is your own responsibility to mine to the correct address/account.

It is recommended to use your own web3api (e.g. Infura / Geth / Parity) if you solo mine, default value is for TESTING PURPOSE ONLY.

There is a default of 2.0% dev fee (Once every 50th nonce: starting from 11th if Pool mine, or starting from 50th if Solo mine).

(the formula is "(nonce mod (100 / devFee)) = 0").

Dev fee in solo mining is by sending the current reward amount after the successful minted block, using the same gas fee as provided in 'gasToMine'.

In the case if the compute load for your GPU is not >= 99%, you can adjust the intensity via (amdIntensity/cudaIntensity/intelIntensity).

Please feedback your results and suggestions so that I can improve the miner. You can either add an issue in the repository, or find me in discord (Amano7). Thanks for trying out this miner!

### CREDITS

Donations are encouraged to help support further development of this miner!

Many thanks to the following developers and testers in the 0xBitcoin discord :

lwYeo

Azlehria

mining-visualizer

LtTofu/Mag517

Infernal Toast

0x1d00ffff

TwenteMining

Mikers

Ghorge

BRob

Sly

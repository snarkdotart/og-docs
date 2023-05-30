# OG Studio documentation

Welcome to the Developer's Guide to OG Studio

OG Studio provides a comprehensive set of tools designed to foster the creation of dynamic, generative NFT collections. As a developer, you'll find an environment where you can independently experiment with cutting-edge technology, and create NFTs that have the ability to grow, breed, fuse, and react to blockchain or real-life events — even after they've been initially purchased. Here, we offer an early access to these trailblazing tools. This document provides a detailed description of each tool in this powerful toolkit.

## Components of the OG Studio System

1. Blockchain Smart Contract: This is where the magic begins. The blockchain smart contract is responsible for creating events that dictate the behaviour and characteristics of the NFTs. It's the foundational layer of the system, establishing the rules and parameters for your dynamic NFT collection.

2. Event Listener: Acting as an intermediary, the event listener accepts events emanating from the blockchain contract or from an external API interface. This tool is crucial as it acts as a bridge between the smart contract and the other components of the system.

3. Trait Generator: This component is responsible for determining what the NFT will be like. Based on the events accepted by the event listener, the trait generator assigns characteristics and properties to the NFT, creating a unique digital asset each time.

4. Artwork Generator: Connected to the generative scene and render farms, the visuals generator is where your NFTs come to life. It takes the traits assigned by the trait generator and translates them into visual representations, creating an NFT that is not only unique but also aesthetically appealing.

5. Metadata Updater: The final piece of the puzzle, the metadata updater ensures that the metadata of the artwork is updated on the blockchain. It also ensures that this updated information is reflected in the wallets of the owners as well as on various platforms like OpenSea. This continuous updating is what allows your NFTs to be truly dynamic, reflecting changes in real-time.
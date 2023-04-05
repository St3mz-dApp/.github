<p align="center">
  <img src="/profile/images/logo_full.png" title="logo" width="600">
</p>

<p align="center">
  <b>A platform for music NFT's in the Polygon blockchain</b>
</p>

**Live app**: https://st3mz.xyz

**Alternative URL**: https://dark-truth-0166.on.fleek.co

This project consists of three **repositories**:

- [st3mz-contracts](https://github.com/St3mz-dApp/st3mz-contracts): Smart contracts, tests and deployment script.
- [st3mz-client](https://github.com/St3mz-dApp/st3mz-client): UI for interaction with the smart contracts and the back end.
- [st3mz-backend](https://github.com/St3mz-dApp/st3mz-backend): Back end to cache files and data for faster retrieval in the UI.

# 👀 Overview

St3mz is a platform that allows artists to publish their music in the form of NFTs in the Polygon blockchain, so that other users can buy them acquiring also the rights to use the music with different levels of freedom.

Each **NFT** is composed of:

- A main audio track
- Multi-track files (stems) that form the main audio track
- An image artwork
- The metadata related with the audio track

These files are stored in the **Filecoin decentralized storage network** to ensure permanent persistence of the data. This, together with the proof of creation that the multi-track files offer, ensures that an artist can demonstrate that is the rightful creator of the material.

The metadata of the NFT includes a **licenses** property. Here the creator can specify up to three different kinds of licenses and the minimum amount of units a user will require owning to exercise the rights granted by that license. These are the three types of licenses available:

- **Basic**: Does NOT allow commercial use.
- **Commercial**: Allows commercial use. The rights over the material are shared
  with other people.
- **Exclusive**: Exclusive rights over the material with no limitations.

We can see how this works with an example. Let's assume that we have an NFT with a total supply of 10 units and these values in its metadata file:

```json
  "licenses": [
    {
      "type": "Basic",
      "tokensRequired": 1
    },
    {
      "type": "Commercial",
      "tokensRequired": 3
    },
    {
      "type": "Exclusive",
      "tokensRequired": 10
    }
  ]
```

This means that a user that just want to own the audio NFT as a collectible can do so buying just one unit. However, if that user wanted to use the track to create a remix and publish it in their new album, they would require buying three units of the NFT. Finally, if the purpose is to have exclusive rights over the piece so that nobody else can use it with commercial purposes they would require to buy the whole supply.

# 🔧 Technologies used

## Smart contracts

The smart contracts have been written in [Solidity 0.8.17](https://docs.soliditylang.org/en/v0.8.17/) and [Foundry](https://book.getfoundry.sh/) development toolchain has been used for testing and deployment.

## Front end

The front end application has been created with JavaScript's [React](https://reactjs.org/) framework, using the scaffolding project [Create React App](https://create-react-app.dev/) and [Tailwind CSS](https://tailwindcss.com/) framework.

The application is hosted in [IPFS](https://ipfs.tech/) though [Fleek](https://fleek.co/).

## Back end

The back end is a [NodeJS](https://nodejs.org/) application built with [Express.js](https://expressjs.com/).

It is hosted with [AWS's Elastic Beanstalk](https://aws.amazon.com/elasticbeanstalk/) service.

## Database

Object-relational [PostgreSQL](https://www.postgresql.org/) database.

## Storage

The NFT files (audios, image and metadata) are stored in [Filecoin](https://filecoin.io/) and made available over IPFS with the [NFT.Storage](https://nft.storage/) service.

All files are also stored in [AWS's S3](https://aws.amazon.com/s3/) by the back end application, for faster retrieval in the client application.

# 📃 Smart contracts

## St3mz

NFT contract based on the ERC1155 standard, but adapted to be transferable just once (when it is bought). This ensures that the buyer cannot resale the NFT after they have exercised the licensing rights associated with its purchase.

The creator sets the supply and unit price for the token at the moment of minting.

## St3mzUtil

This is a utility contract to perform read-only operations over the St3mz contract.

## Deployments

**St3mz**: [0xd89e04f2ddf5f8212461d27584216f00ab6e96f4](https://polygonscan.com/address/0xd89e04f2ddf5f8212461d27584216f00ab6e96f4#code)

**Util**: [0x2da83a100e25ad3a2ea58967d37f8439a33de4fb](https://polygonscan.com/address/0x2da83a100e25ad3a2ea58967d37f8439a33de4fb#code)

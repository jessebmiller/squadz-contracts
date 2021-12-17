# squadz-contracts
Contracts for Squadz, a shell engine for managing your squad

vision idea for the first specific shell use case cluster: spinning up squads, i.e. adding a formal crypto shell onto an existing, cohesive social group (your group chat, product team, working group, hackathon team, gaming guild, etc.)
- got a group of people that are all into each other and excited about some idea?
- launch an NFT with shell that can come with a bunch of features: 1) cheaply mint for the whole group (batch mint or merkle drop), 2) unique PFP for everyone in your crew (upgrade them later! core shell feature-type beat), 3) comes with a snapshot that looks at the mintedTo address 4) social erc20 that can start vesting to the members right away (HV), 5) mint extra NFTs or ERC20 that can be sold / swapped for capital, 6) fun basic squad website that shows members and their PFPs, 7) NFTs are compatible with Tally / Nouns DAO compound fork if you want to set up a formal DAO later 
the idea being that squads are everywhere in crypto (hackathon projects, grant apps, us, dao working groups, every product team...) and they're super valuable, but they're kind of invisible -- you can use shell to show off your squad and give it infrastructure it needs to grow its reputation / size / etc.! 
imagine every grant application we get they link to their squad page and we can see all the members and any relevant on-chain reputation-type stuff

### Problem
Squads — the groups that actually get work done — are invisible online. Squads do things like:
- Build projects together
- Hang out on group chats
- Go to events together
- Build solidarity around specific ideas

You want to grow your Squad — in members and/or in reputation — but how can you do that when your Squad can’t directly interact with web3?

(More details: you can make a website for your Squad, but websites are archaic: they contain none of your social data, don’t talk to anything, have to be manually updated.)

### Solution
Let people show off their Squad: who the members are, what they’re doing

### User Stories + Implementation
As a squad member, I want to create a new squad
As a squad member, I want to show off my Squad’s vibe
	- custom imagery of some kind
        - Page background?
	- unique name (ENS?)
As a squad member, I want to invite my co-members to the Squad
	- mint /burn NFTs (I.e. join / kick from squad)
            - Possible permissions: mint admin NFTs, burn admin NFTs, mint member NFTs, burn member NFTs, mint fan NFTs, burn fan NFTs
                - Owner — swap engine + all (except burning fan NFTs)
                - Admin NFT holders — all (except burning fan NFTs)
                - Member NFT holders — mint fan NFTs
                - Fan NFT holders — none
                - (Fan NFTs cannot be burned)
As a squad member, I want to show off my Squad’s members
    - cool NFT images
As a squad member, I want to show off my Squad’s accomplishments
    - Maybe not MVP
As a squad member, I want to share my Squad’s information with potential collaborators
	- Unique domain I can link people to, possibly embed
As a squad member, I want to be able to use my membership as a delegatable voting share on snapshot or in a DAO

### Architecture
squadz = engine, is Votes, Ownable

squad = collection using the squadz engine

Create a squad by calling the collection factory with squadz as engine (core squadz ui)

squadz.xyz queries shell subgraph to find and display squads — go to a *.squadz.xyz subdomain, and it will attempt to query for that squad (may not exist)

squad owner can claim one *.squadz.eth subdomain to get a unique name (squadz ui form)

squadz ui links to shell ui for core functions

Mint some admin NFTs to core members (squadz ui)

Admins mint NFTs to other members (squadz ui)

Anyone may mint Fan NFTs (squadz ui)

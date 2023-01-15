<script lang="ts">
    import { onMount } from "svelte";

    type NFT = {
        imageURL: string;
        name: string;
        description: string;
    };

    let nfts: NFT[] = [];
    let nftsPush: NFT[] = [];

    const NFT1 = {
        imageURL: "https://ngmipandas.com/images/special/420.jpg",
        name: "NGMIPandas",
        description: "420 Panda",
    };

    const NFT2 = {
        imageURL: "https://ngmipandas.com/images/special/fast-shitcoiner.jpg",
        name: "NGMIPandas",
        description: "Fast Food Panda",
    };

    const NFT3 = {
        imageURL: "https://ngmipandas.com/images/special/GMI.jpg",
        name: "NGMIPandas",
        description: "Space Panda",
    };

    const NFT4 = {
        imageURL: "https://ngmipandas.com/images/special/ice-cold.jpg",
        name: "NGMIPandas",
        description: "Ice cold Panda",
    };

    nfts = [NFT1, NFT2, NFT3, NFT4];

    let imagesrc = "https://ngmipandas.com/images/special/420.jpg";
    let i = 0;
    let displayName;
    let displayDescription;
    onMount(() => {
        setInterval(() => {
            nftsPush.push({
                imageURL: nfts[i].imageURL,
                name: nfts[i].name,
                description: nfts[i].description,
            });
            if (nftsPush.length <= nfts.length) {
                nftsPush = nftsPush;
            } else {
                return;
            }
        }, 3000);
    });
    function displayImage() {
        // console.log(i);
        displayName = nfts[i].name;
        imagesrc = nfts[i].imageURL;
        displayDescription = nfts[i].description;
        // console.log(nfts[i].imageURL);
        // console.log(nfts.length);
        // console.log(nfts[i].imageURL);
        if (i === nfts.length - 1) {
            i = 0;
        } else {
            i = i + 1;
        }

        setTimeout(displayImage, 3000);
    }
    displayImage();
</script>

<h4>
    {displayName}<br />
    <img src={imagesrc} alt="Pandas" /><br />
    {displayDescription}
</h4>

<div id="pandas">
    
        {#each nftsPush as nft}
        <div>
          
            <br />
            {nft.name}
            <br />
            {nft.description}
            <br>
            <img src={nft.imageURL} alt="pandas"/>
        </div>
    
        
    {/each}
    

</div>

<style>
    img {
        height: 150px;
        width: 150px;
    }

    #pandas {
        display: flex;
        flex-direction: row;
    }
</style>


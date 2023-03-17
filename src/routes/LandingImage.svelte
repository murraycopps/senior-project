<script>
    import LandingImage from '$lib/images/landing-image2.svg';

    export let isTall = true;
</script>

<img 
src={LandingImage} 
alt=""
class="{isTall ? 'tall' : 'short'}"
 />
 
 <div class="{isTall ? 'tall' : 'short'} text-gray-200" >
    <h1 class="{isTall ?"text-5xl" : "text-3xl"} text-center font-bold">The Rise of Super Shoes</h1>
    <h2 class="{isTall ?"text-3xl" : "text-xl"} text-center font-bold">Are They Necessary for Athletes to Compete at the World Stage?</h2>
    </div>
 <style>

    img{
        position: fixed;
        object-fit: cover;
        width: 100vw;
        transform: scaleX(1.1);
        transition: all 0.5s ease-in-out;
        transform-origin: 50% 100%;    
        pointer-events: none;
    }
    div{
        transition: all 0.5s ease-in-out;
        position: fixed;
        display: flex;
        align-items: center;
        position: fixed;
        width: max-content;
        flex-direction: column;
        pointer-events: none;
    }
    img.tall{
        bottom: 15vh;
        min-height: 85vh;
    }
    img.short{
        min-height: 20vh;
        bottom: 80vh;
        transform: scaleX(1.1) scaleY(0.6);
    }

    div.tall{
        gap:4rem;
        top: 35%;
        left: 50%;
        transform: translate(-50%, -50%);

    }
    div.short{
        top: 1rem;
        left: 2rem;
        gap: 2rem;
        max-height: 25vh;
    }

    div > *{
        transition: all 0.5s ease-in-out;
    }
 </style>
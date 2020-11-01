<script>
    import { onMount } from "svelte";
    let Peaks;
    let instance;
    let overview;
    let zoom;
    let audio;
    let controls;
    let peaksControls;
    let zoomIn;
    let zoomOut;
    let playing = false;
    let playPause;
    export let title = "title";
    export let subtitle = "subtitle";
    export let performer = null;
    export let perfLink = null;
    export let file;
    export let buffer;

    function handleZoomIn () {
        instance.zoom.zoomIn();
    }

    function handleZoomOut () {
        instance.zoom.zoomOut();
    }

    function handlePlay () {
        if (playing){
            playing = false;
            instance.player.pause()
        } else {
            playing = true;
            instance.player.play()
        }     
    }

    onMount (async () => {
        try {
            // SSR Compatability
            const module = await import("peaks.js");
            Peaks = module.default;

            // Generate an instance form factory
            instance = Peaks.init({
                containers: {
                    zoomview: zoom,
                    overview: overview
                },
                dataUri: { arraybuffer: buffer },
                mediaElement: audio,
                height: 30,
                segmentStartMarkerColor: '#a0a0a0',
                segmentEndMarkerColor: '#a0a0a0',
                zoomWaveformColor: 'rgba(0, 30, 128, 1.0)',
                overviewWaveformColor: 'rgba(0, 15, 100, 1.0)',
                overviewHighlightColor: 'grey',
                segmentColor: 'rgba(255, 161, 39, 1)',
                playheadColor: 'rgba(0, 0, 0, 1)',
                playheadTextColor: '#aaa',
                showPlayheadTime: false,
                pointMarkerColor: '#FF0000',
                axisGridlineColor: '#ccc',
                axisLabelColor: '#aaa',
                randomizeSegmentColor: true,
            })
        } catch (err) {
            console.error(err);
        }

    });
</script>

<style>
    .audio-box {
        padding-top: 1em;
        padding-bottom: 1em;
    }

    .audio-controls {
        display: flex;
        flex-direction: row;
		flex-wrap: nowrap;
		flex-basis: auto;
        justify-content: center;
    }

    .pp-button {
        width: 5em;
    }

    .title {
        font-size: 13px;
        font-weight:500;
        padding: 0;
    }

    .subtitle {
        font-size: 12px;
        padding: 0;
    }

    .peaks-controls {
        z-index: 100;
    }
</style>

<div class="audio-box">
    <span class="title">{title}</span><br>
    <span class="subtitle">{subtitle}</span>
    {#if performer}
    <br>
    <span class="subtitle">
        <a target="blank" href={perfLink}>{performer}</a>
    </span>    
    {/if}
    <div bind:this={overview} />
    <div bind:this={zoom} />
    <div bind:this={peaksControls} class="peaks-controls">
        <audio bind:this={audio}>
            <source src={file} type="audio/mp3">
            <track kind="captions">
        </audio>
        <div bind:this={controls} class="audio-controls">
            <div>
                <button bind:this={playPause} on:click={handlePlay} class="pp-button">
                    {#if playing}
                        pause
                    {:else}
                        play
                    {/if}
                </button>
                <button bind:this={zoomIn} on:click={handleZoomIn} class="button">zoom in</button>
                <button bind:this={zoomOut} on:click={handleZoomOut} class="button">zoom out</button>
            </div>
        </div>
    </div>
</div>


    
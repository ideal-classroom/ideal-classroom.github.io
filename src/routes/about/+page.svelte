<div class="main">
    <h1>About</h1>

    <p>An Ideal Classroom is a classroom that is structured to reduce the effects of labeling and poor class structure on the performance of children in those classes.</p>
    <p>This particular application takes the results of children, as well as their relative performance compared to their peers, and feeds it through an algorithm, to try and make an accurate judgement as to whether the class structure is getting the most out of the student.</p>
</div>

<svelte:head>
    <title>About | Ideal Classroom</title>
</svelte:head>

<style>
    label, h3 {
        font-size: 18.72px;
        font-weight: 500;
    }

    .grid {
        display: grid;
        grid-template-columns: 200px auto;
        gap: 5px;
    }

    input {
        background-color: #eeeeee;
        outline: none;
        border: none;
        border-radius: 2px;
        padding: 5px 10px;
    }

    button {
        background-color: #2f1832;
        color: #fff;
        outline: none;
        border: none;
        border-radius: 5px;
        margin-top: 24px;
        padding: 10px;
        width: 100%;
        cursor: pointer;
    }

    input::-webkit-outer-spin-button,
    input::-webkit-inner-spin-button {
        -webkit-appearance: none;
        margin: 0;
    }

    input[type=number] {
        -moz-appearance: textfield;
    }
</style>
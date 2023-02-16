<script>
    import SvelteTooltip from 'svelte-tooltip';

    let messages = [
        "Your child may want to consider switching subjects, as they seem to be struggling with this subject.",
        "Your child is under pressure due to the structure of the classes. Maybe consider switching to a smaller class or taking up homeschooling.",
        "Your child seems to be in a good position and their class structure is having little impact on thier marks." 
    ]
    let initial = "";
    let position = "";
    let students = "";
    let message = "";
    let information = "";
    let percentage;
    let valid = false;

    function update() {
        valid = false;

        if (initial != "" && position != "" && students != "") {
            percentage = initial * (Math.E ** ((-0.35 * ((position / students) ** 2)) / 2));
            if (!isNaN(percentage)) {
                if (students >= 30) {
                    message = `Predicted Percentage: ${Math.round(percentage * 100) / 100}%`;
                    valid = true;
                } else {
                    message = `Error`;
                    information = "Algorithm only works with classes of 30 students or more.";
                }
            }
            else {
                message = `Error`;
                information = "Invalid data in one or more inputs";
            }
        } else {
            message = `Error`;
            information = "Please fill in all inputs";
        }

        if (valid) {
            if (initial < 50) {
                information = messages[0]
            } else if (initial - percentage > 6) {
                information = messages[1]
            } else {
                information = messages[2]
            }
        }
    }
</script>

<svelte:head>
    <title>Ideal Classroom</title>
</svelte:head>

<div class="main">
    <h1>Ideal Classroom</h1>
    <div class="grid">
        <label for="percentage">Raw Percentage:</label>
        <input bind:value={initial} id="percentage" type="number">
        <label for="position">Class Position:</label>
        <input bind:value={position} id="position" type="number">
        <label for="students">Number of Students:</label>
        <SvelteTooltip tip="Ensure that number is larger than 30" top color="#ffffff" >
            <input bind:value={students} id="students" type="number">
        </SvelteTooltip>
    </div>

    <button on:click={update}>Update</button>
    <h3>{ message }</h3>
    <p>{ information }</p>
</div>

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
        width: 100%;
    }

    button {
        background-color: #2a1c63;
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
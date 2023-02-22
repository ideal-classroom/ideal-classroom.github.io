<script>
    import SvelteTooltip from 'svelte-tooltip';

    let messages = [
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
                if (students >= 15) {
                    message = `Predicted Percentage: ${Math.round(percentage * 100) / 100}%`;
                    valid = true;
                } else {
                    message = `Error`;
                    information = "Algorithm only works with classes of 15 students or more.";
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
            if (((initial - percentage) / initial) * 100 > 10) {
                information = messages[0]
            } else {
                information = messages[1]
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
        <SvelteTooltip tip="Ensure that number of students is larger than 15" top color="#ffffff" >
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
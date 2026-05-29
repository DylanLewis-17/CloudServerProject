# Websites creation + custom code

The entirity of my website was designed using wordpress, using their themes, and creating the necessary blocks to form my website.
I have 1 section, the arrow recommendations, which is a custom html block, of which the code for is shared below.

## CSS
```
.archery-form input,
.archery-form textarea {
    width: 100%;
    padding: 12px;
    margin-bottom: 15px;
    border: none;
    border-radius: 4px;
}

.archery-button {
    background: #ff9800;
    color: black;
    border: none;
    padding: 12px 20px;
    cursor: pointer;
    font-weight: bold;
    border-radius: 4px;
}

.archery-button:hover {
    background: white;
}
```
## HTML
```
<p>Enter your details for arrow specifications that will best suit your requirements.</p>

<div class="archery-form">

    <form id="archeryForm">

        <input type="number" id="drawLength" placeholder="Draw Length (inches)" required="">

        <input type="number" id="bowWeight" placeholder="Bow Weight (lbs)" required="">

        <button type="submit" class="archery-button">
            Get Recommendation
        </button>

    </form>

    <div id="results" style="margin-top:20px;"></div>

</div>
```
## Javsscript <br>
```
<script>

document.getElementById("archeryForm").addEventListener("submit", function(event) {

    event.preventDefault();

    let drawLength = document.getElementById("drawLength").value;

    let bowWeight = parseInt(document.getElementById("bowWeight").value);

    let arrowRecommendation = "";

    let stiffnessRecommendation = "";

    let stringRecommendation = "";

    // ARROW SPINE RECOMMENDATIONS

    if (bowWeight >= 25 && bowWeight <= 40) {

        arrowRecommendation = "600 – 500 Spine";

        stiffnessRecommendation = "Most Flexible";

        stringRecommendation = "Dacron bow string recommended.";
    }

    else if (bowWeight >= 41 && bowWeight <= 55) {

        arrowRecommendation = "500 – 400 Spine";

        stiffnessRecommendation = "Medium Flexibility";

        stringRecommendation = "Fast Flight string recommended.";
    }

    else if (bowWeight >= 56 && bowWeight <= 70) {

        arrowRecommendation = "400 – 340 Spine";

        stiffnessRecommendation = "Stiff";

        stringRecommendation = "High-performance synthetic string recommended.";
    }

    else if (bowWeight >= 71 && bowWeight <= 85) {

        arrowRecommendation = "340 – 300 Spine";

        stiffnessRecommendation = "Very Stiff";

        stringRecommendation = "Professional synthetic string recommended.";
    }

    else {

        arrowRecommendation = "No recommendation available for this draw weight.";

        stiffnessRecommendation = "N/A";

        stringRecommendation = "N/A";
    }

    document.getElementById("results").innerHTML = `

        <h3>Recommendation Results</h3>

        <p><strong>Draw Length:</strong> ${drawLength} inches</p>

        <p><strong>Bow Weight:</strong> ${bowWeight} lbs</p>

        <br>

        <p><strong>Recommended Arrow Spine:</strong> ${arrowRecommendation}</p>

        <p><strong>Arrow Stiffness:</strong> ${stiffnessRecommendation}</p>

        <p><strong>Bow String Recommendation:</strong> ${stringRecommendation}</p>
    `;
});

</script>
```
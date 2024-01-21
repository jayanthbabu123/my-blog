+++
title = ' HTML and CSS Recipe Card: Assignment 6'
date = 2024-01-21T10:50:43+05:30
draft = true
+++

Create a styled recipe card for a "Simple Omelette" using HTML and CSS, replicating the provided code structure and styling.

  <style>
      .assignment-6 {
        font-family: "Arial", sans-serif;
         padding: 10px 67px 10px 15px;
        padding-top: 15px;
        background: #f1e8e8;
        color: #333;
      }
      .assignment-6 .container {
        max-width: 768px;
        margin: auto;
        padding: 20px;
        background: #fff;
        color: #333;
        border-radius: 19px;
      }
      .assignment-6 .image {
        width: 100%;
        height: auto;
        border-radius: 19px;
      }
      .assignment-6 h1 {
        font-size: 28px;
        text-align: left;
        margin: 20px 0;
      }
      .assignment-6 h2 {
        color: #d7932d;
        font-size: 22px;
        margin: 16px 0;
      }
      .assignment-6 p {
        color: #666;
        line-height: 1.6;
      }

      .assignment-6 li {
        padding: 8px 0;
        color: #666;
      }
      .assignment-6 .time,
      .assignment-6 .ingredients,
      .assignment-6 .instructions,
      .assignment-6 .nutrition {
        background: #fff;
        padding: 15px;
        margin-top: 0;
        padding-top: 9px;
      }
      .assignment-6 .nutrition {
        margin-top: 0px;
      }

      .assignment-6 .time h3 {
        color: #d53f99;
      }

      .assignment-6 .time {
        background-color: #f5f2f2;
        border-radius: 10px;
      }
      .assignment-6 table {
        border-collapse: collapse;
        width: 100%;
      }
      .assignment-6 td {
        border-bottom: 1px solid #e5e5e5;
        padding: 13px;
        padding-left: 30px;
      }

      .assignment-6 ul {
        margin-bottom: 0;
      }
    </style>
<div class="assignment-6">
  <div class="container">
    <img
      src="https://i.postimg.cc/Z5vMmSRv/assignment-burger.jpg"
      alt="Simple Omelette"
      class="image"
    />
    <h1>Simple Omelette Recipe</h1>
    <p>
      An easy and quick dish, perfect for any meal. This classic omelette
      combines beaten eggs cooked to perfection, optionally filled with your
      choice of cheese, vegetables, or meats.
    </p>
  <div class="time">
      <h3>Preparation time</h3>
      <ol>
        <li><strong>Total:</strong> Approximately 10 minutes</li>
        <li><strong>Preparation:</strong> 5 minutes</li>
        <li><strong>Cooking:</strong> 5 minutes</li>
      </ol>
    </div>
 <div class="ingredients">
      <h2>Ingredients</h2>
      <ul>
        <li>2-3 large eggs</li>
        <li>Salt, to taste</li>
        <li>Pepper, to taste</li>
        <li>1 tablespoon of butter or oil</li>
        <li>
          Optional fillings: cheese, diced vegetables, cooked meats, herbs
        </li>
      </ul>
    </div>

<div class="instructions">
      <h2>Instructions</h2>
      <ol>
        <li>Beat the eggs in a bowl...</li>
        <li>Heat the pan over medium heat...</li>
        <li>Cook the omelette until golden brown...</li>
        <li>Add fillings (optional) and fold the omelette...</li>
        <li>Remove from heat and serve immediately...</li>
        <li>Enjoy with additional salt and pepper to taste...</li>
      </ol>
    </div>

<div class="nutrition">
      <h2>Nutrition</h2>
      <p>The table below shows how much of each nutrient is in this recipe.</p>
      <table>
        <tr>
          <td><strong>Calories</strong></td>
          <td>277kcal</td>
        </tr>
        <tr>
          <td><strong>Carbs</strong></td>
          <td>0g</td>
        </tr>
        <tr>
          <td><strong>Protein</strong></td>
          <td>20g</td>
        </tr>
        <tr>
          <td><strong>Fat</strong></td>
          <td>22g</td>
        </tr>
      </table>
    </div>
  </div>
  </div>

### Specifications:

- **Page Background Color:** #f1e8e8
- **Card Background Color:** #ffffff
- **Title Font Size:** 28px
- **Subtitle Font Size:** 22px
- **Body Text Color:** #666666
- **Subtitle Text Color:** #d7932d
- **Preparation Time Background Color:** #f5f2f2
- **Preparation Time Text Color:** #d53f99
- **Image Source:** https://i.postimg.cc/Z5vMmSRv/assignment-burger.jpg
- **Border Radius for Image and Card:** 20px

### Deliverable:

- A .html file containing the markup for the recipe card.
- An accompanying .css file (or `<style>` block in the HTML file) with the styles applied.

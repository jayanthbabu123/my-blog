+++
title = 'Feedback Rating Card: Assignment-7'
date = 2024-01-21T11:32:59+05:30
draft = false
tags = [
    "HTML",
    "HTML 5",
    "HTML Interview",
    "HTML Assignments",
    "CSS Assignments",
    "HTML CSS designs"
]
categories = ['Assignments']
+++

Develop a feedback rating card that enables users to provide a rating from 1 to 5. Your task is to replicate the provided design with precision, focusing on the color scheme, layout, and interactive elements.

<div class="feedback-card">
      <div class="feedback-header">
        <div class="icon">
          <i class="fas fa-star"></i>
        </div>
        <h2>How did we do?</h2>
        <p>
          Please let us know how we did with your support request. All feedback
          is appreciated to help us improve our offering!
        </p>
      </div>
      <div class="ratings">
        <button>1</button>
        <button>2</button>
        <button>3</button>
        <button>4</button>
        <button>5</button>
      </div>
      <button class="submit-btn">SUBMIT</button>
    </div>
<style>
  .feedback-card {
    background-color: #2d3748; /* Lighter blue background */
    border-radius: 15px;
    padding: 20px;
    width: 330px;
    margin: auto;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  }
  .feedback-header .icon {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 50px;
    height: 50px;
    border-radius: 50%;
    background-color: #1f2937;
  }
 .feedback-card .feedback-header i {
    color: #fbbf24; /* Star icon color */
    font-size: 24px;
  }
 .feedback-card .feedback-header h2,
 .feedback-card .feedback-header p {
    color: #ffffff; /* White text */
    margin: 17px 0;
  }
 .feedback-card .feedback-header h2 {
    margin-top: 15px;
  }
.feedback-card .ratings button {
    background-color: #4a5568;
    color: #ffffff;
    border: none;
    border-radius: 50%;
    width: 49px;
    height: 49px;
    margin: 5px;
    cursor: pointer;
    font-size: 16px;
  }
 .feedback-card .submit-btn {
    background-color: #f6ad55; /* Submit button background */
    color: #ffffff; /* Submit button text color */
    border: none;
    border-radius: 5px;
    padding: 10px 15px;
    margin-top: 15px;
    width: 100%;
    cursor: pointer;
    font-size: 16px;
  }
.feedback-card .ratings button:hover,
.feedback-card .submit-btn:hover {
    opacity: 0.8;
  }
</style>

## Resources:

**Font Awesome CDN:** `<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css">`

**Color Codes:**

- **Card Background:** #2d3748
- **Icon Background:** #1f2937
- **Icon Color:** #fbbf24
- **Text Color:** #ffffff
- **Button Background:** #4a5568
- **Submit Button Background:** #f6ad55

**Tasks:**

- Structure the HTML with a feedback-card container, including a header section with a star icon, text asking for feedback, rating buttons, and a submit button.
- Style the card in CSS using the provided color codes, ensuring the star icon from Font Awesome is centered within a circular background.
- Implement hover effects on the buttons to change opacity on user interaction.

**Deliverables**

- A fully functional HTML file named feedback.html.
- A CSS file named styles.css that contains all the styling for your feedback interface.

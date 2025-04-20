# akaike

# Email Shield: PII Protection & Email Classification System

## Overview
Email Shield is an AI-powered web-based application designed to protect sensitive personal information (PII) and accurately classify incoming emails into predefined support categories. This project leverages regular expressions for PII detection and Google's Gemini API for intelligent classification. The platform provides a user-friendly interface for visualizing results and supports real-time email analysis.

## Features
- **PII Detection & Masking**: Identifies personal information like names, emails, phone numbers, Aadhaar, card details, etc., and replaces them with labeled placeholders.
- **Email Classification**: Categorizes emails into one of the four classes: Billing Issues, Technical Support, Account Management, or Other using the Gemini model.
- **Web Interface**: Built with Flask and Tailwind CSS for a responsive and interactive user experience.
- **Logging & Error Handling**: Logs all key events and gracefully handles API and input-related errors.

## Technologies Used
- Python, Flask
- HTML/CSS, Tailwind CSS, JavaScript
- Google Generative AI
- Regular Expressions
- Flask-CORS for API interaction

## Setup Instructions
1. Clone this repository.
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Run the Flask server:
   ```bash
   python app.py
   ```
4. Access the app at: `http://localhost:5000`

## API Endpoint
- `POST /classify`
  - **Request Body**: `{ "email": "<email content>" }`
  - **Response Format**:
    ```json
    {
      "input_email_body": "<original email>",
      "list_of_masked_entities": [
        {
          "position": [start, end],
          "classification": "<PII Type>",
          "entity": "<original value>"
        }
      ],
      "masked_email": "<masked email>",
      "category_of_the_email": "<category>"
    }
    ```

## Project Structure
```
email-shield/
├── app.py
├── templates/
│   └── index.html
├── requirements.txt
├── README.md
```

## Future Enhancements
- Use Transformer-based models for better entity recognition
- Add user login & history of analyzed emails
- Visualize email insights and trends

---

# 📄 2-Page Project Report

## Title: Email Shield – AI-powered Email Classification with PII Protection

### Objective
To create a web-based system that safeguards personally identifiable information in emails and classifies the content into support categories for automated helpdesk management.

### Modules
1. **PII Detection & Masking**: Uses handcrafted regular expressions to identify and label:
   - Names
   - Emails
   - Phone Numbers
   - Dates (DOB)
   - Aadhaar Numbers
   - Credit Card Info (with CVV and expiry)

2. **Classification**: Uses the Gemini API (Google Generative AI) to classify content into:
   - Billing Issues
   - Technical Support
   - Account Management
   - Other

3. **Flask Backend API**:
   - `/classify` accepts raw email content and returns classification along with masked version and metadata.
   - Implements logging and error handling.

4. **Frontend (HTML + Tailwind CSS)**:
   - Email content box
   - Output panels for masked email, category, and detected entities
   - Visualized in steps for better user experience

### Tools and Technologies
- **Languages**: Python, HTML, JS
- **Frameworks**: Flask, TailwindCSS
- **APIs**: Gemini-Pro by Google
- **Security**: CORS, basic regex sanitation

### Architecture Diagram
```
Email Input --> PII Masking --> Classification (Gemini) --> JSON Response --> UI Display
```

### Sample Output
```json
{
  "input_email_body": "Hi, I'm Sasikumar V, my email is ramesh.k@company.com and card 1234 5678 9101 1121...",
  "list_of_masked_entities": [...],
  "masked_email": "Hi, I'm [full_name], my email is [email] and card [credit_debit_no]...",
  "category_of_the_email": "Billing Issues"
}
```

### Conclusion
Email Shield ensures both **privacy protection** and **actionable email routing** using a blend of NLP techniques and AI classification. It improves the productivity and safety of customer support workflows while being easy to deploy and expand.


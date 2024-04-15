# Cognita_A_Truly_Unified_RAG_Framework
Cognita_A_Truly_Unified_RAG_Framework

## Setting Up Cognita_A_Truly_Unified_RAG_Framework Environment

Setup required software
   1. Install python
   2. Install Ollama 

To set up the `Cognita_A_Truly_Unified_RAG_Framework` environment, follow these steps:

Note : Make sure you are in project root directory

0. cd <Project_root_directory>

1. take "Cognita" in your current workspace
   ```bash
   git clone https://github.com/truefoundry/cognita.git
   ```

2. Create a virtual environment using Python's built-in `venv` module:
    ```bash
    python -m venv Cognita_A_Truly_Unified_RAG_Framework
    ```

3. Activate the virtual environment:

    - On Windows:

        ```bash
        Cognita_A_Truly_Unified_RAG_Framework\Scripts\activate
        ```

    - On Unix or MacOS:

        ```bash
        source Cognita_A_Truly_Unified_RAG_Framework/bin/activate
        ```
4. install dependencies
   ```bash
   pip install -r cognita/backend/requirements.txt
   ```
5. copy .env to cognita/backend/
6. Let's ingest our own "knowledge base" into Cognita RAG system, so we can perform QnA on it
   ```bash
   cd cognita 
   python -m local.ingest
   ```
7. Run backend service
(Cognita_A_Truly_Unified_RAG_Framework) ~\PycharmProjects\Cognita_A_Truly_Unified_RAG_Framework\cognita>uvicorn --host 0.0.0.0 --port 8000 backend.server.app:app --reload

8. Test : POST req

 curl -s -X POST "http://localhost:8000/retrievers/example-app/answer" \
     -H "Content-Type: application/json" \
     -d '{
          "collection_name": "creditcard",
          "query": "Explain in detail different categories of credit cards",
          "model_configuration": {
            "name": "ollama/mistral",
            "provider": "ollama",
            "parameters": {
              "temperature": 0.1
            }
          },
          "prompt_template": "Answer the question based only on the following context:\nContext: {context} \nQuestion: {question}",
          "retriever_name": "vectorstore",
          "retriever_config": {
            "search_type": "similarity",
            "search_kwargs": {
              "k": 20
            }
          },
          "stream": false
        }' | jq

9. Response

{
  "answer": " Credit cards can be broadly categorized into several types based on various features and benefits they offer. Here are some common categories of credit cards:\n\n1. **Basic Credit Cards:** These cards have no annual fee, simple reward programs, and limited additional benefits. They are suitable for individuals who make small purchases frequently or those who want to build a good credit history.\n\n2. **Standard Credit Cards:** These cards offer more rewards and benefits than basic cards. They may come with cashback offers, discounts at partner merchants, or reward points that can be redeemed for various benefits. Standard credit cards usually have an annual fee.\n\n3. **Premium Credit Cards:** Premium credit cards offer a wide range of benefits, including higher reward points, exclusive discounts and privileges, airport lounge access, travel insurance, and more. They typically have a high annual fee.\n\n4. **Secured Credit Cards:** Secured credit cards require cardholders to deposit a security deposit, which acts as collateral for the credit limit. These cards are suitable for individuals with poor or no credit history who want to build a good credit score.\n\n5. **Business Credit Cards:** Business credit cards are designed specifically for business owners and entrepreneurs. They offer features like higher credit limits, reward programs tailored to business expenses, expense tracking tools, and more.\n\n6. **Student Credit Cards:** Student credit cards are targeted towards students who may not have a long credit history or a stable income. These cards often come with lower credit limits, no annual fee, and student-specific rewards and benefits.\n\n7. **Gold/Platinum Credit Cards:** Gold or Platinum credit cards offer premium benefits like airport lounge access, travel insurance, higher reward points, and more. They typically have a high annual fee and are suitable for frequent travelers or high net worth individuals.\n\n8. **Diners Club Credit Cards:** Diners Club credit cards offer unique features like cashback rewards, discounts at partner merchants, and exclusive dining privileges. These cards may also come with an annual fee and higher reward points compared to standard credit cards.\n\n9. **Fuel Credit Cards:** Fuel credit cards are designed for individuals who frequently purchase fuel. They offer benefits like fuel discounts, cashback on fuel purchases, and more. Some fuel credit cards may also offer additional benefits like airport lounge access or travel insurance.\n\n10. **Cashback Credit Cards:** Cashback credit cards offer rewards in the form of cashback on certain purchases or transactions. These cards may have a higher annual fee compared to standard credit cards but offer more significant savings for cardholders.\n\nThese categories represent the most common types of credit cards, and each one has its unique features and benefits. It's essential to understand which category best suits your spending habits and lifestyle before applying for a credit card.",
  "docs": [
    {
      "page_content": "# [Marriott bonvoy credit card](https://www.hdfcbank.com/personal/pay/cards/credit-cards/marriott-bonvoy-credit-card)\n## Features\n#### Features\n\\*[Click here](/Personal/Pay/Cards/Credit Card/Credit Card Landing Page/Credit Cards/Co-Brand/Marriott Co-Brand Credit card/Card-Benefit-Terms-Conditions-clean-HDFC-Bank-response.pdf \"/Personal/Pay/Cards/Credit Card/Credit Card Landing Page/Credit Cards/Co-Brand/Marriott Co-Brand Credit card/Card-Benefit-Terms-Conditions-clean-HDFC-Bank-response.pdf\") to view detailed Terms and Conditions\n\\*\\*[Click here](/Personal/Pay/Cards/Credit Card/Credit Card Landing Page/Credit Cards/Co-Brand/Marriott Co-Brand Credit card/Golf-TC-Marriott.pdf \"/Personal/Pay/Cards/Credit Card/Credit Card Landing Page/Credit Cards/Co-Brand/Marriott Co-Brand Credit card/Golf-TC-Marriott.pdf\") to view detailed Terms and Conditions on Golf Lounge access",
      "metadata": {
        "Header4": "Features",
        "Header2": "Features",
        "Header1": "[Marriott bonvoy credit card](https://www.hdfcbank.com/personal/pay/cards/credit-cards/marriott-bonvoy-credit-card)",
        "_data_point_fqn": "localdir::sample-data/creditcards::marriott-bonvoy-credit-card.md",
        "_data_point_hash": "10778",
        "_id": "d80657fefeaa468ab00b4c706b2f7d65",
        "_collection_name": "creditcard"
      },
      "type": "Document"
    },
    {
      "page_content": "# [Diners club black](https://www.hdfcbank.com/personal/pay/cards/credit-cards/diners-club-black)\n## Features\n#### Key Features\nInternational Golf Courses (handicap certificate mandatory), [click here](/Personal/Pay/Cards/Credit Card/Credit Card Landing Page/Credit Cards/Super Premium/Diners Privilege/International Golf.pdf \"/Personal/Pay/Cards/Credit Card/Credit Card Landing Page/Credit Cards/Super Premium/Diners Privilege/International Golf.pdf\")\n[Click here](/Personal/Pay/Cards/Credit Card/Credit Card Landing Page/Credit Cards/Super Premium/Diners Privilege/HDFC_Diners_Website_T_C_v2.pdf \"/Personal/Pay/Cards/Credit Card/Credit Card Landing Page/Credit Cards/Super Premium/Diners Privilege/HDFC_Diners_Website_T_C_v2.pdf\") for detailed T&C and FAQ on the golf program",
      "metadata": {
        "Header4": "Key Features",
        "Header2": "Features",
        "Header1": "[Diners club black](https://www.hdfcbank.com/personal/pay/cards/credit-cards/diners-club-black)",
        "_data_point_fqn": "localdir::sample-data/creditcards::diners-club-black.md",
        "_data_point_hash": "11446",
        "_id": "344534f9bfde41d4a63140ed2c3a413d",
        "_collection_name": "creditcard"
      },
      "type": "Document"
    },
    {
      "page_content": "# [Freedom card new](https://www.hdfcbank.com/personal/pay/cards/credit-cards/freedom-card-new)\n## Features\n#### Additional Features\nAdditional Features\n**Zero lost Card liability :** In the unfortunate event of losing your HDFC Bank Freedom Credit Card, report it immediately to our 24-hour call centre. On reporting the loss immediately, you have zero liability on any fraudulent transactions made on your Credit Card.Â\n**Interest Free Credit Period :** Avail up to 50 days of interest free period on your HDFC Bank Freedom Credit Card from the date of purchase (subject to the submission of the charge by the Merchant).\n**Revolving Credit :** Enjoy Revolving Credit on your HDFC Bank Freedom [Credit Card](https://www.hdfcbank.com/personal/pay/cards/credit-cards \"https://www.hdfcbank.com/personal/pay/cards/credit-cards\") at nominal interest rate. Please refer to the Fees and Charges section for more details.\n**Exclusive Dining Privileges :**â€‹â€‹â€‹â€‹â€‹â€‹â€‹Enjoy amazing dining benefits with Good Food Trail program.",
      "metadata": {
        "Header4": "Additional Features",
        "Header2": "Features",
        "Header1": "[Freedom card new](https://www.hdfcbank.com/personal/pay/cards/credit-cards/freedom-card-new)",
        "_data_point_fqn": "localdir::sample-data/creditcards::freedom-card-new.md",
        "_data_point_hash": "7707",
        "_id": "56952be9e0494d9da5337de5101e3412",
        "_collection_name": "creditcard"
      },
      "type": "Document"
    },
    {
# Ecommerce-
## Description 
This ecommerce is designed for educational purposes and all the contents are just to get the knowledge on how ecommerces work. The platform will be a simple ecommerce about some products with payment methods, categories, users with their dashboards, a shopping cart, etc.

## Technologies
- **Backend**: Django
- **Frontend**: HTML, CSS, Bootstrap
- **Database**: SQLite
- **Payment Gateway**: PayPal

## **Installation**
### **Prerequisites** 
- Python 3.x
- Django 4.x
- SQLite (for local development)
- PayPal API key

### **Installation steps**
1. Clone the repository:
```bash
    git clone https://github.com/226129/Ecommerce-.git
    cd Ecommerce-
```

2. Create a virtual environment and install dependencies: 
```bash
    python -m venv env 
    env/Scripts/activate
    pip install -r requirements.txt
```

3. Set environment variables creating a .env file with your API keys
```python 
    PAYPAL_API_KEY=your-paypal-key
    SECRET_KEY=your-secret-key
    DEBUG=True
```

4. Run migrations and set up the database 
```bash
    python manage.py migrate
```

5. Start the server 
```bash 
    python manage.py runserver 
```
6. Access the platform at (`http://localhost:8000`)


## Contributing 
1. Fork the repository
2. Create a new branch (`git checkout *b feature/new-feature`)
3. Make your changes and commit them (`git commit -m 'Added new features'`)
4. Push your branch (`git push origin feature/new-feature`)
5. Create a pull request.

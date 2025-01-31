
# FlowX SDK - Python

FlowX is a protocol designed to empower developers building financial solutions by offering an efficient, low-cost way to handle cross-border payments using stablecoins. FlowX aims to address real-world issues in African financial systems, such as high remittance costs, limited liquidity, and currency volatility.

This SDK provides an easy-to-use interface for integrating FlowX's cross-border payment protocol into Python applications. It offers seamless interaction with the FlowX network, allowing developers to process stablecoin-based payments efficiently and securely.

---

## Table of Contents

1. [Installation](#installation)
2. [Getting Started](#getting-started)
3. [Usage](#usage)
4. [Authentication](#authentication)
5. [API Endpoints](#api-endpoints)
6. [Error Handling](#error-handling)
7. [Contributing](#contributing)
8. [License](#license)
9. [Support](#support)

---

## Set an account 

First install Flowx as a local command globally on your machine

### Create a virtual environment
```
python -m venv .virtual_env_name
```

### Start the virtual environment
```
source .venv/bin/activate
```
### install the command with pipx
```
pipx install flowx-sdk
```
### If not for the 1st time do 
```
pipx install -f flowx-sdk
```
### After that run the command to initialize the programm
```
flowx init
```
### Login to authenticate your machine
```
flowx login
```
### Or signup 
```
flowx signup
```
### Create token
```
flowx create --token <api-token>
```
## Then you can use the module in your project


## Installation

To install the FlowX SDK, you can use `pip`:

```bash
pip install flowx-sdk
```

Alternatively, you can install the latest development version directly from the GitHub repository:

```bash
pip install git@github.com:georgegoldman/FlowX.git
```

---

## Getting Started

After installing the `flowx-sdk`, you can start integrating FlowX into your Python application. The first step is to import the SDK and set up your API key for authentication.

### Example:

```python
from flowx_sdk.client import Client

# Initialize FlowX client
client = Client(api_key="your-api-key")

client.authenticated #True

# Example: Get supported currencies
currencies = client.get_supported_currencies()
print(currencies)
```

---

## Usage

Here are some common tasks you can accomplish with the `flowx-sdk`:

### 1. **Get Supported Currencies**

To check which currencies FlowX supports for cross-border payments:

```python
currencies = client.get_supported_currencies()
print(currencies)
```

### 2. **Send Cross-Border Payment**

To send a stablecoin-based payment:

```python
payment = client.send_payment(
    sender_wallet="your_sender_wallet_address",
    receiver_wallet="receiver_wallet_address",
    amount="100.00",
    currency="USD"
)
print(payment)
```

### 3. **Check Payment Status**

To check the status of a payment:

```python
status = client.get_payment_status(payment_id="your_payment_id")
print(status)
```

---

## Authentication

The FlowX SDK requires an API key for authentication. You can obtain your API key by registering on the FlowX platform.

To authenticate, simply pass your API key when initializing the `Client` object:

```python
client = flowx.Client(api_key="your_api_key")
```

For security purposes, it is recommended to keep your API key in an environment variable or a configuration file rather than hardcoding it directly into your scripts.

---

## API Endpoints

The SDK interacts with FlowX's API endpoints. Below are some key endpoints:

### 1. **GET /supported_currencies**
   - ### Supported Currencies

        1. **Stablecoins**
            - **USDT** (Tether)
            - **USDC** (USD Coin)
            - **DAI** (MakerDAO’s decentralized stablecoin)
            - **BUSD** (Binance USD)
            - **EUROC** (Circle's Euro-backed stablecoin)

        2. **Local African Currencies (For Real-World** Integration)
            - **NGN** (Nigerian Naira)
            - **KES** (Kenyan Shilling)
            - **ZAR** (South African Rand)
            - **GHS** (Ghanaian Cedi)
            - **TZS** (Tanzanian Shilling)
            - **UGX** (Ugandan Shilling)

        3. **Global Reserve Currencies**
            - **USD** (US Dollar)
            - **EUR** (Euro)
            - **GBP** (British Pound)

        4. **Cryptocurrencies for Liquidity Bridging**
            - **SUI** (Sui)
            - **BTC** (Bitcoin)
            - **ETH** (Ethereum)
            - **XRP** (Ripple)



### 2. **POST /send_payment**
   - Initiates a cross-border payment from one wallet to another.
   - Parameters: `sender_wallet`, `receiver_wallet`, `amount`, `currency`

### 3. **GET /payment_status/{payment_id}**
   - Retrieves the status of a previously initiated payment.
   - Parameters: `payment_id`

---

## Error Handling

The SDK raises exceptions for various error conditions. Common exceptions include:

- `flowx.exceptions.AuthenticationError`: If the API key is invalid or missing.
- `flowx.exceptions.PaymentError`: If the payment cannot be processed due to insufficient funds, invalid wallet address, or other reasons.
- `flowx.exceptions.NetworkError`: If there is a network issue when contacting FlowX servers.

You can handle errors using standard `try` and `except` blocks:

```python
try:
    payment = client.send_payment(
        sender_wallet="your_sender_wallet_address",
        receiver_wallet="receiver_wallet_address",
        amount="100.00",
        currency="USD"
    )
    print(payment)
except flowx.exceptions.PaymentError as e:
    print(f"Payment failed: {e}")
except flowx.exceptions.NetworkError as e:
    print(f"Network error: {e}")
```

---

## Contributing

We welcome contributions to the `flowx-sdk`. To contribute:

1. Fork the repository on GitHub.
2. Create a new branch for your feature or bugfix.
3. Make your changes and commit them with descriptive messages.
4. Push your changes and create a pull request.

Please ensure that you write tests for any new features or fixes you add.

---

## License

The FlowX SDK is released under the [MIT License](LICENSE).

---

## Support

If you have any issues or need further assistance, please reach out to our support team at [support@flowx.com](mailto:support@flowx.com) or check our documentation and FAQ on [FlowX Documentation](https://flowx.com/docs).

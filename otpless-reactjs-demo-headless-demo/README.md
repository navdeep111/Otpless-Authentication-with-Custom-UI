[![OTPless](https://d1j61bbz9a40n6.cloudfront.net/website/home/v4/logo/white_logo.svg)](https://otpless.com/)

# React-JS Demo: Otpless Headless SDK

## Steps to add OTPless Headless SDK to your ReactJS Website

1. **Create an App in [OTPless dashboard](https://otpless.com/dashboard/app) and copy the `APP ID`**
2. **Add OTPLESS Script as a function**

    > Add the contents of [initOtpless.js](./src/utils/initOtpless.js) file in `src/utils/initOtpless.js` file in your project and *paste* the `APP ID` [here](./src/utils/initOtpless.js#L13).

    **initOtpless.js file exports the following functions**

    >> ***[initOTPless](./src/utils/initOtpless.js#L26)***, to initialize the OTPless SDK,

    >> ***[Authenticate](./src/utils/initOtpless.js#L45)***, to authenticate the user.

    >> ***[verifyOTP](./src/utils/initOtpless.js#L94)***, to verify the OTP.



3. **Load the script in Login/Signup component and add callback function**

    > Add following code in Login/Signup component.
    >> retrive data using **otplessUser** object

    ```jsx
    useEffect(() => initOTPless(handleUserData), []);

    const handleUserData = (otplessUser) => {
        alert(JSON.stringify(otplessUser));
    };
    ```

    [view source](./src/pages/Home.jsx#L10)

4. **Create your UI**

    > Design UI to collect user input and trigger authentication method of your choice.

    ```jsx
    const [phone, setPhone] = useState(null)
	const [otp, setOtp] = useState(null)
    return <>
        <div id="mobile-section">
            <input id='mobile-input' placeholder='Enter mobile number' onChange={(e) => setPhone(e.target.value)} />
            <button onClick={() => Authenticate({ channel: 'PHONE', phone })}>Request OTP</button>
        </div>

        <div id="otp-section">
            <input id='otp-input' placeholder='Enter OTP' onChange={(e) => setOtp(e.target.value)} minLength={6} maxLength={6} />
            <button onClick={() => verifyOTP({ channel: activeSection, otp, phone })}>Verify OTP</button>
        </div>

        <button onClick={() => Authenticate({channel: 'OAUTH', channelType:'WHATSAPP' })}>Authenticate with WhatsApp</button>
        <button onClick={() => Authenticate({channel: 'OAUTH', channelType:'GOOGLE'})}>Authenticate with Gmail</button>
    </>
    ```
    [view source](./src/pages/Home.jsx#L36)  (NOTE: This integration has a different ui)

### This demo implementation adds extra modularity, scalability and reusability to the OTPless Headless sdk

### Usage

> **Prerequisites**: [NodeJS](https://nodejs.org/en)

- Install Packages

    ```bash
    npm install
    ```

- Run the demo

    ```bash
    npm run dev
    ```

- Open [localhost:5173](http://localhost:5173) in your browser
- Switch branches to check out available options to integrate *OTPless* in your project

### ***Note: Enable your choosen Authentication Method from [OTPless dashboard](https://otpless.com/dashboard/customer/channels) before using it.***

## *Thank You*

## [Visit OTPless](https://otpless.com/platforms/react)

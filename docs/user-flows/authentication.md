## SoCon Authentication

SoCon introduces a novel approach to message signing by creating a separate signer public-private key pair. This method enhances security and privacy by eliminating the need to use the sender's private key for signing messages.
When a user logs into any messaging app built on the SoCon platform, the app generates a unique SCID and SCName for the user. Simultaneously, a new signer is created on the App Layer, serving as a cryptographic key pair securely stored locally on the user's device. This signer signs messages on behalf of the user, ensuring secure authentication without compromising the user's custody address's private key.

## Role of web3auth in Socon auth

the login and signup process is seamlessly handled through Web3Auth, a user-friendly authentication method. Web3Auth simplifies the authentication experience for users by abstracting the complexities of key handling, offering a hassle-free and secure login mechanism. Users can enjoy a seamless authentication journey without needing to worry about managing cryptographic keys, ensuring a smooth and intuitive user experience.
After initiating the social login via email, users are directed through the Web3Auth process for authentication. An OTP (One-Time Password) is sent to the user's registered email address for verification purposes. Users receive the OTP in their email inbox, which they must enter into the application to successfully complete the verification process.
By combining the convenience of Web3Auth for seamless login and signup processes with the added security of OTP verification via email, our application aims to provide users with both a user-friendly experience and robust identity authentication, enhancing overall security and trust in our platform.

![Authentication Flow](/assets/authentication-flow.png)

Upon a successful login through Web3Auth, users receive their detailed account information and the creation of a wallet specific to their account. Web3Auth facilitates a streamlined login process, ensuring users' authentication details are securely managed without burdening them with cryptographic complexities. As users complete the authentication process, a wallet associated with their account is automatically generated.
In addition to providing user details and creating the wallet, Web3Auth returns an ID token. This token serves as a form of identification and verification, encapsulating essential user information. The ID token acts as a secure credential, allowing the backend system to verify the legitimacy of users during registration or subsequent interactions.
The payload received post-verification includes vital information such as the wallet's public address and the user's email along with other necessary details. Upon receipt, the system checks if the email is whitelisted, indicating that the user has been invited to use the app by another user.
Next, utilizing the received public key of the wallet, the system computes the wallet address. This calculated wallet address is then registered on Socon's smart contract, enabling seamless integration and authentication within the platform's ecosystem.
This process ensures that verified users with whitelisted emails and associated wallet information are securely onboarded and integrated into Socon's network, fostering a trusted and connected community within the platform.
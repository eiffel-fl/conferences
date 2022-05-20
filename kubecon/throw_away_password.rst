Throw Away Your Passwords: Trusting Workload Identity
-----------------------------------------------------

Instead of using password, we will use identity.
A identity party can give you information about a subject.
You should not use long lived service account tokens by bounding their lifetime and audience.

A JSON Web Token (JWT) is composed of the following:

1. A header.
2. A payload.
3. A signature.

Using the token to identify your workload is actually in preview on Azure but is already available for others coud providers like AWS.
You can also use Open Policy Agent to enforce using token.
GitHub can also provide you identity token instead of k8s.

SPIFFE is the specification of the identity while SPIRE is the corresponding runtime.
SPIRE can be used with a TPM.

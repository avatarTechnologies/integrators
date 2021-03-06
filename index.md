## Avatar ERA (Electronic Revenue Assurance) Solution: Integration scenarios
1. Introduction
1. Definitions and official documentation
1. [SAM](https://en.wikipedia.org/wiki/Secure_access_module) Card devices
1. V-SDC devices

## Introduction
Avatar ERA helps Tax Authorities fiscalize sale transactions by providing the infrastructure that validates purchase receipts. Merchants are required to use POS devices compatible with Avatar but are free to buy them from any vendor they choose. This documentation let vendors understand their options to produce these devices.
## Definitions and official documentation
**CIS (Certified Invoice System):** Any invoicing device approved by the Tax Authority

**SE (Secure Element):** A device or software issued by the Tax Authority with the cryptographic and processing capabilities required to validate receipts and audit sale transactions. The most salient features of the SE are:
* It makes it possible for every device to identify itself using Avatar's [PKI](https://en.wikipedia.org/wiki/Public_key_infrastructure)
* It is able to sign invoices 
* It keeps several inner records to ensure the device can be audited at will by the Tax Authority

**SDC (Sales Data Controller):** Secure system that verifies the format of the invoices generated by a CIS and communicates with Avatar server to fiscalize the transactions. There are three kinds of SDC, internal (I-SDC, found in CIS's with their own SE), external (E-SDC, a device with a SE that connects to a CIS to make it Avatar compatible) and virtual (V-SDC, a cloud based platform that hold SE's for registered devices that support this type of SDC)
* **I-SDC:** A [POS](https://en.wikipedia.org/wiki/Point_of_sale) / CIS (it can be a device or an application) able to communicate with its own SE (a SAM card) through the [APDU API](https://github.com/avatarTechnologies/integrators/blob/master/Avatar_APDU_v1_5.pdf).
* **E-SDC:** A device with its own SE (a SAM card) that offers an API to make any CIS Avatar compatible. There are no restrictions regarding CIS / E-SDC communication, as long as the E-SDC ensures the device is properly fiscalized by Avatar, which sees the E-SDC as another I-SDC.
* **V-SDC:** Those integrators not willing to deal directly with the SE may use the V-SDC to have the invoiced produced by their POS / CIS fiscalized by Avatar. Instead of a SAM card, V-SDC devices must have a certificate issued by Avatar's [CA](https://en.wikipedia.org/wiki/Certificate_authority) and send the invoices to the V-SDC for fiscalization before issuing them to the end customers.

**Official documentation:** 
* [APDU API](https://github.com/avatarTechnologies/integrators/blob/master/Avatar_APDU_v1_5.pdf)
* [Avatar API](https://github.com/avatarTechnologies/integrators/blob/master/AVATARAPIDOCUMENTATION.pdf)

**POA (Proof of Audit):** In order to ensure that all invoices are signed and submitted to Avatar, all SAM Card devices must perform a POA (Proof of Audit) process periodically, at least before a configurable limit on the amount of sales that can be "signed" to Avatar is reached, the SAM card is locked and it is no longer possible to sign more invoices until a POA is successfully performed. 

**Invoice Verification:** Approved CIS must produce a printed version of invoices with a QR code containing a verification URL for the invoice. End customers can verify the invoice is valid by accessing that URL

## SAM Card devices
Those integrators planning to develop an I-SDC or E-SDC device should register as Avatar Integrator and request SAM cards preconfigured for an Avatar sandbox environment. Please do it [here](http://integrators.avatar-technologies.com/)


## V-SDC devices
Those integrators planning to develop an I-SDC or E-SDC device should register as Avatar Integrator and request a certificates preconfigured for an Avatar sandbox environment. Please do it [here.](http://integrators.avatar-technologies.com)

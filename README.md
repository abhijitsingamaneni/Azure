# Azure

## Steps to create a Service Principle in AZURE 

### Step:1 Installing Azure CLI

Use the az --version command to verify you have installed Azure CLI v0.10.5 or higher.

```az --version```

If you don't have azure cli installed on your machine got to this link(https://docs.microsoft.com/en-us/cli/azure/install-azure-cli-macos?view=azure-cli-latest) and follow the steps for installation.

### Step:2 Set Your Default Subscription
1.Run az account list to get the list of subscriptions.

 ```az account list```

#### Out put


 ``` 
[
  {
    "cloudName": "AzureCloud",
    "id": "xxx-xxx-xx-xx-xxxx",
    "isDefault": false,
    "name": "Free Trial",
    "state": "Enabled",
    "tenantId": "xxx-xxx-xx-xx-xxxx",
    "user": {
      "name": "xxxxxx.xxxxx@xxxxxxxx.com",
      "type": "user"
      
    }
  },
  {
    "cloudName": "AzureCloud",
    "id": "xxx-xxx-xx-xx-xxxx",
    "isDefault": true,
    "name": "Free Trial",
    "state": "Enabled",
    "tenantId": "xxx-xxx-xx-xx-xxxx",
    "user": {
      "name": "xxx-xxx-xx-xx-xxxx",
      "type": "servicePrincipal"
    }
  }
]
 ```
2.Finding the default subscription using `isDefault` = True

3.Change the default subscription using 

 ``` az account set $Subscription_ID```

4.Record the `tenantID` for future use

### Step 3: Create an Azure Active Directory (AAD) Application

1.Run the following commant to create AAD Application.

```az ad app create --display-name "BOSH" --password "PASSWORD" --homepage "http://BOSHAzureCPI" --identifier-uris "http://BOSHAzureCPI"```

#### Output

```
{
  "acceptMappedClaims": null,
  "addIns": [],
  "appId": "xxxxxx-xxxxxx-xxxxxxx-xxxxxx",
  "appPermissions": null,
  "appRoles": [],
  "availableToOtherTenants": false,
  "deletionTimestamp": null,
  "displayName": "xxxxxxx",
  "errorUrl": null,
  "groupMembershipClaims": null,
  "homepage": "http://BOSHAzureCPI",
  "identifierUris": [
    "http://BOSHAzureCPI"
  ],
  "informationalUrls": {
    "marketing": null,
    "privacy": null,
    "support": null,
    "termsOfService": null
  },
  "isDeviceOnlyAuthSupported": null,
  "keyCredentials": [],
  "knownClientApplications": [],
  "logo@odata.mediaContentType": "axxxxxxxxxx",
  "logoUrl": null,
  "logoutUrl": null,
  "oauth2AllowIdTokenImplicitFlow": true,
  "oauth2AllowImplicitFlow": false,
  "oauth2AllowUrlPathMatching": false,
  "oauth2Permissions": [
    {
      "adminConsentDescription": "xxxxxx",
      "adminConsentDisplayName": "xxxxxx",
      "id": "xxxxxx-xxxx-xxxx--xxxxx",
      "isEnabled": true,
      "type": "User",
      "userConsentDescription": "xxxx",
      "userConsentDisplayName": "xxxxxx",
      "value": "user_impersonation"
    }
  ],
  "oauth2RequirePostResponse": false,
  "objectId": "xxxxx-xxxxx-xxxxx-xxxx",
  "objectType": "Application",
  "odata.metadata": "xxx",
  "odata.type": "xxxxx",
  "optionalClaims": null,
  "orgRestrictions": [],
  "parentalControlSettings": {
    "countriesBlockedForMinors": [],
    "legalAgeGroupRule": "Allow"
  },
  "passwordCredentials": [
    {
      "customKeyIdentifier": null,
      "endDate": "2019-10-28T01:38:27.570691Z",
      "keyId": "xx-xxxxx-xxxxxx-xxx",
      "startDate": "2018-10-28T01:38:27.570691Z",
      "value": null
    }
  ],
  "publicClient": null,
  "publisherDomain": null,
  "recordConsentConditions": null,
  "replyUrls": [],
  "requiredResourceAccess": [],
  "samlMetadataUrl": null,
  "signInAudience": "AzureADMyOrg",
  "tokenEncryptionKeyId": null
}
```

2.Record the `appId` for future use

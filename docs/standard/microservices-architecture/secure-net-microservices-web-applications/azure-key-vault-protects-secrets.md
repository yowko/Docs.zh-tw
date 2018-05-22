---
title: 使用 Azure Key Vault 以在生產階段保護密碼
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 使用 Azure Key Vault 以在生產階段保護密碼
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 5ad5686909c29eba5916cbcc4b7115a16108a004
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="using-azure-key-vault-to-protect-secrets-at-production-time"></a>使用 Azure Key Vault 以在生產階段保護密碼

儲存為環境變數或由密碼管理員工具所儲存的密碼仍然會儲存在本機，而且在電腦上未加密。 儲存密碼的更安全選項是 [Azure Key Vault](https://azure.microsoft.com/services/key-vault/)，以提供安全且集中的位置來儲存金鑰和密碼。

Microsoft.Extensions.Configuration.AzureKeyVault 套件允許 ASP.NET Core 應用程式從 Azure Key Vault 中讀取組態資訊。 若要開始使用 Azure Key Vault 中的密碼，您可以遵循下列步驟：

首先，將應用程式註冊為 Azure AD 應用程式  (對金鑰保存庫的存取是由 Azure AD 所管理)。這可以透過 Azure 管理入口網站完成。

或者，如果您想要應用程式使用憑證進行驗證，而不是使用密碼或用戶端密碼，則可以使用 [New-AzureRmADApplication](https://docs.microsoft.com/powershell/resourcemanager/azurerm.resources/v3.3.0/new-azurermadapplication) PowerShell Cmdlet。 您向 Azure Key Vault 註冊的憑證只需要公開金鑰  (您的應用程式將會使用私密金鑰)。

第二，建立新的服務主體，以提供已註冊應用程式對金鑰保存庫的存取。 您可以使用下列 PowerShell 命令執行這項作業：

```powershell
$sp = New-AzureRmADServicePrincipal -ApplicationId "<Application ID guid>"
Set-AzureRmKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
```

第三，在建立 IConfigurationRoot 執行個體時呼叫 IConfigurationBuilder.AddAzureKeyVault 擴充方法，以包含金鑰保存庫作為應用程式中的組態來源。 請注意，呼叫 AddAzureKeyVault 時需要已註冊並提供先前步驟中金鑰保存庫存取權的應用程式識別碼。

  目前，.NET Standard 和 .NET Core 支援使用用戶端識別碼和用戶端密碼，以從 Azure Key Vault 取得組態資訊。 .NET Framework 應用程式可以使用採用憑證來取代用戶端密碼的 IConfigurationBuilder.AddAzureKeyVault 多載。 從這項撰寫開始，工作[正在進行](https://github.com/aspnet/Configuration/issues/605)，讓該多載可在 .NET Standard 和 .NET Core 中使用。 除非接受憑證的 AddAzureKeyVault 多載可用，否則 ASP.NET Core 應用程式可以明確建立 KeyVaultClient 物件，以使用憑證型驗證來存取 Azure Key Vault，如下列範例所示：

```csharp
// Configure Key Vault client
var kvClient = new KeyVaultClient(new KeyVaultClient.AuthenticationCallback(async
    (authority, resource, scope) =>
    {
        var cert = // Get certificate from local store/file/key vault etc. as needed
        // From the Microsoft.IdentityModel.Clients.ActiveDirectory pacakge
        var authContext = new AuthenticationContext(authority,
            TokenCache.DefaultShared);
        var result = await authContext.AcquireTokenAsync(resource,
            // From the Microsoft.Rest.ClientRuntime.Azure.Authentication pacakge
            new ClientAssertionCertificate("{Application ID}", cert));
        return result.AccessToken;
    }));

    // Get configuration values from Key Vault
    var builder = new ConfigurationBuilder()
        .SetBasePath(env.ContentRootPath)
        // Other configuration providers go here.
        .AddAzureKeyVault("{KeyValueUri}", kvClient,
        new DefaultKeyVaultSecretManager());
```

在此範例中，AddAzureKeyVault 呼叫是在組態提供者登錄的結尾。 最好將 Azure Key Vault 註冊為最後一個組態提供者，讓它可以覆寫先前提供者中的組態值，因此其他來源中的組態值不會覆寫金鑰保存庫中的組態值。

## <a name="additional-resources"></a>其他資源

-   **使用 Azure Key Vault 來保護應用程式祕密**
    [*https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault*](https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault)

-   **在開發期間安全儲存應用程式祕密**
    [*https://docs.microsoft.com/aspnet/core/security/app-secrets*](https://docs.microsoft.com/aspnet/core/security/app-secrets)

-   **設定資料保護**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview)

-   **金鑰管理和存留期**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings\#data-protection-default-settings*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings#data-protection-default-settings)

-   **Microsoft.Extensions.Configuration.DockerSecrets.** GitHub 存放庫。
    [*https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets*](https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets)

>[!div class="step-by-step"]
[上一個] (developer-app-secrets-storage.md) [下一個] (../key-takeaways.md)

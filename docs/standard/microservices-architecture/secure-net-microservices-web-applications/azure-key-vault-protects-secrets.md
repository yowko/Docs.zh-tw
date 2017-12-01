---
title: "在實際執行階段保護機密資訊使用 Azure 金鑰保存庫"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |在實際執行階段保護機密資訊使用 Azure 金鑰保存庫"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 7f922997e8d0c63e206cd68f4efda14985c86b72
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="using-azure-key-vault-to-protect-secrets-at-production-time"></a>在實際執行階段保護機密資訊使用 Azure 金鑰保存庫

密碼儲存為環境變數，或儲存的密碼管理員工具仍會儲存在本機，並在電腦上未加密。 儲存機密資料的更安全選項是[Azure 金鑰保存庫](https://azure.microsoft.com/services/key-vault/)，這樣會提供安全的中央位置來儲存金鑰和密碼。

Microsoft.Extensions.Configuration.AzureKeyVault 封裝可讓 ASP.NET Core 應用程式來讀取 Azure 金鑰保存庫中的組態資訊。 若要開始使用 Azure 金鑰保存庫中的機密資料，您可以依照下列步驟：

首先，為 Azure AD 應用程式註冊您的應用程式。 （金鑰保存庫的存取是由 Azure AD 管理）。這可以透過 Azure 管理入口網站。

或者，如果您希望應用程式使用憑證，而不密碼或用戶端密碼進行驗證，您可以使用[新增 AzureRmADApplication](https://docs.microsoft.com/powershell/resourcemanager/azurerm.resources/v3.3.0/new-azurermadapplication) PowerShell cmdlet。 Azure 金鑰保存庫中註冊的憑證必須只有您的公開金鑰。 （您的應用程式會使用私密金鑰）。

第二，提供已註冊的應用程式的存取金鑰保存庫，藉由建立新的服務主體。 您可以使用下列 PowerShell 命令：

```powershell
$sp = New-AzureRmADServicePrincipal -ApplicationId "<Application ID guid>"
Set-AzureRmKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
```

第三，包含金鑰保存庫做為組態中的來源應用程式藉由呼叫 IConfigurationBuilder.AddAzureKeyVault 擴充方法，當您建立 IConfigurationRoot 執行個體。 請注意，呼叫 AddAzureKeyVault 將需要已註冊並提供存取金鑰保存庫在先前步驟中的應用程式識別碼。

  目前，標準.NET 和.NET Core 支援取得組態資訊從 Azure 金鑰保存庫使用用戶端識別碼和用戶端密碼。 .NET framework 應用程式可以使用 IConfigurationBuilder.AddAzureKeyVault 採用的憑證來取代用戶端密碼的多載。 工作是在撰寫本文[正在](https://github.com/aspnet/Configuration/issues/605)將該多載提供的標準.NET 和.NET 核心。 接受憑證可用於 AddAzureKeyVault 多載中，直到 ASP.NET Core 應用程式可以存取 Azure 金鑰保存庫憑證為基礎的驗證與明確建立 KeyVaultClient 物件，如下列範例所示：

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

在此範例中，AddAzureKeyVault 呼叫是在組態提供者登錄的結尾。 它是 Azure 金鑰保存庫註冊為最後的組態提供者，使其具有可以覆寫組態值，從上一個提供者，以及任何其他來源的組態值會覆寫從金鑰保存庫的最佳作法。

## <a name="additional-resources"></a>其他資源

-   **使用 Azure 金鑰保存庫保護應用程式密碼**
    [*https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault*](https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault)

-   **在開發期間的應用程式密碼的安全存放**
    [*https://docs.microsoft.com/aspnet/core/security/app-secrets*](https://docs.microsoft.com/aspnet/core/security/app-secrets)

-   **設定資料保護**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview)

-   **金鑰管理和存留期**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings\#資料保護的預設設定*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings#data-protection-default-settings)

-   **Microsoft.Extensions.Configuration.DockerSecrets。** GitHub 儲存機制。
    [*https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets*](https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets)

>[!div class="step-by-step"]
[上一個](開發人員為應用程式-機密-storage.md) [下一步] (.../ 索引鍵 takeaways.md）

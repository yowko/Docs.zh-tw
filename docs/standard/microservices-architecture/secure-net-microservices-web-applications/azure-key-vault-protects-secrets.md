---
title: 使用 Azure Key Vault 以在生產階段保護密碼
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 使用 Azure Key Vault 以在生產階段保護密碼
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 171d9120e4817065ddafc9dfa9caa362694ddeb3
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105280"
---
# <a name="using-azure-key-vault-to-protect-secrets-at-production-time"></a><span data-ttu-id="fef8d-103">使用 Azure Key Vault 以在生產階段保護密碼</span><span class="sxs-lookup"><span data-stu-id="fef8d-103">Using Azure Key Vault to protect secrets at production time</span></span>

<span data-ttu-id="fef8d-104">儲存為環境變數或由密碼管理員工具所儲存的密碼仍然會儲存在本機，而且在電腦上未加密。</span><span class="sxs-lookup"><span data-stu-id="fef8d-104">Secrets stored as environment variables or stored by the Secret Manager tool are still stored locally and unencrypted on the machine.</span></span> <span data-ttu-id="fef8d-105">儲存密碼的更安全選項是 [Azure Key Vault](https://azure.microsoft.com/services/key-vault/)，以提供安全且集中的位置來儲存金鑰和密碼。</span><span class="sxs-lookup"><span data-stu-id="fef8d-105">A more secure option for storing secrets is [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), which provides a secure, central location for storing keys and secrets.</span></span>

<span data-ttu-id="fef8d-106">Microsoft.Extensions.Configuration.AzureKeyVault 套件允許 ASP.NET Core 應用程式從 Azure Key Vault 中讀取組態資訊。</span><span class="sxs-lookup"><span data-stu-id="fef8d-106">The Microsoft.Extensions.Configuration.AzureKeyVault package allows an ASP.NET Core application to read configuration information from Azure Key Vault.</span></span> <span data-ttu-id="fef8d-107">若要開始使用 Azure Key Vault 中的密碼，您可以遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="fef8d-107">To start using secrets from an Azure Key Vault, you follow these steps:</span></span>

<span data-ttu-id="fef8d-108">首先，將應用程式註冊為 Azure AD 應用程式 </span><span class="sxs-lookup"><span data-stu-id="fef8d-108">First, register your application as an Azure AD application.</span></span> <span data-ttu-id="fef8d-109">(對金鑰保存庫的存取是由 Azure AD 所管理)。這可以透過 Azure 管理入口網站完成。</span><span class="sxs-lookup"><span data-stu-id="fef8d-109">(Access to key vaults is managed by Azure AD.) This can be done through the Azure management portal.</span></span>

<span data-ttu-id="fef8d-110">或者，如果您想要應用程式使用憑證進行驗證，而不是使用密碼或用戶端密碼，則可以使用 [New-AzureRmADApplication](https://docs.microsoft.com/powershell/resourcemanager/azurerm.resources/v3.3.0/new-azurermadapplication) PowerShell Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fef8d-110">Alternatively, if you want your application to authenticate using a certificate instead of a password or client secret, you can use the [New-AzureRmADApplication](https://docs.microsoft.com/powershell/resourcemanager/azurerm.resources/v3.3.0/new-azurermadapplication) PowerShell cmdlet.</span></span> <span data-ttu-id="fef8d-111">您向 Azure Key Vault 註冊的憑證只需要公開金鑰 </span><span class="sxs-lookup"><span data-stu-id="fef8d-111">The certificate that you register with Azure Key Vault needs only your public key.</span></span> <span data-ttu-id="fef8d-112">(您的應用程式將會使用私密金鑰)。</span><span class="sxs-lookup"><span data-stu-id="fef8d-112">(Your application will use the private key.)</span></span>

<span data-ttu-id="fef8d-113">第二，建立新的服務主體，以提供已註冊應用程式對金鑰保存庫的存取。</span><span class="sxs-lookup"><span data-stu-id="fef8d-113">Second, give the registered application access to the key vault by creating a new service principal.</span></span> <span data-ttu-id="fef8d-114">您可以使用下列 PowerShell 命令執行這項作業：</span><span class="sxs-lookup"><span data-stu-id="fef8d-114">You can do this using the following PowerShell commands:</span></span>

```powershell
$sp = New-AzureRmADServicePrincipal -ApplicationId "<Application ID guid>"
Set-AzureRmKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
```

<span data-ttu-id="fef8d-115">第三，在建立 IConfigurationRoot 執行個體時呼叫 IConfigurationBuilder.AddAzureKeyVault 擴充方法，以包含金鑰保存庫作為應用程式中的組態來源。</span><span class="sxs-lookup"><span data-stu-id="fef8d-115">Third, include the key vault as a configuration source in your application by calling the IConfigurationBuilder.AddAzureKeyVault extension method when you create an IConfigurationRoot instance.</span></span> <span data-ttu-id="fef8d-116">請注意，呼叫 AddAzureKeyVault 時需要已註冊並提供先前步驟中金鑰保存庫存取權的應用程式識別碼。</span><span class="sxs-lookup"><span data-stu-id="fef8d-116">Note that calling AddAzureKeyVault will require the application ID that was registered and given access to the key vault in the previous steps.</span></span>

  <span data-ttu-id="fef8d-117">目前，.NET Standard 和 .NET Core 支援使用用戶端識別碼和用戶端密碼，以從 Azure Key Vault 取得組態資訊。</span><span class="sxs-lookup"><span data-stu-id="fef8d-117">Currently, .NET Standard and .NET Core support getting configuration information from an Azure Key Vault using a client ID and client secret.</span></span> <span data-ttu-id="fef8d-118">.NET Framework 應用程式可以使用採用憑證來取代用戶端密碼的 IConfigurationBuilder.AddAzureKeyVault 多載。</span><span class="sxs-lookup"><span data-stu-id="fef8d-118">.NET Framework applications can use an overload of IConfigurationBuilder.AddAzureKeyVault that takes a certificate in place of the client secret.</span></span> <span data-ttu-id="fef8d-119">從這項撰寫開始，工作[正在進行](https://github.com/aspnet/Configuration/issues/605)，讓該多載可在 .NET Standard 和 .NET Core 中使用。</span><span class="sxs-lookup"><span data-stu-id="fef8d-119">As of this writing, work is [in progress](https://github.com/aspnet/Configuration/issues/605) to make that overload available in .NET Standard and .NET Core.</span></span> <span data-ttu-id="fef8d-120">除非接受憑證的 AddAzureKeyVault 多載可用，否則 ASP.NET Core 應用程式可以明確建立 KeyVaultClient 物件，以使用憑證型驗證來存取 Azure Key Vault，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="fef8d-120">Until the AddAzureKeyVault overload that accepts a certificate is available, ASP.NET Core applications can access an Azure Key Vault with certificate-based authentication by explicitly creating a KeyVaultClient object, as shown in the following example:</span></span>

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

<span data-ttu-id="fef8d-121">在此範例中，AddAzureKeyVault 呼叫是在組態提供者登錄的結尾。</span><span class="sxs-lookup"><span data-stu-id="fef8d-121">In this example, the call to AddAzureKeyVault comes at the end of configuration provider registration.</span></span> <span data-ttu-id="fef8d-122">最好將 Azure Key Vault 註冊為最後一個組態提供者，讓它可以覆寫先前提供者中的組態值，因此其他來源中的組態值不會覆寫金鑰保存庫中的組態值。</span><span class="sxs-lookup"><span data-stu-id="fef8d-122">It is a best practice to register Azure Key Vault as the last configuration provider so that it has an opportunity to override configuration values from previous providers, and so that no configuration values from other sources override those from the key vault.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="fef8d-123">其他資源</span><span class="sxs-lookup"><span data-stu-id="fef8d-123">Additional resources</span></span>

-   <span data-ttu-id="fef8d-124">**使用 Azure Key Vault 來保護應用程式祕密**
    [*https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault*](https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault)</span><span class="sxs-lookup"><span data-stu-id="fef8d-124">**Using Azure Key Vault to protect application secrets**
[*https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault*](https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault)</span></span>

-   <span data-ttu-id="fef8d-125">**在開發期間安全儲存應用程式祕密**
    [*https://docs.microsoft.com/aspnet/core/security/app-secrets*](https://docs.microsoft.com/aspnet/core/security/app-secrets)</span><span class="sxs-lookup"><span data-stu-id="fef8d-125">**Safe storage of app secrets during development**
[*https://docs.microsoft.com/aspnet/core/security/app-secrets*](https://docs.microsoft.com/aspnet/core/security/app-secrets)</span></span>

-   <span data-ttu-id="fef8d-126">**設定資料保護**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview)</span><span class="sxs-lookup"><span data-stu-id="fef8d-126">**Configuring data protection**
[*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview)</span></span>

-   <span data-ttu-id="fef8d-127">**金鑰管理和存留期**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings\#data-protection-default-settings*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings#data-protection-default-settings)</span><span class="sxs-lookup"><span data-stu-id="fef8d-127">**Key management and lifetime**
[*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings\#data-protection-default-settings*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings#data-protection-default-settings)</span></span>

-   <span data-ttu-id="fef8d-128">**Microsoft.Extensions.Configuration.DockerSecrets.**</span><span class="sxs-lookup"><span data-stu-id="fef8d-128">**Microsoft.Extensions.Configuration.DockerSecrets.**</span></span> <span data-ttu-id="fef8d-129">GitHub 存放庫。</span><span class="sxs-lookup"><span data-stu-id="fef8d-129">GitHub repo.</span></span>
    [*https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets*](https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets)

>[!div class="step-by-step"]
<span data-ttu-id="fef8d-130">[上一頁](developer-app-secrets-storage.md)
[下一頁](../key-takeaways.md)</span><span class="sxs-lookup"><span data-stu-id="fef8d-130">[Previous](developer-app-secrets-storage.md)
[Next](../key-takeaways.md)</span></span>

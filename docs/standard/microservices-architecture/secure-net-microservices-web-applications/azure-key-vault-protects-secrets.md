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
# <a name="using-azure-key-vault-to-protect-secrets-at-production-time"></a><span data-ttu-id="bb1ec-104">在實際執行階段保護機密資訊使用 Azure 金鑰保存庫</span><span class="sxs-lookup"><span data-stu-id="bb1ec-104">Using Azure Key Vault to protect secrets at production time</span></span>

<span data-ttu-id="bb1ec-105">密碼儲存為環境變數，或儲存的密碼管理員工具仍會儲存在本機，並在電腦上未加密。</span><span class="sxs-lookup"><span data-stu-id="bb1ec-105">Secrets stored as environment variables or stored by the Secret Manager tool are still stored locally and unencrypted on the machine.</span></span> <span data-ttu-id="bb1ec-106">儲存機密資料的更安全選項是[Azure 金鑰保存庫](https://azure.microsoft.com/services/key-vault/)，這樣會提供安全的中央位置來儲存金鑰和密碼。</span><span class="sxs-lookup"><span data-stu-id="bb1ec-106">A more secure option for storing secrets is [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), which provides a secure, central location for storing keys and secrets.</span></span>

<span data-ttu-id="bb1ec-107">Microsoft.Extensions.Configuration.AzureKeyVault 封裝可讓 ASP.NET Core 應用程式來讀取 Azure 金鑰保存庫中的組態資訊。</span><span class="sxs-lookup"><span data-stu-id="bb1ec-107">The Microsoft.Extensions.Configuration.AzureKeyVault package allows an ASP.NET Core application to read configuration information from Azure Key Vault.</span></span> <span data-ttu-id="bb1ec-108">若要開始使用 Azure 金鑰保存庫中的機密資料，您可以依照下列步驟：</span><span class="sxs-lookup"><span data-stu-id="bb1ec-108">To start using secrets from an Azure Key Vault, you follow these steps:</span></span>

<span data-ttu-id="bb1ec-109">首先，為 Azure AD 應用程式註冊您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="bb1ec-109">First, register your application as an Azure AD application.</span></span> <span data-ttu-id="bb1ec-110">（金鑰保存庫的存取是由 Azure AD 管理）。這可以透過 Azure 管理入口網站。</span><span class="sxs-lookup"><span data-stu-id="bb1ec-110">(Access to key vaults is managed by Azure AD.) This can be done through the Azure management portal.</span></span>

<span data-ttu-id="bb1ec-111">或者，如果您希望應用程式使用憑證，而不密碼或用戶端密碼進行驗證，您可以使用[新增 AzureRmADApplication](https://docs.microsoft.com/powershell/resourcemanager/azurerm.resources/v3.3.0/new-azurermadapplication) PowerShell cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bb1ec-111">Alternatively, if you want your application to authenticate using a certificate instead of a password or client secret, you can use the [New-AzureRmADApplication](https://docs.microsoft.com/powershell/resourcemanager/azurerm.resources/v3.3.0/new-azurermadapplication) PowerShell cmdlet.</span></span> <span data-ttu-id="bb1ec-112">Azure 金鑰保存庫中註冊的憑證必須只有您的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="bb1ec-112">The certificate that you register with Azure Key Vault needs only your public key.</span></span> <span data-ttu-id="bb1ec-113">（您的應用程式會使用私密金鑰）。</span><span class="sxs-lookup"><span data-stu-id="bb1ec-113">(Your application will use the private key.)</span></span>

<span data-ttu-id="bb1ec-114">第二，提供已註冊的應用程式的存取金鑰保存庫，藉由建立新的服務主體。</span><span class="sxs-lookup"><span data-stu-id="bb1ec-114">Second, give the registered application access to the key vault by creating a new service principal.</span></span> <span data-ttu-id="bb1ec-115">您可以使用下列 PowerShell 命令：</span><span class="sxs-lookup"><span data-stu-id="bb1ec-115">You can do this using the following PowerShell commands:</span></span>

```powershell
$sp = New-AzureRmADServicePrincipal -ApplicationId "<Application ID guid>"
Set-AzureRmKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
```

<span data-ttu-id="bb1ec-116">第三，包含金鑰保存庫做為組態中的來源應用程式藉由呼叫 IConfigurationBuilder.AddAzureKeyVault 擴充方法，當您建立 IConfigurationRoot 執行個體。</span><span class="sxs-lookup"><span data-stu-id="bb1ec-116">Third, include the key vault as a configuration source in your application by calling the IConfigurationBuilder.AddAzureKeyVault extension method when you create an IConfigurationRoot instance.</span></span> <span data-ttu-id="bb1ec-117">請注意，呼叫 AddAzureKeyVault 將需要已註冊並提供存取金鑰保存庫在先前步驟中的應用程式識別碼。</span><span class="sxs-lookup"><span data-stu-id="bb1ec-117">Note that calling AddAzureKeyVault will require the application ID that was registered and given access to the key vault in the previous steps.</span></span>

  <span data-ttu-id="bb1ec-118">目前，標準.NET 和.NET Core 支援取得組態資訊從 Azure 金鑰保存庫使用用戶端識別碼和用戶端密碼。</span><span class="sxs-lookup"><span data-stu-id="bb1ec-118">Currently, .NET Standard and .NET Core support getting configuration information from an Azure Key Vault using a client ID and client secret.</span></span> <span data-ttu-id="bb1ec-119">.NET framework 應用程式可以使用 IConfigurationBuilder.AddAzureKeyVault 採用的憑證來取代用戶端密碼的多載。</span><span class="sxs-lookup"><span data-stu-id="bb1ec-119">.NET Framework applications can use an overload of IConfigurationBuilder.AddAzureKeyVault that takes a certificate in place of the client secret.</span></span> <span data-ttu-id="bb1ec-120">工作是在撰寫本文[正在](https://github.com/aspnet/Configuration/issues/605)將該多載提供的標準.NET 和.NET 核心。</span><span class="sxs-lookup"><span data-stu-id="bb1ec-120">As of this writing, work is [in progress](https://github.com/aspnet/Configuration/issues/605) to make that overload available in .NET Standard and .NET Core.</span></span> <span data-ttu-id="bb1ec-121">接受憑證可用於 AddAzureKeyVault 多載中，直到 ASP.NET Core 應用程式可以存取 Azure 金鑰保存庫憑證為基礎的驗證與明確建立 KeyVaultClient 物件，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="bb1ec-121">Until the AddAzureKeyVault overload that accepts a certificate is available, ASP.NET Core applications can access an Azure Key Vault with certificate-based authentication by explicitly creating a KeyVaultClient object, as shown in the following example:</span></span>

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

<span data-ttu-id="bb1ec-122">在此範例中，AddAzureKeyVault 呼叫是在組態提供者登錄的結尾。</span><span class="sxs-lookup"><span data-stu-id="bb1ec-122">In this example, the call to AddAzureKeyVault comes at the end of configuration provider registration.</span></span> <span data-ttu-id="bb1ec-123">它是 Azure 金鑰保存庫註冊為最後的組態提供者，使其具有可以覆寫組態值，從上一個提供者，以及任何其他來源的組態值會覆寫從金鑰保存庫的最佳作法。</span><span class="sxs-lookup"><span data-stu-id="bb1ec-123">It is a best practice to register Azure Key Vault as the last configuration provider so that it has an opportunity to override configuration values from previous providers, and so that no configuration values from other sources override those from the key vault.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="bb1ec-124">其他資源</span><span class="sxs-lookup"><span data-stu-id="bb1ec-124">Additional resources</span></span>

-   <span data-ttu-id="bb1ec-125">**使用 Azure 金鑰保存庫保護應用程式密碼**
    [*https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault*](https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault)</span><span class="sxs-lookup"><span data-stu-id="bb1ec-125">**Using Azure Key Vault to protect application secrets**
[*https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault*](https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault)</span></span>

-   <span data-ttu-id="bb1ec-126">**在開發期間的應用程式密碼的安全存放**
    [*https://docs.microsoft.com/aspnet/core/security/app-secrets*](https://docs.microsoft.com/aspnet/core/security/app-secrets)</span><span class="sxs-lookup"><span data-stu-id="bb1ec-126">**Safe storage of app secrets during development**
[*https://docs.microsoft.com/aspnet/core/security/app-secrets*](https://docs.microsoft.com/aspnet/core/security/app-secrets)</span></span>

-   <span data-ttu-id="bb1ec-127">**設定資料保護**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview)</span><span class="sxs-lookup"><span data-stu-id="bb1ec-127">**Configuring data protection**
[*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview)</span></span>

-   <span data-ttu-id="bb1ec-128">**金鑰管理和存留期**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings\#資料保護的預設設定*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings#data-protection-default-settings)</span><span class="sxs-lookup"><span data-stu-id="bb1ec-128">**Key management and lifetime**
[*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings\#data-protection-default-settings*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings#data-protection-default-settings)</span></span>

-   <span data-ttu-id="bb1ec-129">**Microsoft.Extensions.Configuration.DockerSecrets。**</span><span class="sxs-lookup"><span data-stu-id="bb1ec-129">**Microsoft.Extensions.Configuration.DockerSecrets.**</span></span> <span data-ttu-id="bb1ec-130">GitHub 儲存機制。</span><span class="sxs-lookup"><span data-stu-id="bb1ec-130">GitHub repo.</span></span>
    [<span data-ttu-id="bb1ec-131">*https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets*</span><span class="sxs-lookup"><span data-stu-id="bb1ec-131">*https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets*</span></span>](https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets)

>[!div class="step-by-step"]
<span data-ttu-id="bb1ec-132">[上一個](開發人員為應用程式-機密-storage.md) [下一步] (.../ 索引鍵 takeaways.md）</span><span class="sxs-lookup"><span data-stu-id="bb1ec-132">[Previous] (developer-app-secrets-storage.md) [Next] (../key-takeaways.md)</span></span>

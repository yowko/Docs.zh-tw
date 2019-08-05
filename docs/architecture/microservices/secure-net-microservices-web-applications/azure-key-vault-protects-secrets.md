---
title: 使用 Azure Key Vault 以在生產階段保護密碼
description: .NET 微服務和 Web 應用程式中的安全性 - Azure Key Vault 是可讓系統管理員完全掌控應用程式祕密處理的絕佳方式。 系統管理員甚至可以指派和撤銷開發值，而不需要開發人員來處理它們。
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: 63bf357c95b82a820b6dfb6a2d24a5d89f66de72
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68675665"
---
# <a name="use-azure-key-vault-to-protect-secrets-at-production-time"></a><span data-ttu-id="9d970-104">使用 Azure Key Vault 在生產階段保護祕密</span><span class="sxs-lookup"><span data-stu-id="9d970-104">Use Azure Key Vault to protect secrets at production time</span></span>

<span data-ttu-id="9d970-105">儲存為環境變數或由密碼管理員工具所儲存的密碼仍然會儲存在本機，而且在電腦上未加密。</span><span class="sxs-lookup"><span data-stu-id="9d970-105">Secrets stored as environment variables or stored by the Secret Manager tool are still stored locally and unencrypted on the machine.</span></span> <span data-ttu-id="9d970-106">儲存密碼的更安全選項是 [Azure Key Vault](https://azure.microsoft.com/services/key-vault/)，以提供安全且集中的位置來儲存金鑰和密碼。</span><span class="sxs-lookup"><span data-stu-id="9d970-106">A more secure option for storing secrets is [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), which provides a secure, central location for storing keys and secrets.</span></span>

<span data-ttu-id="9d970-107">**Microsoft.Extensions.Configuration.AzureKeyVault** 套件允許 ASP.NET Core 應用程式從 Azure Key Vault 中讀取設定資訊。</span><span class="sxs-lookup"><span data-stu-id="9d970-107">The **Microsoft.Extensions.Configuration.AzureKeyVault** package allows an ASP.NET Core application to read configuration information from Azure Key Vault.</span></span> <span data-ttu-id="9d970-108">若要開始使用 Azure Key Vault 中的密碼，您可以遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="9d970-108">To start using secrets from an Azure Key Vault, you follow these steps:</span></span>

1. <span data-ttu-id="9d970-109">將應用程式註冊為 Azure AD 應用程式。</span><span class="sxs-lookup"><span data-stu-id="9d970-109">Register your application as an Azure AD application.</span></span> <span data-ttu-id="9d970-110">(對金鑰保存庫的存取是由 Azure AD 所管理)。這可以透過 Azure 管理入口網站完成。</span><span class="sxs-lookup"><span data-stu-id="9d970-110">(Access to key vaults is managed by Azure AD.) This can be done through the Azure management portal.</span></span>\

   <span data-ttu-id="9d970-111">或者，如果您想要應用程式使用憑證進行驗證，而不是使用密碼或用戶端密碼，則可以使用 [New-AzADApplication](/powershell/module/az.resources/new-azadapplication) PowerShell Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9d970-111">Alternatively, if you want your application to authenticate using a certificate instead of a password or client secret, you can use the [New-AzADApplication](/powershell/module/az.resources/new-azadapplication) PowerShell cmdlet.</span></span> <span data-ttu-id="9d970-112">您向 Azure Key Vault 註冊的憑證只需要公開金鑰</span><span class="sxs-lookup"><span data-stu-id="9d970-112">The certificate that you register with Azure Key Vault needs only your public key.</span></span> <span data-ttu-id="9d970-113">您的應用程式將會使用私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="9d970-113">Your application will use the private key.</span></span>

2. <span data-ttu-id="9d970-114">建立新的服務主體，以提供已註冊應用程式對金鑰保存庫的存取。</span><span class="sxs-lookup"><span data-stu-id="9d970-114">Give the registered application access to the key vault by creating a new service principal.</span></span> <span data-ttu-id="9d970-115">您可以使用下列 PowerShell 命令執行這項作業：</span><span class="sxs-lookup"><span data-stu-id="9d970-115">You can do this using the following PowerShell commands:</span></span>

   ```powershell
   $sp = New-AzADServicePrincipal -ApplicationId "<Application ID guid>"
   Set-AzKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
   ```

3. <span data-ttu-id="9d970-116">在建立 <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> 執行個體時呼叫 <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType> 擴充方法，以包含金鑰保存庫作為應用程式中的設定來源。</span><span class="sxs-lookup"><span data-stu-id="9d970-116">Include the key vault as a configuration source in your application by calling the <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType> extension method when you create an <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> instance.</span></span> <span data-ttu-id="9d970-117">請注意，呼叫 `AddAzureKeyVault` 時需要已註冊並提供先前步驟中金鑰保存庫存取權的應用程式識別碼。</span><span class="sxs-lookup"><span data-stu-id="9d970-117">Note that calling `AddAzureKeyVault` requires the application ID that was registered and given access to the key vault in the previous steps.</span></span>

   <span data-ttu-id="9d970-118">您也可以藉由包含 [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) 套件的參考，使用採用憑證來取代用戶端祕密的 `AddAzureKeyVault` 多載。</span><span class="sxs-lookup"><span data-stu-id="9d970-118">You can also use an overload of `AddAzureKeyVault` that takes a certificate in place of the client secret by just including a reference to the [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) package.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9d970-119">建議您將 Azure Key Vault 註冊為最新的設定提供者，如此它才能覆寫先前提供者的設定值。</span><span class="sxs-lookup"><span data-stu-id="9d970-119">We recommend you to register Azure Key Vault as the last configuration provider, so it can override configuration values from previous providers.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="9d970-120">其他資源</span><span class="sxs-lookup"><span data-stu-id="9d970-120">Additional resources</span></span>

- <span data-ttu-id="9d970-121">**使用 Azure Key Vault 保護應用程式祕密** </span><span class="sxs-lookup"><span data-stu-id="9d970-121">**Using Azure Key Vault to protect application secrets** </span></span>\
  [https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault](/azure/guidance/guidance-multitenant-identity-keyvault)

- <span data-ttu-id="9d970-122">**在開發期間安全儲存應用程式祕密** </span><span class="sxs-lookup"><span data-stu-id="9d970-122">**Safe storage of app secrets during development** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/app-secrets](/aspnet/core/security/app-secrets)

- <span data-ttu-id="9d970-123">**設定資料保護** </span><span class="sxs-lookup"><span data-stu-id="9d970-123">**Configuring data protection** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview](/aspnet/core/security/data-protection/configuration/overview)

- <span data-ttu-id="9d970-124">**ASP.NET Core 中的資料保護金鑰管理和存留期** </span><span class="sxs-lookup"><span data-stu-id="9d970-124">**Data Protection key management and lifetime in ASP.NET Core** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings](/aspnet/core/security/data-protection/configuration/default-settings)

- <span data-ttu-id="9d970-125">**Microsoft.Extensions.Configuration.KeyPerFile** GitHub 存放庫。</span><span class="sxs-lookup"><span data-stu-id="9d970-125">**Microsoft.Extensions.Configuration.KeyPerFile** GitHub repository.</span></span> \
  <https://github.com/aspnet/Configuration/tree/master/src/Config.KeyPerFile>

>[!div class="step-by-step"]
><span data-ttu-id="9d970-126">[上一頁](developer-app-secrets-storage.md)
>[下一頁](../key-takeaways.md)</span><span class="sxs-lookup"><span data-stu-id="9d970-126">[Previous](developer-app-secrets-storage.md)
[Next](../key-takeaways.md)</span></span>

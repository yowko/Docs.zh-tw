---
title: 在開發期間安全地儲存應用程式祕密
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 在開發期間安全地儲存應用程式祕密
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 6f5dfbb53b99fec4d7cc66c528fe866c71c2172f
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143866"
---
# <a name="storing-application-secrets-safely-during-development"></a><span data-ttu-id="29011-103">在開發期間安全地儲存應用程式祕密</span><span class="sxs-lookup"><span data-stu-id="29011-103">Storing application secrets safely during development</span></span>

<span data-ttu-id="29011-104">為了連接到受保護的資源和其他服務，ASP.NET Core 應用程式通常需要使用包含機密資訊的連接字串、密碼或其他認證。</span><span class="sxs-lookup"><span data-stu-id="29011-104">To connect with protected resources and other services, ASP.NET Core applications typically need to use connection strings, passwords, or other credentials that contain sensitive information.</span></span> <span data-ttu-id="29011-105">這些機密資訊稱為「祕密」。</span><span class="sxs-lookup"><span data-stu-id="29011-105">These sensitive pieces of information are called *secrets*.</span></span> <span data-ttu-id="29011-106">最佳做法是不要在原始程式碼中包含祕密，而且絕不要在原始檔控制中儲存秘密。</span><span class="sxs-lookup"><span data-stu-id="29011-106">It is a best practice to not include secrets in source code and certainly not to store secrets in source control.</span></span> <span data-ttu-id="29011-107">相反地，您應該使用 ASP.NET Core 組態模型，從更安全的位置讀取秘密。</span><span class="sxs-lookup"><span data-stu-id="29011-107">Instead, you should use the ASP.NET Core configuration model to read the secrets from more secure locations.</span></span>

<span data-ttu-id="29011-108">您應該將用於存取開發和暫存資源的秘密，與用於存取生產資源的秘密分開，因為不同的人需要存取不同組的秘密。</span><span class="sxs-lookup"><span data-stu-id="29011-108">You should separate the secrets for accessing development and staging resources from those used for accessing production resources, because different individuals will need access to those different sets of secrets.</span></span> <span data-ttu-id="29011-109">若要儲存在開發期間使用的秘密，常見的方法是將秘密儲存在環境變數中，或藉由使用 ASP.NET Core Secret Manager 工具來儲存。</span><span class="sxs-lookup"><span data-stu-id="29011-109">To store secrets used during development, common approaches are to either store secrets in environment variables or by using the ASP.NET Core Secret Manager tool.</span></span> <span data-ttu-id="29011-110">為了在生產環境中更安全的儲存，微服務可以將秘密儲存在 Azure Key Vault 中。</span><span class="sxs-lookup"><span data-stu-id="29011-110">For more secure storage in production environments, microservices can store secrets in an Azure Key Vault.</span></span>

## <a name="storing-secrets-in-environment-variables"></a><span data-ttu-id="29011-111">將秘密儲存在環境變數中</span><span class="sxs-lookup"><span data-stu-id="29011-111">Storing secrets in environment variables</span></span>

<span data-ttu-id="29011-112">將秘密與原始程式碼分開保存的一個方法，是由開發人員在其開發電腦上將字串型秘密設定為[環境變數](https://docs.microsoft.com/aspnet/core/security/app-secrets#environment-variables)。</span><span class="sxs-lookup"><span data-stu-id="29011-112">One way to keep secrets out of source code is for developers to set string-based secrets as [environment variables](https://docs.microsoft.com/aspnet/core/security/app-secrets#environment-variables) on their development machines.</span></span> <span data-ttu-id="29011-113">當您使用環境變數來儲存具有階層式名稱 (巢狀於組態區段中) 的秘密時，請建立環境變數的名稱，其中包含秘密名稱的完整階層，並以冒號 (:) 分隔。</span><span class="sxs-lookup"><span data-stu-id="29011-113">When you use environment variables to store secrets with hierarchical names (those nested in configuration sections), create a name for the environment variables that includes the full hierarchy of the secret’s name, delimited with colons (:).</span></span>

<span data-ttu-id="29011-114">例如，將環境變數 Logging:LogLevel:Default 設定為 Debug 相當於下列 JSON 檔案中的組態值：</span><span class="sxs-lookup"><span data-stu-id="29011-114">For example, setting an environment variable Logging:LogLevel:Default to Debug would be equivalent to a configuration value from the following JSON file:</span></span>

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

<span data-ttu-id="29011-115">若要從環境變數存取這些值，應用程式只需要在建構 IConfigurationRoot 物件時在其 ConfigurationBuilder 上呼叫 AddEnvironmentVariables 即可。</span><span class="sxs-lookup"><span data-stu-id="29011-115">To access these values from environment variables, the application just needs to call AddEnvironmentVariables on its ConfigurationBuilder when constructing an IConfigurationRoot object.</span></span>

<span data-ttu-id="29011-116">請注意，環境變數通常會儲存為純文字，因此如果具有環境變數的電腦或處理序遭到入侵，就會顯示環境變數值。</span><span class="sxs-lookup"><span data-stu-id="29011-116">Note that environment variables are generally stored as plain text, so if the machine or process with the environment variables is compromised, the environment variable values will be visible.</span></span>

## <a name="storing-secrets-using-the-aspnet-core-secret-manager"></a><span data-ttu-id="29011-117">使用 ASP.NET Core Secret Manager 儲存秘密</span><span class="sxs-lookup"><span data-stu-id="29011-117">Storing secrets using the ASP.NET Core Secret Manager</span></span>

<span data-ttu-id="29011-118">ASP.NET Core [Secret Manager](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager) 工具提供另一種方法來將秘密與原始程式碼分開保存。</span><span class="sxs-lookup"><span data-stu-id="29011-118">The ASP.NET Core [Secret Manager](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager) tool provides another method of keeping secrets out of source code.</span></span> <span data-ttu-id="29011-119">若要使用 Secret Manager 工具，請在您的專案檔中包含 Microsoft.Extensions.SecretManager.Tools 封裝的工具參考 (DotNetCliToolReference)。</span><span class="sxs-lookup"><span data-stu-id="29011-119">To use the Secret Manager tool, include a tools reference (DotNetCliToolReference) to the Microsoft.Extensions.SecretManager.Tools package in your project file.</span></span> <span data-ttu-id="29011-120">一旦該相依性存在並已還原，即可使用 dotnet user-secrets 命令從命令列設定祕密的值。</span><span class="sxs-lookup"><span data-stu-id="29011-120">Once that dependency is present and has been restored, the dotnet user-secrets command can be used to set the value of secrets from the command line.</span></span> <span data-ttu-id="29011-121">這些秘密會儲存在使用者設定檔目錄中的 JSON 檔案中 (細目會因 OS 而異)，並遠離原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="29011-121">These secrets will be stored in a JSON file in the user’s profile directory (details vary by OS), away from source code.</span></span>

<span data-ttu-id="29011-122">Secret Manager 工具所設定的秘密會依使用秘密之專案的 UserSecretsId 屬性來組織。</span><span class="sxs-lookup"><span data-stu-id="29011-122">Secrets set by the Secret Manager tool are organized by the UserSecretsId property of the project that is using the secrets.</span></span> <span data-ttu-id="29011-123">因此，您必須確定在專案檔中設定 UserSecretsId 屬性 (如下列程式碼片段所示)。</span><span class="sxs-lookup"><span data-stu-id="29011-123">Therefore, you must be sure to set the UserSecretsId property in your project file (as shown in the snippet below).</span></span> <span data-ttu-id="29011-124">識別碼只要在專案中是唯一的，所使用的實際字串並不重要。</span><span class="sxs-lookup"><span data-stu-id="29011-124">The actual string used as the ID is not important as long as it is unique in the project.</span></span>

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

<span data-ttu-id="29011-125">若要使用 Secret Manager 儲存在應用程式中的秘密，請在 ConfigurationBuilder 執行個體上呼叫 AddUserSecrets&lt;T&gt; 以在其組態中包含應用程式的秘密。</span><span class="sxs-lookup"><span data-stu-id="29011-125">Using secrets stored with Secret Manager in an application is accomplished by calling AddUserSecrets&lt;T&gt; on the ConfigurationBuilder instance to include secrets for the application in its configuration.</span></span> <span data-ttu-id="29011-126">泛型參數 T 應該是已套用 UserSecretId 之組件的類型。</span><span class="sxs-lookup"><span data-stu-id="29011-126">The generic parameter T should be a type from the assembly that the UserSecretId was applied to.</span></span> <span data-ttu-id="29011-127">通常使用 AddUserSecrets&lt;Startup&gt; 就可以。</span><span class="sxs-lookup"><span data-stu-id="29011-127">Usually using AddUserSecrets&lt;Startup&gt; is fine.</span></span>


>[!div class="step-by-step"]
><span data-ttu-id="29011-128">[上一頁](authorization-net-microservices-web-applications.md)
>[下一頁](azure-key-vault-protects-secrets.md)</span><span class="sxs-lookup"><span data-stu-id="29011-128">[Previous](authorization-net-microservices-web-applications.md)
[Next](azure-key-vault-protects-secrets.md)</span></span>
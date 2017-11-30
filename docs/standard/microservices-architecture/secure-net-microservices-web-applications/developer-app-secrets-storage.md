---
title: "在開發期間，安全地儲存應用程式密碼"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |在開發期間，安全地儲存應用程式密碼"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: f1b8b257a3e677c7e665e1d394a8adf7e651bec2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="storing-application-secrets-safely-during-development"></a><span data-ttu-id="21d90-104">在開發期間，安全地儲存應用程式密碼</span><span class="sxs-lookup"><span data-stu-id="21d90-104">Storing application secrets safely during development</span></span>

<span data-ttu-id="21d90-105">若要連接與受保護的資源和其他服務，ASP.NET Core 應用程式通常需要使用連接字串、 密碼或其他包含機密資訊的認證。</span><span class="sxs-lookup"><span data-stu-id="21d90-105">To connect with protected resources and other services, ASP.NET Core applications typically need to use connection strings, passwords, or other credentials that contain sensitive information.</span></span> <span data-ttu-id="21d90-106">這些機密的資訊片段稱為*密碼*。</span><span class="sxs-lookup"><span data-stu-id="21d90-106">These sensitive pieces of information are called *secrets*.</span></span> <span data-ttu-id="21d90-107">最佳作法是在原始程式碼中包含機密資料，當然不將密碼儲存在原始檔控制它。</span><span class="sxs-lookup"><span data-stu-id="21d90-107">It is a best practice to not include secrets in source code and certainly not to store secrets in source control.</span></span> <span data-ttu-id="21d90-108">相反地，您應該從更安全的位置讀取密碼使用 ASP.NET Core 組態模型。</span><span class="sxs-lookup"><span data-stu-id="21d90-108">Instead, you should use the ASP.NET Core configuration model to read the secrets from more secure locations.</span></span>

<span data-ttu-id="21d90-109">您應該將用於存取開發和暫存資源，因為不同的個人將需要存取這些不同的密碼，以存取實際執行資源使用的密碼。</span><span class="sxs-lookup"><span data-stu-id="21d90-109">You should separate the secrets for accessing development and staging resources from those used for accessing production resources, because different individuals will need access to those different sets of secrets.</span></span> <span data-ttu-id="21d90-110">若要儲存在開發期間使用的密碼，常見的方法是請將密碼儲存在環境變數，或使用 ASP.NET Core 密碼管理員工具。</span><span class="sxs-lookup"><span data-stu-id="21d90-110">To store secrets used during development, common approaches are to either store secrets in environment variables or by using the ASP.NET Core Secret Manager tool.</span></span> <span data-ttu-id="21d90-111">在生產環境中更安全的儲存體，microservices 可以將密碼儲存在 Azure 金鑰保存庫。</span><span class="sxs-lookup"><span data-stu-id="21d90-111">For more secure storage in production environments, microservices can store secrets in an Azure Key Vault.</span></span>

## <a name="storing-secrets-in-environment-variables"></a><span data-ttu-id="21d90-112">環境變數中儲存機密資料</span><span class="sxs-lookup"><span data-stu-id="21d90-112">Storing secrets in environment variables</span></span>

<span data-ttu-id="21d90-113">保留原始程式碼出的機密資料的其中一個方法是讓開發人員設定字串為基礎的密碼，做為[環境變數](https://docs.microsoft.com/aspnet/core/security/app-secrets#environment-variables)其開發電腦上。</span><span class="sxs-lookup"><span data-stu-id="21d90-113">One way to keep secrets out of source code is for developers to set string-based secrets as [environment variables](https://docs.microsoft.com/aspnet/core/security/app-secrets#environment-variables) on their development machines.</span></span> <span data-ttu-id="21d90-114">當您使用環境變數以儲存機密資料，有名為階層式 （其組態區段中的巢狀），建立包含密碼的名稱的完整階層架構的環境變數名稱時，會以冒號 （:） 分隔。</span><span class="sxs-lookup"><span data-stu-id="21d90-114">When you use environment variables to store secrets with hierarchical names (those nested in configuration sections), create a name for the environment variables that includes the full hierarchy of the secret’s name, delimited with colons (:).</span></span>

<span data-ttu-id="21d90-115">例如，要進行偵錯設定環境變數記錄： LogLevel:Default 會等於下列 JSON 檔案中設定值：</span><span class="sxs-lookup"><span data-stu-id="21d90-115">For example, setting an environment variable Logging:LogLevel:Default to Debug would be equivalent to a configuration value from the following JSON file:</span></span>

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

<span data-ttu-id="21d90-116">若要存取這些值從環境變數，應用程式只需要建構 IConfigurationRoot 物件時，呼叫其 ConfigurationBuilder AddEnvironmentVariables。</span><span class="sxs-lookup"><span data-stu-id="21d90-116">To access these values from environment variables, the application just needs to call AddEnvironmentVariables on its ConfigurationBuilder when constructing an IConfigurationRoot object.</span></span>

<span data-ttu-id="21d90-117">請注意，環境變數通常會儲存為純文字，因此如果遭到入侵的電腦或使用環境變數的程序，會顯示環境變數值。</span><span class="sxs-lookup"><span data-stu-id="21d90-117">Note that environment variables are generally stored as plain text, so if the machine or process with the environment variables is compromised, the environment variable values will be visible.</span></span>

## <a name="storing-secrets-using-the-aspnet-core-secret-manager"></a><span data-ttu-id="21d90-118">儲存機密資料，使用 ASP.NET Core 密碼管理員</span><span class="sxs-lookup"><span data-stu-id="21d90-118">Storing secrets using the ASP.NET Core Secret Manager</span></span>

<span data-ttu-id="21d90-119">ASP.NET Core[密碼管理員](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager)工具提供的原始碼超出保密的另一種方法。</span><span class="sxs-lookup"><span data-stu-id="21d90-119">The ASP.NET Core [Secret Manager](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager) tool provides another method of keeping secrets out of source code.</span></span> <span data-ttu-id="21d90-120">若要使用密碼管理員工具，包含的工具參考 (DotNetCliToolReference) Microsoft.Extensions.SecretManager.Tools 封裝專案檔中。</span><span class="sxs-lookup"><span data-stu-id="21d90-120">To use the Secret Manager tool, include a tools reference (DotNetCliToolReference) to the Microsoft.Extensions.SecretManager.Tools package in your project file.</span></span> <span data-ttu-id="21d90-121">一旦該相依性存在，並且已還原，dotnet 使用者密碼命令可用來從命令列設定密碼的值。</span><span class="sxs-lookup"><span data-stu-id="21d90-121">Once that dependency is present and has been restored, the dotnet user-secrets command can be used to set the value of secrets from the command line.</span></span> <span data-ttu-id="21d90-122">這些密碼將儲存在使用者的設定檔目錄中 （詳細資料會因作業系統），遠離原始碼在 JSON 檔案中。</span><span class="sxs-lookup"><span data-stu-id="21d90-122">These secrets will be stored in a JSON file in the user’s profile directory (details vary by OS), away from source code.</span></span>

<span data-ttu-id="21d90-123">密碼管理員工具來設定的密碼被依專案是使用密碼 UserSecretsId 屬性。</span><span class="sxs-lookup"><span data-stu-id="21d90-123">Secrets set by the Secret Manager tool are organized by the UserSecretsId property of the project that is using the secrets.</span></span> <span data-ttu-id="21d90-124">因此，您必須確定在專案檔 （如以下程式碼片段所示） 中設定 UserSecretsId 屬性。</span><span class="sxs-lookup"><span data-stu-id="21d90-124">Therefore, you must be sure to set the UserSecretsId property in your project file (as shown in the snippet below).</span></span> <span data-ttu-id="21d90-125">用做為識別碼的實際字串並不重要，只要它是唯一的專案中。</span><span class="sxs-lookup"><span data-stu-id="21d90-125">The actual string used as the ID is not important as long as it is unique in the project.</span></span>

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

<span data-ttu-id="21d90-126">使用儲存在應用程式中使用密碼管理員密碼都會伴隨著呼叫 AddUserSecrets&lt;T&gt; ConfigurationBuilder 執行個體，要在其組態中包含機密資料的應用程式上。</span><span class="sxs-lookup"><span data-stu-id="21d90-126">Using secrets stored with Secret Manager in an application is accomplished by calling AddUserSecrets&lt;T&gt; on the ConfigurationBuilder instance to include secrets for the application in its configuration.</span></span> <span data-ttu-id="21d90-127">泛型參數 T 應該是來自 UserSecretId 已套用至組件的類型。</span><span class="sxs-lookup"><span data-stu-id="21d90-127">The generic parameter T should be a type from the assembly that the UserSecretId was applied to.</span></span> <span data-ttu-id="21d90-128">通常使用 AddUserSecrets&lt;啟動&gt;是正常的。</span><span class="sxs-lookup"><span data-stu-id="21d90-128">Usually using AddUserSecrets&lt;Startup&gt; is fine.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="21d90-129">[上一個](授權-網路-microservices-web-applications.md) [下一步] (azure-金鑰-保存庫-保護-secrets.md)</span><span class="sxs-lookup"><span data-stu-id="21d90-129">[Previous] (authorization-net-microservices-web-applications.md) [Next] (azure-key-vault-protects-secrets.md)</span></span>

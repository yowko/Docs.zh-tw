---
title: 在開發期間安全地儲存應用程式祕密
description: .NET 微服務和 Web 應用程式中的安全性 - 請勿將您的應用程式祕密 (例如密碼、連接字串或 API 金鑰) 儲存在原始檔控制中，請了解您可以在 ASP.NET Core 中使用的選項，尤其是必須了解如何處理「使用者祕密」。
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: fe8e7fa11c9a4f4cae133c2e09f9e4b4dd40a546
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2019
ms.locfileid: "54361985"
---
# <a name="store-application-secrets-safely-during-development"></a><span data-ttu-id="cf81c-103">在開發期間安全地儲存應用程式密碼</span><span class="sxs-lookup"><span data-stu-id="cf81c-103">Store application secrets safely during development</span></span>

<span data-ttu-id="cf81c-104">為了連接到受保護的資源和其他服務，ASP.NET Core 應用程式通常需要使用包含機密資訊的連接字串、密碼或其他認證。</span><span class="sxs-lookup"><span data-stu-id="cf81c-104">To connect with protected resources and other services, ASP.NET Core applications typically need to use connection strings, passwords, or other credentials that contain sensitive information.</span></span> <span data-ttu-id="cf81c-105">這些機密資訊稱為「祕密」。</span><span class="sxs-lookup"><span data-stu-id="cf81c-105">These sensitive pieces of information are called *secrets*.</span></span> <span data-ttu-id="cf81c-106">最佳做法是不要在原始程式碼中包含祕密，而且絕不要在原始檔控制中儲存祕密。</span><span class="sxs-lookup"><span data-stu-id="cf81c-106">It's a best practice to not include secrets in source code and making sure not to store secrets in source control.</span></span> <span data-ttu-id="cf81c-107">相反地，您應該使用 ASP.NET Core 組態模型，從更安全的位置讀取祕密。</span><span class="sxs-lookup"><span data-stu-id="cf81c-107">Instead, you should use the ASP.NET Core configuration model to read the secrets from more secure locations.</span></span>

<span data-ttu-id="cf81c-108">您必須將用於存取開發和暫存資源的祕密，與用於存取生產資源的祕密分開，因為不同的人需要存取不同組的祕密。</span><span class="sxs-lookup"><span data-stu-id="cf81c-108">You must separate the secrets for accessing development and staging resources from the ones used for accessing production resources, because different individuals will need access to those different sets of secrets.</span></span> <span data-ttu-id="cf81c-109">若要儲存在開發期間使用的祕密，常見的方法是將祕密儲存在環境變數中，或藉由使用 ASP.NET Core Secret Manager 工具來儲存。</span><span class="sxs-lookup"><span data-stu-id="cf81c-109">To store secrets used during development, common approaches are to either store secrets in environment variables or by using the ASP.NET Core Secret Manager tool.</span></span> <span data-ttu-id="cf81c-110">為了在生產環境中更安全的儲存，微服務可以將祕密儲存在 Azure Key Vault 中。</span><span class="sxs-lookup"><span data-stu-id="cf81c-110">For more secure storage in production environments, microservices can store secrets in an Azure Key Vault.</span></span>

## <a name="store-secrets-in-environment-variables"></a><span data-ttu-id="cf81c-111">將祕密儲存在環境變數中</span><span class="sxs-lookup"><span data-stu-id="cf81c-111">Store secrets in environment variables</span></span>

<span data-ttu-id="cf81c-112">將祕密與原始程式碼分開保存的一個方法，是由開發人員在其開發電腦上將字串型祕密設定為[環境變數](/aspnet/core/security/app-secrets#environment-variables)。</span><span class="sxs-lookup"><span data-stu-id="cf81c-112">One way to keep secrets out of source code is for developers to set string-based secrets as [environment variables](/aspnet/core/security/app-secrets#environment-variables) on their development machines.</span></span> <span data-ttu-id="cf81c-113">當您使用環境變數來儲存具有階層式名稱的祕密 (例如巢狀於組態區段中) 時，您必須將變數命名以包含其區段的完整階層 (以冒號 (:) 分隔)。</span><span class="sxs-lookup"><span data-stu-id="cf81c-113">When you use environment variables to store secrets with hierarchical names, such as the ones nested in configuration sections, you must name the variables to include the complete hierarchy of its sections, delimited with colons (:).</span></span>

<span data-ttu-id="cf81c-114">例如，將環境變數 `Logging:LogLevel:Default` 設定為 `Debug` 相當於下列 JSON 檔案中的設定值：</span><span class="sxs-lookup"><span data-stu-id="cf81c-114">For example, setting an environment variable `Logging:LogLevel:Default` to `Debug` value would be equivalent to a configuration value from the following JSON file:</span></span>

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

<span data-ttu-id="cf81c-115">若要從環境變數存取這些值，應用程式只需要在建構 IConfigurationRoot 物件時在其 ConfigurationBuilder 上呼叫 AddEnvironmentVariables 即可。</span><span class="sxs-lookup"><span data-stu-id="cf81c-115">To access these values from environment variables, the application just needs to call AddEnvironmentVariables on its ConfigurationBuilder when constructing an IConfigurationRoot object.</span></span>

<span data-ttu-id="cf81c-116">請注意，環境變數通常會儲存為純文字，因此如果電腦或具有環境變數的處理序遭到入侵，就會顯示環境變數值。</span><span class="sxs-lookup"><span data-stu-id="cf81c-116">Note that environment variables are commonly stored as plain text, so if the machine or process with the environment variables is compromised, the environment variable values will be visible.</span></span>

## <a name="store-secrets-with-the-aspnet-core-secret-manager"></a><span data-ttu-id="cf81c-117">使用 ASP.NET Core Secret Manager 儲存祕密</span><span class="sxs-lookup"><span data-stu-id="cf81c-117">Store secrets with the ASP.NET Core Secret Manager</span></span>

<span data-ttu-id="cf81c-118">ASP.NET Core [Secret Manager](/aspnet/core/security/app-secrets#secret-manager) 工具提供另一種方法來將祕密與原始程式碼分開保存。</span><span class="sxs-lookup"><span data-stu-id="cf81c-118">The ASP.NET Core [Secret Manager](/aspnet/core/security/app-secrets#secret-manager) tool provides another method of keeping secrets out of source code.</span></span> <span data-ttu-id="cf81c-119">若要使用 Secret Manager 工具，請在您的專案檔中安裝套件 **Microsoft.Extensions.Configuration.SecretManager**。</span><span class="sxs-lookup"><span data-stu-id="cf81c-119">To use the Secret Manager tool, install the package **Microsoft.Extensions.Configuration.SecretManager** in your project file.</span></span> <span data-ttu-id="cf81c-120">一旦該相依性存在並已還原，即可使用 `dotnet user-secrets` 命令從命令列設定祕密的值。</span><span class="sxs-lookup"><span data-stu-id="cf81c-120">Once that dependency is present and has been restored, the `dotnet user-secrets` command can be used to set the value of secrets from the command line.</span></span> <span data-ttu-id="cf81c-121">這些祕密會儲存在使用者設定檔目錄中的 JSON 檔案中 (細目會因 OS 而異)，並遠離原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="cf81c-121">These secrets will be stored in a JSON file in the user’s profile directory (details vary by OS), away from source code.</span></span>

<span data-ttu-id="cf81c-122">Secret Manager 工具所設定的祕密會依使用祕密之專案的 `UserSecretsId` 屬性來組織。</span><span class="sxs-lookup"><span data-stu-id="cf81c-122">Secrets set by the Secret Manager tool are organized by the `UserSecretsId` property of the project that's using the secrets.</span></span> <span data-ttu-id="cf81c-123">因此，請務必在專案檔中設定 UserSecretsId 屬性，如下列程式碼片段所示。</span><span class="sxs-lookup"><span data-stu-id="cf81c-123">Therefore, you must be sure to set the UserSecretsId property in your project file, as shown in the snippet below.</span></span> <span data-ttu-id="cf81c-124">預設值是 Visual Studio 指派的 GUID，但只要它在您電腦中是唯一的，則實際字串並不重要。</span><span class="sxs-lookup"><span data-stu-id="cf81c-124">The default value is a GUID assigned by Visual Studio, but the actual string is not important as long as it's unique in your computer.</span></span>

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

<span data-ttu-id="cf81c-125">若要使用 Secret Manager 儲存在應用程式中的祕密，請在 ConfigurationBuilder 執行個體上呼叫 `AddUserSecrets<T>` 以在其設定中包含應用程式的祕密。</span><span class="sxs-lookup"><span data-stu-id="cf81c-125">Using secrets stored with Secret Manager in an application is accomplished by calling `AddUserSecrets<T>` on the ConfigurationBuilder instance to include secrets for the application in its configuration.</span></span> <span data-ttu-id="cf81c-126">泛型參數 T 應該是已套用 UserSecretId 之組件的類型。</span><span class="sxs-lookup"><span data-stu-id="cf81c-126">The generic parameter T should be a type from the assembly that the UserSecretId was applied to.</span></span> <span data-ttu-id="cf81c-127">通常，使用 `AddUserSecrets<Startup>` 沒有問題。</span><span class="sxs-lookup"><span data-stu-id="cf81c-127">Usually using `AddUserSecrets<Startup>` is fine.</span></span>

<span data-ttu-id="cf81c-128">在 *Program.cs* 中使用 `CreateDefaultBuilder` 方法時，`AddUserSecrets<Startup>()` 會包含在開發環境的預設選項中。</span><span class="sxs-lookup"><span data-stu-id="cf81c-128">The `AddUserSecrets<Startup>()` is included in the default options for the Development environment when using the `CreateDefaultBuilder` method in *Program.cs*.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="cf81c-129">[上一頁](authorization-net-microservices-web-applications.md)
>[下一頁](azure-key-vault-protects-secrets.md)</span><span class="sxs-lookup"><span data-stu-id="cf81c-129">[Previous](authorization-net-microservices-web-applications.md)
[Next](azure-key-vault-protects-secrets.md)</span></span>

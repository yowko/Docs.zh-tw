---
title: 瞭解適用于 .NET 的 Azure 程式庫中的驗證
description: 說明使用 Azure SDK for .NET 進行驗證的不同方式。
ms.date: 06/19/2020
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: 5ed29d5485dc7f59bcc757c8903116edf6bd5d7d
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174916"
---
# <a name="authenticate-with-the-azure-sdk-for-net"></a><span data-ttu-id="4a913-103">使用 Azure SDK for .NET 進行驗證</span><span class="sxs-lookup"><span data-stu-id="4a913-103">Authenticate with the Azure SDK for .NET</span></span>

## <a name="recommended-azureidentity"></a><span data-ttu-id="4a913-104">建議： Azure。身分識別</span><span class="sxs-lookup"><span data-stu-id="4a913-104">Recommended: Azure.Identity</span></span>

<span data-ttu-id="4a913-105">Azure SDK for .NET 中的最新套件會使用一般驗證套件來進行驗證 `Azure.Identity` 。</span><span class="sxs-lookup"><span data-stu-id="4a913-105">The latest packages in the Azure SDK for .NET use a common authentication package to authenticate, `Azure.Identity`.</span></span> <span data-ttu-id="4a913-106">`Azure.Identity`建議使用，而不是本檔稍後所述的其他驗證機制。</span><span class="sxs-lookup"><span data-stu-id="4a913-106">Using `Azure.Identity` is recommended over other authentication mechanisms described later in this document.</span></span> <span data-ttu-id="4a913-107">支援所提供認證的套件， `Azure.Identity` 具有從 Azure 開始的套件識別碼 *。*</span><span class="sxs-lookup"><span data-stu-id="4a913-107">Packages supporting the credentials provided by `Azure.Identity` have package identifiers starting with *Azure.*</span></span> <span data-ttu-id="4a913-108">[如需詳細資訊，請參閱 AZURE SDK For .net 中的最新版本](https://azure.github.io/azure-sdk/releases/latest/index.html#net)。</span><span class="sxs-lookup"><span data-stu-id="4a913-108">[For more information, see the latest releases in the Azure SDK for .NET](https://azure.github.io/azure-sdk/releases/latest/index.html#net).</span></span>

<span data-ttu-id="4a913-109">如需在專案中使用的完整指示 `Azure.Identity` ，請參閱適用[于 .Net 的 Azure 身分識別用戶端](/dotnet/api/overview/azure/identity-readme)檔。</span><span class="sxs-lookup"><span data-stu-id="4a913-109">For complete instructions on using `Azure.Identity` in your project, see the documentation for [Azure Identity client for .NET](/dotnet/api/overview/azure/identity-readme).</span></span>

> [!TIP]
> <span data-ttu-id="4a913-110">如需使用 Azure 身分識別來管理和存取 Azure 資源的範例，請參閱[azure 身分識別、資源管理和儲存體範例](/samples/dotnet/samples/azure-identity-resource-management-storage/)。</span><span class="sxs-lookup"><span data-stu-id="4a913-110">See the [Azure Identity, Resource Management, and Storage sample](/samples/dotnet/samples/azure-identity-resource-management-storage/) for examples of using Azure Identity to manage and access Azure resources.</span></span>

<span data-ttu-id="4a913-111">若要向不支援 Azure 身分識別的程式庫進行驗證，請參閱本主題的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="4a913-111">To authenticate with libraries that don't support Azure.Identity, see the rest of this topic.</span></span>

## <a name="access-azure-resources"></a><span data-ttu-id="4a913-112">存取 Azure 資源</span><span class="sxs-lookup"><span data-stu-id="4a913-112">Access Azure resources</span></span>

<span data-ttu-id="4a913-113">若要與 Azure 資源互動，例如從 Key Vault 中抓取秘密，或在儲存體中儲存 blob，許多 Azure 服務程式庫都需要連接字串或金鑰來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="4a913-113">To interact with Azure resources, such as retrieving a secret from Key Vault or storing a blob in Storage, many Azure service libraries require a connection string or keys for authentication.</span></span> <span data-ttu-id="4a913-114">例如，SQL Database 使用標準的[SQL 連接字串](https://docs.microsoft.com/azure/azure-sql/database/connect-query-dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="4a913-114">For example, SQL Database uses a [standard SQL connection string](https://docs.microsoft.com/azure/azure-sql/database/connect-query-dotnet-core).</span></span> <span data-ttu-id="4a913-115">服務連接字串會在其他 Azure 服務中使用，例如[CosmosDB](/azure/cosmos-db/)、 [Azure Cache for Redis](/azure/azure-cache-for-redis/cache-dotnet-how-to-use-azure-redis-cache)和[服務匯流排](/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues)。</span><span class="sxs-lookup"><span data-stu-id="4a913-115">Service connection strings are used in other Azure services like [CosmosDB](/azure/cosmos-db/), [Azure Cache for Redis](/azure/azure-cache-for-redis/cache-dotnet-how-to-use-azure-redis-cache), and [Service Bus](/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues).</span></span> <span data-ttu-id="4a913-116">您可以使用 Azure 入口網站、CLI 或 PowerShell 來取得這些字串。</span><span class="sxs-lookup"><span data-stu-id="4a913-116">You can get those strings using the Azure portal, CLI, or PowerShell.</span></span> <span data-ttu-id="4a913-117">您也可以使用適用於 .NET 的 Azure 管理程式庫來查詢資源，從而在程式碼中建置連接字串。</span><span class="sxs-lookup"><span data-stu-id="4a913-117">You can also use the Azure management libraries for .NET to query resources to build connection strings in your code.</span></span>

<span data-ttu-id="4a913-118">使用連接字串的方法會因產品而異。</span><span class="sxs-lookup"><span data-stu-id="4a913-118">The methods for using a connection string vary by product.</span></span> <span data-ttu-id="4a913-119">[請參閱 Azure 產品的檔](/azure/?product=featured)。</span><span class="sxs-lookup"><span data-stu-id="4a913-119">[Refer to the documentation for your Azure product](/azure/?product=featured).</span></span>

## <a name="manage-azure-resources"></a><span data-ttu-id="4a913-120">管理 Azure 資源</span><span class="sxs-lookup"><span data-stu-id="4a913-120">Manage Azure resources</span></span>

[!include[Create service principal](includes/create-sp.md)]

<span data-ttu-id="4a913-121">現在您已建立服務主體，有兩個選項可用來驗證服務主體，從而建立和管理資源。</span><span class="sxs-lookup"><span data-stu-id="4a913-121">Now that the service principal is created, two options are available to authenticate to the service principal to create and manage resources.</span></span>

<span data-ttu-id="4a913-122">針對這兩個選項，您必須將下列 NuGet 套件新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="4a913-122">For both options you will need to add the following NuGet packages to your project.</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Fluent
Install-Package Microsoft.Azure.Management.ResourceManager.Fluent
```

### <a name="authenticate-with-token-credentials"></a><span data-ttu-id="4a913-123">使用權杖認證進行驗證</span><span class="sxs-lookup"><span data-stu-id="4a913-123">Authenticate with token credentials</span></span>

<span data-ttu-id="4a913-124">第一個方法是在程式碼中建置權杖認證物件。</span><span class="sxs-lookup"><span data-stu-id="4a913-124">The first method is to build the token credential object in code.</span></span> <span data-ttu-id="4a913-125">您應該在組態檔、登錄或 Azure Key Vault 中安全地儲存認證。</span><span class="sxs-lookup"><span data-stu-id="4a913-125">You should store the credentials securely in a configuration file, the registry, or Azure KeyVault.</span></span>

```csharp
var credentials = SdkContext.AzureCredentialsFactory
    .FromServicePrincipal(clientId,
        clientSecret,
        tenantId,
        AzureEnvironment.AzureGlobalCloud);
```

<span data-ttu-id="4a913-126">使用 *clientId*、*clientSecret*和 *tenantId* 等值，這些值來自已建立服務主體處的 JSON 輸出。</span><span class="sxs-lookup"><span data-stu-id="4a913-126">Use the *clientId*, *clientSecret*, and *tenantId* values from the JSON output when you created the service principal.</span></span>

<span data-ttu-id="4a913-127">然後，建立進入點 `Azure` 物件來開始使用 API：</span><span class="sxs-lookup"><span data-stu-id="4a913-127">Then create the entry point `Azure` object to start working with the API:</span></span>

```csharp
var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```

### <a name="file-based-authentication"></a><a name="mgmt-file"></a><span data-ttu-id="4a913-128">以檔案作為基礎的驗證</span><span class="sxs-lookup"><span data-stu-id="4a913-128">File-based authentication</span></span>

<span data-ttu-id="4a913-129">以檔案作為基礎的驗證可讓您將服務主體認證放在純文字檔案，並在檔案系統內加以保護。</span><span class="sxs-lookup"><span data-stu-id="4a913-129">File-based authentication allows you to put the service principal credentials in a plain text file and secure it within the file system.</span></span>

[!include[File-based authentication](includes/file-based-auth.md)]

<span data-ttu-id="4a913-130">讀取檔案的內容，並建立進入點 `Azure` 物件來開始使用 API：</span><span class="sxs-lookup"><span data-stu-id="4a913-130">Read the contents of the file and create the entry point `Azure` object to start working with the API:</span></span>

```csharp
// pull in the location of the authentication properties file from the environment
var credentials = SdkContext.AzureCredentialsFactory
    .FromFile(Environment.GetEnvironmentVariable("AZURE_AUTH_LOCATION"));

var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```

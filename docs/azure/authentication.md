---
title: 瞭解適用于 .NET 的 Azure 程式庫中的驗證
description: 說明使用 Azure SDK for .NET 進行驗證的不同方式。
ms.date: 06/19/2020
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: dbae72eb9e80801d7338b210f9664f1c4e318ae0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539173"
---
# <a name="authenticate-with-the-azure-sdk-for-net"></a><span data-ttu-id="caf41-103">使用 Azure SDK for .NET 進行驗證</span><span class="sxs-lookup"><span data-stu-id="caf41-103">Authenticate with the Azure SDK for .NET</span></span>

## <a name="recommended-azureidentity"></a><span data-ttu-id="caf41-104">建議： Azure 身分識別</span><span class="sxs-lookup"><span data-stu-id="caf41-104">Recommended: Azure.Identity</span></span>

<span data-ttu-id="caf41-105">Azure SDK for .NET 中的最新套件使用一般驗證套件來進行驗證 `Azure.Identity` 。</span><span class="sxs-lookup"><span data-stu-id="caf41-105">The latest packages in the Azure SDK for .NET use a common authentication package to authenticate, `Azure.Identity`.</span></span> <span data-ttu-id="caf41-106">`Azure.Identity`建議您不要使用本檔稍後所述的其他驗證機制。</span><span class="sxs-lookup"><span data-stu-id="caf41-106">Using `Azure.Identity` is recommended over other authentication mechanisms described later in this document.</span></span> <span data-ttu-id="caf41-107">支援所提供之認證的套件 `Azure.Identity` 建置於之上 `Azure.Core` ，並具有從 *Azure*開始的套件識別碼。</span><span class="sxs-lookup"><span data-stu-id="caf41-107">Packages supporting the credentials provided by `Azure.Identity` are built on top of `Azure.Core` and have package identifiers starting with *Azure*.</span></span> <span data-ttu-id="caf41-108">[請參閱套件清單](packages.md) ，以取得使用的封裝清查 `Azure.Core` 。</span><span class="sxs-lookup"><span data-stu-id="caf41-108">[See the package list](packages.md) for an inventory of packages that use `Azure.Core`.</span></span>

<span data-ttu-id="caf41-109">如需在專案中使用的完整指示 `Azure.Identity` ，請參閱適用于 [.Net 的 Azure 身分識別用戶端](/dotnet/api/overview/azure/identity-readme)檔。</span><span class="sxs-lookup"><span data-stu-id="caf41-109">For complete instructions on using `Azure.Identity` in your project, see the documentation for [Azure Identity client for .NET](/dotnet/api/overview/azure/identity-readme).</span></span>

> [!TIP]
> <span data-ttu-id="caf41-110">如需使用 Azure 身分識別來管理和存取 Azure 資源的範例，請參閱 [azure 身分識別、資源管理和儲存體範例](/samples/dotnet/samples/azure-identity-resource-management-storage/) 。</span><span class="sxs-lookup"><span data-stu-id="caf41-110">See the [Azure Identity, Resource Management, and Storage sample](/samples/dotnet/samples/azure-identity-resource-management-storage/) for examples of using Azure Identity to manage and access Azure resources.</span></span>

<span data-ttu-id="caf41-111">若要使用不支援 Azure 的程式庫進行驗證，請參閱本主題的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="caf41-111">To authenticate with libraries that don't support Azure.Identity, see the rest of this topic.</span></span>

## <a name="access-azure-resources"></a><span data-ttu-id="caf41-112">存取 Azure 資源</span><span class="sxs-lookup"><span data-stu-id="caf41-112">Access Azure resources</span></span>

<span data-ttu-id="caf41-113">若要與 Azure 資源互動，例如從 Key Vault 取出秘密或將 blob 儲存在儲存體中，許多 Azure 服務程式庫都需要連接字串或金鑰來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="caf41-113">To interact with Azure resources, such as retrieving a secret from Key Vault or storing a blob in Storage, many Azure service libraries require a connection string or keys for authentication.</span></span> <span data-ttu-id="caf41-114">例如，SQL Database 會使用 [標準的 SQL 連接字串](/azure/azure-sql/database/connect-query-dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="caf41-114">For example, SQL Database uses a [standard SQL connection string](/azure/azure-sql/database/connect-query-dotnet-core).</span></span> <span data-ttu-id="caf41-115">服務連接字串會在其他 Azure 服務中使用，例如 [CosmosDB](/azure/cosmos-db/)、 [Azure Cache for Redis](/azure/azure-cache-for-redis/cache-dotnet-how-to-use-azure-redis-cache)和 [服務匯流排](/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues)。</span><span class="sxs-lookup"><span data-stu-id="caf41-115">Service connection strings are used in other Azure services like [CosmosDB](/azure/cosmos-db/), [Azure Cache for Redis](/azure/azure-cache-for-redis/cache-dotnet-how-to-use-azure-redis-cache), and [Service Bus](/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues).</span></span> <span data-ttu-id="caf41-116">您可以使用 Azure 入口網站、CLI 或 PowerShell 來取得這些字串。</span><span class="sxs-lookup"><span data-stu-id="caf41-116">You can get those strings using the Azure portal, CLI, or PowerShell.</span></span> <span data-ttu-id="caf41-117">您也可以使用適用於 .NET 的 Azure 管理程式庫來查詢資源，從而在程式碼中建置連接字串。</span><span class="sxs-lookup"><span data-stu-id="caf41-117">You can also use the Azure management libraries for .NET to query resources to build connection strings in your code.</span></span>

<span data-ttu-id="caf41-118">使用連接字串的方法會因產品而異。</span><span class="sxs-lookup"><span data-stu-id="caf41-118">The methods for using a connection string vary by product.</span></span> <span data-ttu-id="caf41-119">[請參閱您 Azure 產品的檔](/azure/?product=featured)。</span><span class="sxs-lookup"><span data-stu-id="caf41-119">[Refer to the documentation for your Azure product](/azure/?product=featured).</span></span>

## <a name="manage-azure-resources"></a><span data-ttu-id="caf41-120">管理 Azure 資源</span><span class="sxs-lookup"><span data-stu-id="caf41-120">Manage Azure resources</span></span>

[!include[Create service principal](includes/create-sp.md)]

<span data-ttu-id="caf41-121">現在您已建立服務主體，有兩個選項可用來驗證服務主體，從而建立和管理資源。</span><span class="sxs-lookup"><span data-stu-id="caf41-121">Now that the service principal is created, two options are available to authenticate to the service principal to create and manage resources.</span></span>

<span data-ttu-id="caf41-122">針對這兩個選項，您必須將下列 NuGet 套件新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="caf41-122">For both options you will need to add the following NuGet packages to your project.</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Fluent
Install-Package Microsoft.Azure.Management.ResourceManager.Fluent
```

### <a name="authenticate-with-token-credentials"></a><span data-ttu-id="caf41-123">使用權杖認證進行驗證</span><span class="sxs-lookup"><span data-stu-id="caf41-123">Authenticate with token credentials</span></span>

<span data-ttu-id="caf41-124">第一個方法是在程式碼中建置權杖認證物件。</span><span class="sxs-lookup"><span data-stu-id="caf41-124">The first method is to build the token credential object in code.</span></span> <span data-ttu-id="caf41-125">您應該在組態檔、登錄或 Azure Key Vault 中安全地儲存認證。</span><span class="sxs-lookup"><span data-stu-id="caf41-125">You should store the credentials securely in a configuration file, the registry, or Azure KeyVault.</span></span>

```csharp
var credentials = SdkContext.AzureCredentialsFactory
    .FromServicePrincipal(clientId,
        clientSecret,
        tenantId,
        AzureEnvironment.AzureGlobalCloud);
```

<span data-ttu-id="caf41-126">使用 *clientId*、*clientSecret*和 *tenantId* 等值，這些值來自已建立服務主體處的 JSON 輸出。</span><span class="sxs-lookup"><span data-stu-id="caf41-126">Use the *clientId*, *clientSecret*, and *tenantId* values from the JSON output when you created the service principal.</span></span>

<span data-ttu-id="caf41-127">然後，建立進入點 `Azure` 物件來開始使用 API：</span><span class="sxs-lookup"><span data-stu-id="caf41-127">Then create the entry point `Azure` object to start working with the API:</span></span>

```csharp
var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```

<span data-ttu-id="caf41-128">建議您明確地將 *subscriptionId* 從 JSON 輸出提供給 `Azure` 物件：</span><span class="sxs-lookup"><span data-stu-id="caf41-128">It is recommended that you explicitly provide the *subscriptionId* from the JSON output to the `Azure` object:</span></span>

```csharp
var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithSubscription(subscriptionId);
```

### <a name="file-based-authentication"></a><a name="mgmt-file"></a><span data-ttu-id="caf41-129">以檔案作為基礎的驗證</span><span class="sxs-lookup"><span data-stu-id="caf41-129">File-based authentication</span></span>

<span data-ttu-id="caf41-130">以檔案作為基礎的驗證可讓您將服務主體認證放在純文字檔案，並在檔案系統內加以保護。</span><span class="sxs-lookup"><span data-stu-id="caf41-130">File-based authentication allows you to put the service principal credentials in a plain text file and secure it within the file system.</span></span>

[!include[File-based authentication](includes/file-based-auth.md)]

<span data-ttu-id="caf41-131">讀取檔案的內容，並建立進入點 `Azure` 物件來開始使用 API：</span><span class="sxs-lookup"><span data-stu-id="caf41-131">Read the contents of the file and create the entry point `Azure` object to start working with the API:</span></span>

```csharp
// pull in the location of the authentication properties file from the environment
var credentials = SdkContext.AzureCredentialsFactory
    .FromFile(Environment.GetEnvironmentVariable("AZURE_AUTH_LOCATION"));

var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```

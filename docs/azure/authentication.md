---
title: 瞭解適用于 .NET 的 Azure 程式庫中的驗證
description: 說明使用 Azure SDK for .NET 進行驗證的不同方式。
ms.date: 06/19/2020
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: e588499a789fc5e7da7eb51009f97090ca75e562
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916610"
---
# <a name="authenticate-with-the-azure-sdk-for-net"></a>使用 Azure SDK for .NET 進行驗證

## <a name="recommended-azureidentity"></a>建議： Azure。身分識別

Azure SDK for .NET 中的最新套件會使用一般驗證套件來進行驗證 `Azure.Identity` 。 `Azure.Identity`建議使用，而不是本檔稍後所述的其他驗證機制。 支援所提供認證的封裝 `Azure.Identity` 建置於之上 `Azure.Core` ，並具有從 Azure 開始的套件識別碼 *。* 如需使用之套件的清查，[請參閱封裝清單](packages.md) `Azure.Core` 。

如需在專案中使用的完整指示 `Azure.Identity` ，請參閱適用[于 .Net 的 Azure 身分識別用戶端](/dotnet/api/overview/azure/identity-readme)檔。

> [!TIP]
> 如需使用 Azure 身分識別來管理和存取 Azure 資源的範例，請參閱[azure 身分識別、資源管理和儲存體範例](/samples/dotnet/samples/azure-identity-resource-management-storage/)。

若要向不支援 Azure 身分識別的程式庫進行驗證，請參閱本主題的其餘部分。

## <a name="access-azure-resources"></a>存取 Azure 資源

若要與 Azure 資源互動，例如從 Key Vault 中抓取秘密，或在儲存體中儲存 blob，許多 Azure 服務程式庫都需要連接字串或金鑰來進行驗證。 例如，SQL Database 使用標準的[SQL 連接字串](https://docs.microsoft.com/azure/azure-sql/database/connect-query-dotnet-core)。 服務連接字串會在其他 Azure 服務中使用，例如[CosmosDB](/azure/cosmos-db/)、 [Azure Cache for Redis](/azure/azure-cache-for-redis/cache-dotnet-how-to-use-azure-redis-cache)和[服務匯流排](/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues)。 您可以使用 Azure 入口網站、CLI 或 PowerShell 來取得這些字串。 您也可以使用適用於 .NET 的 Azure 管理程式庫來查詢資源，從而在程式碼中建置連接字串。

使用連接字串的方法會因產品而異。 [請參閱 Azure 產品的檔](/azure/?product=featured)。

## <a name="manage-azure-resources"></a>管理 Azure 資源

[!include[Create service principal](includes/create-sp.md)]

現在您已建立服務主體，有兩個選項可用來驗證服務主體，從而建立和管理資源。

針對這兩個選項，您必須將下列 NuGet 套件新增至您的專案。

```powershell
Install-Package Microsoft.Azure.Management.Fluent
Install-Package Microsoft.Azure.Management.ResourceManager.Fluent
```

### <a name="authenticate-with-token-credentials"></a>使用權杖認證進行驗證

第一個方法是在程式碼中建置權杖認證物件。 您應該在組態檔、登錄或 Azure Key Vault 中安全地儲存認證。

```csharp
var credentials = SdkContext.AzureCredentialsFactory
    .FromServicePrincipal(clientId,
        clientSecret,
        tenantId,
        AzureEnvironment.AzureGlobalCloud);
```

使用 *clientId*、*clientSecret*和 *tenantId* 等值，這些值來自已建立服務主體處的 JSON 輸出。

然後，建立進入點 `Azure` 物件來開始使用 API：

```csharp
var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```

建議您明確地從 JSON 輸出提供*subscriptionId*給 `Azure` 物件：

```csharp
var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithSubscription(subscriptionId);
```

### <a name="file-based-authentication"></a><a name="mgmt-file"></a>以檔案作為基礎的驗證

以檔案作為基礎的驗證可讓您將服務主體認證放在純文字檔案，並在檔案系統內加以保護。

[!include[File-based authentication](includes/file-based-auth.md)]

讀取檔案的內容，並建立進入點 `Azure` 物件來開始使用 API：

```csharp
// pull in the location of the authentication properties file from the environment
var credentials = SdkContext.AzureCredentialsFactory
    .FromFile(Environment.GetEnvironmentVariable("AZURE_AUTH_LOCATION"));

var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```

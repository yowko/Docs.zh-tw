---
title: 使用 F# 開始使用 Azure 資料表儲存體
description: 使用 Azure 資料表儲存體或 Azure Cosmos DB 將結構化資料儲存在雲端。
author: sylvanc
ms.date: 03/26/2018
ms.openlocfilehash: 23f5e40e1d9b3d5a0ee27d675362930ef86e90c5
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2020
ms.locfileid: "75935579"
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a>開始使用 Azure 資料表儲存體和使用 F\# 的 Azure Cosmos DB 資料表 API

Azure 表格儲存體是可將結構化的 NoSQL 資料儲存在雲端中的服務。 表格儲存體是具有無結構描述設計的索引鍵/屬性存放區。 由於表格儲存體並無結構描述，因此可輕易隨著應用程式發展需求改寫資料。 所有類型的應用程式都可以用快速且具成本效益的方式存取資料。 相較於類似資料量的傳統 SQL，資料表儲存體通常可大幅降低成本。

您可以使用表格儲存體來儲存具彈性的資料集，例如 Web 應用程式的使用者資料、通訊錄、裝置資訊，以及服務所需的任何其他中繼資料類型。 您可以在資料表中儲存任意數目的實體，且儲存體帳戶可包含任意數目的資料表，最高可達儲存體帳戶的容量限制。

Azure Cosmos DB 提供針對 Azure 資料表儲存體所撰寫，而且需要高階功能的應用程式資料表 API，例如：

- 周全的全域發佈。
- 全球專用的輸送量。
- 99 百分位數的單一數字毫秒延遲。
- 保證高可用性。
- 自動次要索引。

針對 Azure 資料表儲存體所撰寫的應用程式可使用資料表 API (不變更程式碼) 來移轉至 Azure Cosmos DB，並且利用進階功能。 資料表 API 具有適用於 .NET、Java、Python 和 Node.js 的用戶端 SDK。

如需詳細資訊，請參閱[Azure Cosmos DB 資料表 API 簡介](https://docs.microsoft.com/azure/cosmos-db/table-introduction)。

## <a name="about-this-tutorial"></a>關於本教學課程

本教學課程說明如何使用F# Azure 資料表儲存體或 Azure Cosmos DB 資料表 API 來撰寫程式碼來執行一些常見的工作，包括建立和刪除資料表，以及插入、更新、刪除和查詢資料表資料。

## <a name="prerequisites"></a>必要條件：

若要使用本指南，您必須先[建立 Azure 儲存體帳戶](/azure/storage/storage-create-storage-account)或[Azure Cosmos DB 帳戶](https://azure.microsoft.com/try/cosmosdb/)。

## <a name="create-an-f-script-and-start-f-interactive"></a>建立F#腳本並啟動F#互動式

本文中的範例可用於F#應用程式或F#腳本中。 若要建立F#腳本，請在您F#的開發環境中建立具有 `.fsx` 副檔名的檔案，例如 `tables.fsx`。

接下來，使用[套件管理員](package-management.md)（例如[Paket](https://fsprojects.github.io/Paket/)或[NuGet](https://www.nuget.org/) ），在您的腳本中使用 `#r` 指示詞來安裝 `WindowsAzure.Storage` 封裝和參考 `WindowsAzure.Storage.dll`。 再次針對 `Microsoft.WindowsAzure.ConfigurationManager` 執行此動作，以取得 Microsoft Azure 命名空間。

### <a name="add-namespace-declarations"></a>加入命名空間宣告

在 `tables.fsx` 檔案頂端新增下列 `open` 陳述式：

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a>取得您的 Azure 儲存體連接字串

如果您要連接到 Azure 儲存體表格服務，您將需要此教學課程的連接字串。 您可以從 Azure 入口網站複製連接字串。 如需連接字串的詳細資訊，請參閱[設定儲存體連接字串](/azure/storage/storage-configure-connection-string)。

### <a name="get-your-azure-cosmos-db-connection-string"></a>取得您的 Azure Cosmos DB 連接字串

如果您要連接到 Azure Cosmos DB，在本教學課程中需要連接字串。 您可以從 Azure 入口網站複製連接字串。 在 Azure 入口網站的 Cosmos DB 帳戶中，移至 [**設定**] > [**連接字串**]，然後按一下 [**複製**] 按鈕以複製主要連接字串。

在本教學課程中，請在腳本中輸入您的連接字串，如下列範例所示：

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

不過，這**不建議**用於實際的專案。 儲存體帳戶金鑰很類似儲存體帳戶的根密碼。 請務必小心保護您的儲存體帳戶金鑰。 請避免轉發給其他使用者、進行硬式編碼，或將它儲存在其他人可以存取的純文字檔案。 如果您認為金鑰可能遭到入侵，您可以使用 Azure 入口網站重新產生金鑰。

對於實際的應用程式而言，維護儲存體連接字串的最佳方式是在設定檔中。 若要從設定檔提取連接字串，您可以執行下列動作：

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

是否使用 Azure Configuration Manager 可由您選擇。 您也可以使用 API，例如 .NET Framework 的 `ConfigurationManager` 類型。

### <a name="parse-the-connection-string"></a>解析連接字串

若要剖析連接字串，請使用：

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

這會傳回 `CloudStorageAccount`。

### <a name="create-the-table-service-client"></a>建立表格服務用戶端

`CloudTableClient` 類別可讓您取得資料表儲存體中的資料表和實體。 以下是建立服務用戶端的其中一種方式：

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

您現在可以開始撰寫程式碼，以讀取表格儲存體的資料並將資料寫入其中。

### <a name="create-a-table"></a>建立資料表

此範例說明如何建立尚不存在的資料表：

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a>將實體新增至資料表

實體必須具有繼承自 `TableEntity`的類型。 您可以用您喜歡的任何方式擴充 `TableEntity`，但您的型別*必須*具有無參數的函式。 只有具有 `get` 和 `set` 的屬性會儲存在您的 Azure 資料表中。

實體的資料分割和資料列索引鍵可唯一識別資料表中的實體。 查詢具有相同分割區索引鍵的實體，其速度快於查詢具有不同分割區索引鍵的實體，但使用不同的資料分割索引鍵可提供更佳的延展性或平行作業。

以下是使用 `lastName` 做為資料分割索引鍵，而 `firstName` 做為資料列索引鍵之 `Customer` 的範例。

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

現在，將 `Customer` 加入至資料表。 若要這麼做，請建立在資料表上執行的 `TableOperation`。 在此情況下，您會建立 `Insert` 作業。

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

### <a name="insert-a-batch-of-entities"></a>插入一批實體

您可以使用單一寫入作業，將一批實體插入資料表。 批次作業可讓您將作業結合成單一執行，但有一些限制：

- 您可以在相同的批次作業中執行更新、刪除和插入。
- 批次作業最多可包含100個實體。
- 批次作業中的所有實體都必須具有相同的分割區索引鍵。
- 雖然您可以在批次作業中執行查詢，但它必須是批次中唯一的作業。

以下的一些程式碼會將兩個插入組合成一個批次作業：

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

### <a name="retrieve-all-entities-in-a-partition"></a>擷取資料分割中的所有實體

若要向資料表查詢資料分割中的所有實體，請使用 `TableQuery` 物件。 在這裡，您會篩選 "Smith" 為分割區索引鍵的實體。

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

您現在會列印結果：

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]

### <a name="retrieve-a-range-of-entities-in-a-partition"></a>擷取資料分割中某個範圍的實體

如果您不想要查詢資料分割中的所有實體，可結合資料分割索引鍵篩選器與資料列索引鍵篩選器來指定範圍。 在這裡，您會使用兩個篩選器來取得 "Smith" 資料分割中的所有實體，其中的資料列索引鍵（名字）是以字母前面的 "M" 開頭。

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

您現在會列印結果：

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a>擷取單一實體

您可以撰寫查詢來擷取單一特定實體。 在這裡，您會使用 `TableOperation` 來指定客戶 "Ben Smith"。 而不是集合，您會取回 `Customer`。 在查詢中同時指定資料分割索引鍵和資料列索引鍵，是從表格服務取得單一實體的最快方式。

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

您現在會列印結果：

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]

### <a name="replace-an-entity"></a>取代實體

若要更新實體，請從表格服務取出它、修改實體物件，然後使用 `Replace` 作業將變更儲存回表格服務。 這會導致在伺服器上完全取代實體，除非伺服器上的實體自抓取以來已變更，在這種情況下，作業會失敗。 此失敗是為了防止您的應用程式不小心覆寫其他來源的變更。

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a>插入或取代實體

有時候，您不知道實體是否存在於資料表中。 如果有的話，就不再需要儲存在其中的目前值。 您可以使用 `InsertOrReplace` 來建立實體，或將它取代（如果存在的話）（不論其狀態為何）。

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a>查詢實體屬性的子集

資料表查詢可以只從實體中抓取幾個屬性，而不是所有的屬性。 這項稱為「投射」的技術可以改善查詢效能，特別是針對大型實體。 在這裡，您只會傳回使用 `DynamicTableEntity` 和 `EntityResolver`的電子郵件地址。 請注意在本機儲存體模擬器上並不支援投影，因此此程式碼只有在資料表服務上使用帳戶時才會執行。

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L147-L158)]

### <a name="retrieve-entities-in-pages-asynchronously"></a>以非同步方式擷取頁面中的實體

如果您要讀取大量實體，而您想要在抓取時處理它們，而不是等待它們全部傳回，您可以使用分段的查詢。 在這裡，您會使用非同步工作流程，在頁面中傳回結果，如此當您等候一組大型結果傳回時，執行就不會遭到封鎖。

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L163-L178)]

您現在會同步執行此計算：

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L180-L180)]

### <a name="delete-an-entity"></a>刪除實體

您可以在抓取實體之後將其刪除。 就像更新實體一樣，如果實體在您抓取之後已經變更，這就會失敗。

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L186-L187)]

### <a name="delete-a-table"></a>刪除資料表

您可以從儲存體帳戶刪除資料表。 已刪除的資料表在刪除後一段時間內，將無法重新建立。

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L193-L193)]

## <a name="next-steps"></a>後續步驟

既然您已瞭解資料表儲存體的基本概念，請遵循下列連結以瞭解更複雜的儲存工作和 Azure Cosmos DB 的資料表 API。

- [Azure Cosmos DB 資料表 API 簡介](https://docs.microsoft.com/azure/cosmos-db/table-introduction)
- [Storage Client Library for .NET 參考資料](https://docs.microsoft.com/dotnet/api/overview/azure/storage)
- [Azure 儲存體型別提供者](https://fsprojects.github.io/AzureStorageTypeProvider/)
- [Azure 儲存體團隊部落格](https://docs.microsoft.com/archive/blogs/windowsazurestorage/)
- [設定連接字串](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)

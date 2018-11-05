---
title: 開始使用 Azure 資料表儲存體使用 F#
description: 使用 Azure 資料表儲存體或 Azure Cosmos DB 在雲端中儲存結構化的資料。
author: sylvanc
ms.date: 03/26/2018
ms.openlocfilehash: 2d793ba8653833ff384f1824e303b08e05aba69b
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "43519531"
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a>開始使用 Azure 資料表儲存體和 Azure Cosmos DB 資料表 API 使用 F# # 

Azure 資料表儲存體是一項服務，將結構化的 NoSQL 資料儲存在雲端中。 資料表儲存體是具有無結構描述設計的索引鍵/屬性存放區。 資料表儲存體沒有結構描述，因為很容易就能隨著應用程式發展需求改寫資料。 快速且符合成本效益的所有類型的應用程式資料的存取。 資料表儲存體通常是大幅降低成本比傳統 SQL 類似的磁碟區的資料。

您可以使用資料表儲存體來儲存具彈性的資料集，例如 web 應用程式、 通訊錄、 裝置的詳細資訊和任何其他類型的服務所需的中繼資料的使用者資料。 您可以在資料表中，儲存任意數目的實體和儲存體帳戶可能包含任意數目的資料表，最大容量限制的儲存體帳戶。

Azure Cosmos DB 會提供資料表 API 應用程式，會寫入 Azure 表格儲存體及所需要進階功能，例如：

- 周全的全域散發。
- 全球有專用的輸送量。
- 99 百分位數的個位數毫秒延遲。
- 保證高可用性。
- 自動的次要索引。

針對 Azure 資料表儲存體所撰寫的應用程式可以使用資料表 API 不必變更程式碼移轉至 Azure Cosmos DB，並利用進階功能。 「 資料表 API 具有.NET、 Java、 Python 和 Node.js 用戶端 Sdk 提供。

如需詳細資訊，請參閱 < [Azure Cosmos DB 資料表 API 簡介](https://docs.microsoft.com/azure/cosmos-db/table-introduction)。

## <a name="about-this-tutorial"></a>關於本教學課程

本教學課程會示範如何撰寫 F# 程式碼來執行一些常見的工作，使用 Azure 資料表儲存體或 Azure Cosmos DB 資料表 API，包括建立和刪除資料表並插入、 更新、 刪除和查詢資料表資料。

## <a name="prerequisites"></a>必要條件

若要使用本指南，您必須先[建立 Azure 儲存體帳戶](/azure/storage/storage-create-storage-account)或是[Azure Cosmos DB 帳戶](https://azure.microsoft.com/try/cosmosdb/)。


## <a name="create-an-f-script-and-start-f-interactive"></a>建立 F# 指令碼，並開始 F# Interactive

這篇文章中的範例可以用於 F# 應用程式或 F# 指令碼。 若要建立 F# 指令碼，建立的檔案`.fsx`擴充功能，例如`tables.fsx`，F# 開發環境中。

接下來，使用[套件管理員](package-management.md)這類[Paket](https://fsprojects.github.io/Paket/)或是[NuGet](https://www.nuget.org/)安裝`WindowsAzure.Storage`封裝和參考`WindowsAzure.Storage.dll`使用指令碼中`#r`指示詞。 請勿重新`Microsoft.WindowsAzure.ConfigurationManager`才能取得 Microsoft.Azure 命名空間。

### <a name="add-namespace-declarations"></a>加入命名空間宣告

新增下列`open`陳述式的`tables.fsx`檔案：

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a>取得 Azure 儲存體連接字串

如果您要連線到 Azure 儲存體表格服務，您必須將連接字串在本教學課程。 您可以從 Azure 入口網站複製您的連接字串。 如需有關連接字串的詳細資訊，請參閱 <<c0> [ 設定儲存體連接字串](/azure/storage/storage-configure-connection-string)。

### <a name="get-your-azure-cosmos-db-connection-string"></a>取得 Azure Cosmos DB 連接字串

如果您要連線到 Azure Cosmos DB，您必須將連接字串在本教學課程。 您可以從 Azure 入口網站複製您的連接字串。 在 Azure 入口網站中，在 Cosmos DB 帳戶中，移至**設定** > **連接字串**，然後按一下**複製**按鈕以複製主要的連線字串。 

教學課程中，輸入您的連接字串中您的指令碼，如下列範例所示：

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

不過，這是**不建議使用**實際的專案。 儲存體帳戶金鑰很類似儲存體帳戶的根密碼。 請務必小心保護您的儲存體帳戶金鑰。 請避免轉發給其他使用者，硬式編碼，或將它儲存在其他人可以存取純文字檔案。 您可以重新產生您使用 Azure 入口網站，如果您認為可能已遭盜用的金鑰。

實際的應用程式，來維護您的儲存體連接字串的最佳方式是在組態檔中。 若要從組態檔擷取連接字串，您可以這樣做：

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

使用 Azure Configuration Manager 是選擇性的。 您也可以使用 API，例如.NET Framework 的`ConfigurationManager`型別。

### <a name="parse-the-connection-string"></a>剖析連接字串

若要剖析的連接字串，請使用：

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

這會傳回`CloudStorageAccount`。

### <a name="create-the-table-service-client"></a>建立表格服務用戶端

`CloudTableClient`類別可讓您擷取資料表和資料表儲存體中的實體。 若要建立服務用戶端的其中一個方法如下：

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

現在您已準備好撰寫程式碼來讀取資料，並將資料寫入資料表儲存體。

### <a name="create-a-table"></a>建立資料表

此範例示範如何建立資料表，如果不存在：

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a>將實體新增至資料表

實體必須具有型別繼承自`TableEntity`。 您可以延伸`TableEntity`各種方式，但您的型別*必須*具有無參數建構函式。 同時具有的屬性`get`和`set`會儲存在您的 Azure 資料表。

實體的資料分割和資料列索引鍵可唯一識別資料表中的實體。 可在速度快於不同的資料分割索引鍵，查詢具有相同的資料分割索引鍵的實體，但使用不同的資料分割索引鍵可提供更佳的延展性的平行作業。

以下是範例`Customer`使用`lastName`做為資料分割索引鍵和`firstName`做為資料列索引鍵。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

現在加入`Customer`至資料表。 若要這樣做，請建立`TableOperation`資料表上執行。 在此案例中，您建立`Insert`作業。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

### <a name="insert-a-batch-of-entities"></a>插入實體批次

您可以將一批實體插入資料表中使用單一寫入作業。 批次作業可讓您將作業結合成單一的執行，但是它們有一些限制：

- 您可以執行更新、 刪除和插入相同的批次作業中。
- 批次作業可以包含最多 100 個實體。
- 批次作業中的所有實體必須都具有相同的資料分割索引鍵。
- 雖然您可以在批次作業中執行查詢，它必須是批次中唯一的作業。

以下是一些結合成一個批次作業的兩個插入的程式碼：

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

### <a name="retrieve-all-entities-in-a-partition"></a>擷取資料分割中的所有實體

若要查詢資料表的資料分割中的所有實體，請使用`TableQuery`物件。 在這裡，您篩選實體"Smith"所在的資料分割索引鍵。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

您現在會列印結果：

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]


### <a name="retrieve-a-range-of-entities-in-a-partition"></a>擷取範圍的資料分割中的實體

如果您不想要查詢資料分割中的所有實體，您可以藉由結合資料分割索引鍵篩選器與資料列索引鍵篩選器來指定範圍。 在這裡，您使用兩個篩選器來取得"Smith"資料分割中的所有實體資料列索引鍵 （名字） 開始的位置以字母"M"字母之前。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

您現在會列印結果：

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a>擷取單一實體

您可以撰寫查詢來擷取單一特定實體。 在這裡，您使用`TableOperation`來指定客戶"Ben Smith"。 而不是集合中，您會回到`Customer`。 在查詢中指定資料分割索引鍵和資料列索引鍵是最快的方法，從資料表服務中擷取單一實體。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

您現在會列印結果：

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]


### <a name="replace-an-entity"></a>取代實體

若要更新實體，從資料表服務中擷取、 修改實體物件，和接著將變更儲存回資料表服務會使用`Replace`作業。 除非伺服器上的實體自擷取後，在此情況下作業將會失敗，已變更，這樣會完全取代伺服器上的實體。 此失敗是為了防止您的應用程式不小心覆寫從其他來源的變更。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a>插入或取代實體

有時候，您不知道實體是否存在於資料表中。 如果有的話，不再需要儲存在它的目前值。 您可以使用`InsertOrReplace`建立實體，或取代它，若有的話，不論其狀態。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a>查詢實體屬性的子集

資料表查詢可以擷取而不是所有的這些實體的少數屬性。 這項技巧，稱為 「 投射 」 可改善查詢效能，尤其是對大型實體。 在這裡，您可以傳回只有電子郵件地址使用`DynamicTableEntity`和`EntityResolver`。 請注意，投射不支援在本機儲存體模擬器中，讓您在資料表服務上使用的帳戶時，才執行此程式碼。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L147-L158)]

### <a name="retrieve-entities-in-pages-asynchronously"></a>以非同步方式擷取頁面中的實體

如果您正在閱讀大量實體，而且您想要擷取這些，而非等待它們全部傳回，您可以使用分割的查詢時進行處理。 在這裡，您傳回的結果頁面中所使用的非同步工作流程，如此一來，您於等待的一大組要傳回的結果時，不會封鎖執行。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L163-L178)]

您現在執行這項計算以同步方式：

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L180-L180)]

### <a name="delete-an-entity"></a>刪除實體

在擷取之後，您可以刪除實體。 使用更新實體，這將會無法如果實體變更您在擷取之後。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L186-L187)]

### <a name="delete-a-table"></a>刪除資料表

您可以從儲存體帳戶刪除資料表。 已刪除的資料表將無法針對一段時間在刪除後加以重新建立。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L193-L193)]

## <a name="next-steps"></a>後續步驟

既然您已了解資料表儲存體的基本概念，請遵循下列連結以深入了解更複雜的儲存體工作以及 Azure Cosmos DB 資料表 API。

- [Azure Cosmos DB 資料表 API 簡介](https://docs.microsoft.com/azure/cosmos-db/table-introduction)
- [For.NET 參考資料的儲存體用戶端程式庫](https://docs.microsoft.com/dotnet/api/overview/azure/storage?view=azure-dotnet)
- [Azure 儲存體類型提供者](http://fsprojects.github.io/AzureStorageTypeProvider/)
- [Azure 儲存體團隊部落格](https://blogs.msdn.com/b/windowsazurestorage/)
- [設定連接字串](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
- [Getting Started with.NET 中的 Azure 資料表儲存體](https://azure.microsoft.com/resources/samples/storage-table-dotnet-getting-started/)

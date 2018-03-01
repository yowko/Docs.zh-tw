---
title: "開始使用 Azure 資料表儲存體使用 F #"
description: "將結構化的資料儲存在雲端中使用 Azure 資料表儲存體，NoSQL 資料存放區。"
keywords: "visual f #、 f #，功能性程式設計，.NET 中，.NET Core，Azure"
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 9e5d6cea-a98c-461e-a5cc-75f1d154eafd
ms.openlocfilehash: 905374a60261b0c2a863edb956943d41ae80f04d
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
---
# <a name="get-started-with-azure-table-storage-using-f"></a>開始使用 Azure 資料表儲存體使用 F # #

Azure 資料表儲存體是結構化的 NoSQL 資料存放在雲端服務。 資料表儲存體是 schemaless 設計的索引鍵/屬性存放區。 因為資料表儲存體是 schemaless，很容易就能為您的應用程式 evolve 的需求調整您的資料。 資料的存取權非常快速且符合成本效益的所有種類的應用程式。 資料表儲存體通常是遠低於成本中類似資料磁碟區的傳統 SQL。

您可以使用資料表儲存體來儲存彈性的資料集，例如 web 應用程式、 通訊錄，裝置資訊和任何其他類型的服務所需的中繼資料的使用者資料。 您可以將任意數目的實體儲存在資料表中，而且儲存體帳戶包含任何數量的資料表，儲存體帳戶的容量上限為止。

### <a name="about-this-tutorial"></a>關於本教學課程

本教學課程會示範如何撰寫 F # 程式碼來執行一些常見的工作，使用 Azure 資料表儲存體，包括建立和刪除資料表並插入、 更新、 刪除和查詢資料表的資料。

資料表儲存體概念的概觀，請參閱[資料表儲存體的.NET 指南](/azure/storage/storage-dotnet-how-to-use-tables)

## <a name="prerequisites"></a>必要條件

若要使用本指南，您必須先[建立 Azure 儲存體帳戶](/azure/storage/storage-create-storage-account)。
您還需要此帳戶的儲存體存取金鑰。

## <a name="create-an-f-script-and-start-f-interactive"></a>建立 F # 指令碼，並開始 F # Interactive

這篇文章中的範例可以用於 F # 應用程式或 F # 指令碼。 若要建立 F # 指令碼，建立檔案之`.fsx`擴充功能，例如`tables.fsx`，F # 開發環境中。

接下來，使用[封裝管理員](package-management.md)例如[Paket](https://fsprojects.github.io/Paket/)或[NuGet](https://www.nuget.org/)安裝`WindowsAzure.Storage`封裝和參考`WindowsAzure.Storage.dll`指令碼使用`#r`指示詞。 執行一次的 'Microsoft.WindowsAzure.ConfigurationManager' 以取得 Microsoft.Azure 命名空間。

### <a name="add-namespace-declarations"></a>加入命名空間宣告

加入下列`open`上方的陳述式`tables.fsx`檔案：

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>取得連接字串

此教學課程中，您將需要 Azure 儲存體連接字串。 如需連接字串的詳細資訊，請參閱[設定儲存體連接字串](/azure/storage/storage-configure-connection-string)。

教學課程中，您會輸入您的連接字串中指令碼中，像這樣：

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

不過，這是**不建議**用於真實的專案。 儲存體帳戶金鑰是類似於儲存體帳戶的根密碼。 一律為保護您的儲存體帳戶金鑰，請小心。 避免將其散發給其他使用者，硬式編碼，或將它儲存在其他人可以存取純文字檔案。 您可以重新產生您使用 Azure 入口網站，如果您認為可能已受到危害的金鑰。

用於真實的應用程式，以維護您的儲存體連接字串的最佳方式是在組態檔中。 若要從組態檔擷取連接字串，您可以：

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

使用 Azure 組態管理員是選擇性的。 您也可以使用例如.NET Framework API`ConfigurationManager`型別。

### <a name="parse-the-connection-string"></a>剖析連接字串

若要剖析的連接字串，使用：

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

這會傳回`CloudStorageAccount`。

### <a name="create-the-table-service-client"></a>建立表格服務用戶端

`CloudTableClient`類別可讓您擷取的資料表和資料表儲存體中儲存的實體。 以下是如何建立服務用戶端：

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

現在您已準備好開始撰寫程式碼讀取資料，並將資料寫入資料表儲存體。

## <a name="create-a-table"></a>建立資料表

這個範例示範如何建立資料表，如果不存在：

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

## <a name="add-an-entity-to-a-table"></a>將實體加入至資料表

實體必須要有型別繼承自`TableEntity`。 您可以擴充`TableEntity`任何方式，但您的型別*必須*具有無參數建構函式。 只有屬性同時具有`get`和`set`會儲存在 Azure 資料表。

實體的資料分割和資料列索引鍵唯一識別資料表中的實體。 具有相同的資料分割索引鍵的實體可以進行查詢速度比的不同資料分割索引鍵，但使用不同的資料分割索引鍵可讓平行作業的更佳的延展性。

以下是範例`Customer`使用`lastName`做為資料分割索引鍵和`firstName`做為資料列索引鍵。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

現在我們將新增我們`Customer`至資料表。 若要這樣做，您建立`TableOperation`用以在資料表上執行。 在此情況下，您建立`Insert`作業。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

## <a name="insert-a-batch-of-entities"></a>插入實體批次

您可以將實體批次插入資料表中使用單一寫入作業。 批次作業可讓您將作業結合成單一的執行，但具有一些限制：

- 您可以執行更新、 刪除和插入相同的批次作業中。
- 批次作業可以包含多達 100 個項目。
- 批次作業中的所有實體必須都有相同的資料分割索引鍵。
- 雖然也可以在批次作業中執行查詢，但是它必須是批次中唯一的作業。

以下是一些結合成一個批次作業的兩個插入的程式碼：

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

## <a name="retrieve-all-entities-in-a-partition"></a>擷取資料分割中的所有實體

若要查詢的資料表資料分割中的所有實體，請使用`TableQuery`物件。 在這裡，您篩選實體"Buster"所在的資料分割索引鍵。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L77-L80)]

您現在會列印結果：

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]


## <a name="retrieve-a-range-of-entities-in-a-partition"></a>擷取某個範圍的資料分割中的實體

如果您不想要查詢資料分割中的所有實體，您可以指定範圍，藉由結合資料分割索引鍵篩選，資料列索引鍵的篩選。 在這裡，您使用兩個篩選條件 」 Buster 」 資料分割中取得所有實體資料列索引鍵 （第一個名稱） 開始的位置以字母"M"中字母之前。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

您現在會列印結果：

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

## <a name="retrieve-a-single-entity"></a>擷取單一實體

您可以撰寫查詢以擷取單一的特定實體。 在此，您可以使用`TableOperation`來指定客戶"Larry Buster"。 而不是集合，您會回到`Customer`。 在查詢中指定資料分割索引鍵和資料列索引鍵是最快的方法來擷取與表格服務的單一實體。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

您現在會列印結果：

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]


## <a name="replace-an-entity"></a>取代實體

若要更新實體，擷取與表格服務、 修改實體物件，以及將變更儲存至表格服務會使用`Replace`作業。 除非變更伺服器上的實體自擷取後，作業會失敗，在此情況下，這會導致在伺服器上，完全取代實體。 此失敗是為了防止您的應用程式不小心覆寫從其他來源的變更。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

## <a name="insert-or-replace-an-entity"></a>插入或取代實體

有時候，您不知道實體是否已存在資料表中或不。 而且，若是如此，不再需要儲存在它的目前值。 您可以使用`InsertOrReplace`建立實體，或取代它，如果存在的話，不論其狀態。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L134-L140)]

## <a name="query-a-subset-of-entity-properties"></a>查詢實體屬性的子集

資料表查詢可以擷取只需要幾個屬性，而不是所有的這些實體。 這項技巧，呼叫投影，可以改善查詢效能，特別是大型的實體。 您在這裡，傳回僅電子郵件地址使用`DynamicTableEntity`和`EntityResolver`。 請注意，投影不支援在本機儲存體模擬器，以便在表格服務上使用的帳戶時，才執行此程式碼。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L146-L157)]

## <a name="retrieve-entities-in-pages-asynchronously"></a>以非同步方式擷取頁面中的實體

如果您正在閱讀大量實體，而且您想要擷取，而非等待它們全部傳回，您可以使用分割的查詢時進行處理。 在這裡，您傳回的結果頁面中使用的非同步工作流程，因此正在等待將大量要傳回的結果時，不會封鎖執行。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L163-L177)]

您現在執行這項計算以同步方式：

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L179-L179)]

## <a name="delete-an-entity"></a>刪除實體

您可以在擷取之後，刪除實體。 與更新實體，這將會失敗之後，如果實體已變更您擷取它。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L185-L186)]

## <a name="delete-a-table"></a>刪除資料表

您可以從儲存體帳戶刪除資料表。 已刪除的資料表將無法在重新建立此一段時間後刪除。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L192-L192)]

## <a name="next-steps"></a>後續步驟

既然您已學到的資料表儲存體的基本概念，請遵循下列連結，以了解更複雜的儲存體工作：

- [適用於.NET 的 azure 儲存體 Api](/dotnet/api/overview/azure/storage)
- [Azure 儲存體型別提供者](https://fsprojects.github.io/AzureStorageTypeProvider/)
- [Azure 儲存體團隊部落格](https://blogs.msdn.microsoft.com/b/windowsazurestorage/)
- [設定 Azure 儲存體連接字串](/azure/storage/common/storage-configure-connection-string)
- [在.NET 的 Azure 資料表儲存體使用者入門](https://azure.microsoft.com/documentation/samples/storage-table-dotnet-getting-started/)

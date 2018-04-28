---
title: '開始使用 Azure Blob 儲存體使用 F #'
description: 搭配 Azure Blob 儲存體在雲端中儲存非結構化的資料。
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: conceptual
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 0414f0ca4aa2c2b75e80b3fd6531be74924fb60f
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="get-started-with-azure-blob-storage-using-f"></a>開始使用 Azure Blob 儲存體使用 F # #

Azure Blob 儲存體是可將非結構化的資料儲存在雲端作為物件/Blob 的服務。 Blob 儲存體可以儲存任何類型的文字或二進位資料，例如文件、媒體檔案或應用程式安裝程式。 Blob 儲存體也稱為物件儲存體。

這篇文章會示範如何使用 Blob 儲存體執行一般工作。 這些範例會使用 F # 使用適用於.NET 的 Azure 儲存體用戶端程式庫所撰寫的。 涵蓋的工作包括如何上傳、 列出、 下載及刪除 blob。

Blob 儲存體概念的概觀，請參閱[blob 儲存體的.NET 指南](/azure/storage/storage-dotnet-how-to-use-blobs)。

## <a name="prerequisites"></a>必要條件

若要使用本指南，您必須先[建立 Azure 儲存體帳戶](/azure/storage/storage-create-storage-account)。 您也會需要此帳戶的儲存體存取金鑰。

## <a name="create-an-f-script-and-start-f-interactive"></a>建立 F # 指令碼，並開始 F # Interactive

這篇文章中的範例可以用於 F # 應用程式或 F # 指令碼。 若要建立 F # 指令碼，建立檔案之`.fsx`擴充功能，例如`blobs.fsx`，F # 開發環境中。

接下來，使用[封裝管理員](package-management.md)例如[Paket](https://fsprojects.github.io/Paket/)或[NuGet](https://www.nuget.org/)安裝`WindowsAzure.Storage`和`Microsoft.WindowsAzure.ConfigurationManager`封裝和參考`WindowsAzure.Storage.dll`和`Microsoft.WindowsAzure.Configuration.dll`在指令碼中使用`#r`指示詞。

### <a name="add-namespace-declarations"></a>加入命名空間宣告

加入下列`open`上方的陳述式`blobs.fsx`檔案：

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>取得連接字串

您在本教學課程需要 Azure 儲存體連接字串。 如需連接字串的詳細資訊，請參閱[設定儲存體連接字串](/azure/storage/storage-configure-connection-string)。

教學課程中，您可以輸入您的連接字串中指令碼中，像這樣：

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

不過，這是**不建議**用於真實的專案。 儲存體帳戶金鑰是類似於儲存體帳戶的根密碼。 一律為保護您的儲存體帳戶金鑰，請小心。 避免將其散發給其他使用者，硬式編碼，或將它儲存在其他人可以存取純文字檔案。 您可以重新產生您使用 Azure 入口網站，如果您認為可能已受到危害的金鑰。

用於真實的應用程式，以維護您的儲存體連接字串的最佳方式是在組態檔中。 若要從組態檔擷取連接字串，您可以：

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

使用 Azure 組態管理員是選擇性的。 您也可以使用例如.NET Framework API`ConfigurationManager`型別。

### <a name="parse-the-connection-string"></a>剖析連接字串

若要剖析的連接字串，使用：

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

這會傳回`CloudStorageAccount`。

### <a name="create-some-local-dummy-data"></a>建立一些本機虛設資料

開始之前，建立一些虛擬的本機資料的指令碼目錄中。 稍後您上傳此資料。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a>建立 Blob 服務用戶端

`CloudBlobClient`類型可讓您擷取容器和 Blob 儲存體中的 blob。 以下是如何建立服務用戶端：

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

現在您已準備好開始撰寫程式碼中讀取的資料，並將資料寫入至 Blob 儲存體。

## <a name="create-a-container"></a>建立容器

這個範例示範如何建立容器，如果不存在：

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

根據預設，新的容器是私人的也就是說，您必須指定要從這個容器下載 blob 儲存體存取金鑰。 如果您想要將容器內檔案提供給任何人，您可以設定容器必須是公用使用下列程式碼：

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

在網際網路上的任何人都可以看到公用容器中的 blob，但您可以修改或刪除它們，只有當您擁有適當的帳戶存取金鑰或共用的存取簽章。

## <a name="upload-a-blob-into-a-container"></a>將 blob 上傳到容器

Azure Blob 儲存體支援區塊 blob 和分頁 blob。 在大部分情況下，區塊 blob 是要使用的建議的類型。

若要上傳至區塊 blob 的檔案，取得為容器參考並使用它來取得區塊 blob 參考。 Blob 參考之後，您可以上傳資料的任何資料流，藉由呼叫`UploadFromFile`方法。 如果先前沒有存在，或覆寫它存在的話，這項作業會建立 blob。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a>列出容器中的 blob

若要列出容器中的 blob，先取得容器的參考。 然後，您可以使用容器的`ListBlobs`方法，以擷取 blob 及/或目錄內。 若要存取的屬性和方法傳回的一系列`IListBlobItem`，您必須將其轉換`CloudBlockBlob`， `CloudPageBlob`，或`CloudBlobDirectory`物件。 如果此類型為 unknown，您可以使用類型檢查來判斷哪些其轉型為。 下列程式碼示範如何擷取並輸出中的每個項目的 URI`mydata`容器：

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

您也可以在其名稱中的路徑資訊的 blob 名稱。 這會建立虛擬目錄結構，您可以組織及周遊如同傳統的檔案系統。 請注意，只是虛擬的目錄結構-Blob 儲存體中可用的唯一資源是容器和 blob。 不過，儲存體用戶端程式庫提供`CloudBlobDirectory`參照虛擬目錄，並簡化的 blob 會組織在這種方式，與處理序的物件。

例如，請考慮下列一名為的容器中的區塊 blob `photos`:

*photo1.jpg*
*2015/architecture/description.txt*
*2015/architecture/photo3.jpg*
*2015/architecture/photo4.jpg*
*2016/architecture/photo5.jpg*
*2016/architecture/photo6.jpg*
*2016/architecture/description.txt*
*2016/photo7.jpg*

當您呼叫`ListBlobs`在容器使用時 （如同上述範例中），會傳回階層式清單。 如果它同時包含`CloudBlobDirectory`和`CloudBlockBlob`物件，代表目錄和 blob 容器中的，則產生的輸出看起來類似這樣：

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

您可以選擇性地設定`UseFlatBlobListing`參數`ListBlobs`方法`true`。 在此情況下，會以傳回容器中的每個 blob`CloudBlockBlob`物件。 若要呼叫`ListBlobs`返回一般清單看起來像這樣：

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

此外，根據您的容器目前的內容，而結果看起來像這樣：

```console
Block blob of length 4: https://<accountname>.blob.core.windows.net/photos/2015/architecture/description.txt
Block blob of length 314618: https://<accountname>.blob.core.windows.net/photos/2015/architecture/photo3.jpg
Block blob of length 522713: https://<accountname>.blob.core.windows.net/photos/2015/architecture/photo4.jpg
Block blob of length 4: https://<accountname>.blob.core.windows.net/photos/2016/architecture/description.txt
Block blob of length 419048: https://<accountname>.blob.core.windows.net/photos/2016/architecture/photo5.jpg
Block blob of length 506388: https://<accountname>.blob.core.windows.net/photos/2016/architecture/photo6.jpg
Block blob of length 399751: https://<accountname>.blob.core.windows.net/photos/2016/photo7.jpg
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

## <a name="download-blobs"></a>下載 blob

若要下載 blob，先擷取 blob 的參考，然後呼叫`DownloadToStream`方法。 下列範例會使用`DownloadToStream`方法來傳輸資料流物件，您可以再保存到本機檔案的 blob 內容。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

您也可以使用`DownloadToStream`方法來下載為文字字串將 blob 的內容。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a>刪除 blob

若要刪除 blob，請先取得 blob 的參考，然後呼叫`Delete`方法。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a>以非同步方式列出網頁中的 blob

如果在列示大量的 blob，或您想要控制您在一個清單作業中傳回的結果數目，您可以列出結果的頁面中的 blob。 此範例顯示如何以非同步方式傳回的結果頁面中，以便等候傳回大量結果時不會封鎖執行。

此範例顯示一般 blob 清單，但您也可以藉由設定執行階層式清單，`useFlatBlobListing`參數`ListBlobsSegmentedAsync`方法`false`。

這個範例會定義非同步方法，使用`async`區塊。 ``let!``關鍵字會暫停執行範例的方法，直到清單的工作完成。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

我們現在可以使用這個非同步常式，如下所示。 第一次您上傳某些虛擬資料 （使用稍早在本教學課程中建立的本機檔案）。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

現在，呼叫常式。 您使用``Async.RunSynchronously``來強制執行非同步作業。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a>要寫入附加 blob

附加 blob 最適合用於附加作業，例如記錄。 如區塊 blob、 附加 blob 區塊組成，但當您新增新的區塊附加 blob 時，它一定會附加到 blob 結尾。 您無法更新或刪除現有區塊附加 blob 中。 因為它們是區塊 blob，不會公開附加 blob 的區塊識別碼。

每個區塊中附加 blob 可以是不同的大小，最大值為 4 MB，而且附加 blob 不可包括最多 50,000 個區塊。 附加 blob 的大小上限，因此是稍微大於 195 GB （4 MB X 50000 區塊）。

下列範例會建立新的附加 blob，並將一些資料附加至它，模擬簡單的記錄作業。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

請參閱[了解區塊 Blob、 分頁 Blob，並附加 Blob](https://msdn.microsoft.com/library/azure/ee691964.aspx)如需有關 blob 的三種類型之間的差異。

## <a name="concurrent-access"></a>並行存取

若要支援的 blob 的並行存取，從多個用戶端或多個處理序執行個體，您可以使用**Etag**或**租用**。

* **Etag** -提供方法來偵測 blob 或容器已修改的另一個處理序

* **租用**-可用來取得獨佔、 更新、 寫入或刪除的一段時間的存取權的 blob

如需詳細資訊，請參閱[管理 Microsoft Azure 儲存體中的並行存取](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/)。

## <a name="naming-containers"></a>命名的容器

Azure 儲存體中的每個 blob 必須位於容器中。 容器的 blob 名稱的一部分。 例如，`mydata`的這些範例 blob Uri 中的容器名稱：

    https://storagesample.blob.core.windows.net/mydata/blob1.txt
    https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg

容器名稱必須是有效的 DNS 名稱，並且符合下列命名規則：

1. 容器名稱必須以字母或數字開頭，而且只能包含字母、 數字和虛線 （-） 字元。
1. 每個虛線 （-） 字元必須是立即之前和之後都是字母或數字。容器名稱中不允許連續虛線。
1. 容器名稱中的所有字母都必須都是小寫。
1. 容器名稱必須介於 3 到 63 個字元。

請注意，容器的名稱一律必須是小寫。 如果您在輸入容器名稱中包含一個大寫字母或違反命名規則的容器，您可能會收到 400 的錯誤 （不正確的要求）。

## <a name="managing-security-for-blobs"></a>管理安全性的 blob

根據預設，Azure 儲存體會保留您的資料安全，方法是限制的存取權的帳戶擁有者，並且擁有帳戶存取金鑰。 當您要共用儲存體帳戶中的 blob 資料時，請務必這樣做不會危及您的帳戶存取金鑰的安全性。 此外，您可以加密以確保它的安全性會透過網路與 Azure 儲存體中的 blob 資料。

### <a name="controlling-access-to-blob-data"></a>控制對 blob 資料的存取

根據預設，在儲存體帳戶的 blob 資料是只有儲存體帳戶擁有者可以存取。 根據預設，驗證要求，針對 Blob 儲存體需要帳戶存取金鑰。 不過，您可能想要讓其他使用者使用特定的 blob 資料。

如需如何控制存取 blob 儲存體的詳細資訊，請參閱[blob 儲存體 區段上存取控制.NET 手冊](/azure/storage/storage-dotnet-how-to-use-blobs#controlling-access-to-blob-data)。


### <a name="encrypting-blob-data"></a>加密的 blob 資料

Azure 儲存體支援加密的用戶端和伺服器上的 blob 資料。

如需加密 blob 資料的詳細資訊，請參閱[blob 儲存體加密 區段的.NET 指南](/azure/storage/storage-dotnet-how-to-use-blobs#encrypting-blob-data)。

## <a name="next-steps"></a>後續步驟

現在，您學到 Blob 儲存體的基本概念，請遵循下列連結，以進一步了解。

### <a name="tools"></a>工具
- [F # AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/) F # 類型提供者可以用來瀏覽 Blob、 資料表和佇列的 Azure 儲存體資產，並輕鬆地套用在其上的 CRUD 作業。
- [FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage) F # 應用程式開發介面使用 Microsoft Azure 資料表儲存體服務
- [Microsoft Azure 儲存體總管 (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)是免費的可讓您能夠以視覺化方式使用 Azure 儲存體資料在 Windows、 OS X 和 Linux 上的 microsoft 獨立應用程式。

### <a name="blob-storage-reference"></a>Blob 儲存體參考

- [適用於.NET 的 azure 儲存體 Api](/dotnet/api/overview/azure/storage)
- [Azure 儲存體服務 REST API 參考](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)

### <a name="related-guides"></a>相關的輔助線

- [在 C# 中的 Azure Blob 儲存體使用者入門](https://azure.microsoft.com/resources/samples/storage-blob-dotnet-getting-started/)
- [使用 Windows 上的 AzCopy 命令列公用程式傳送資料](/azure/storage/common/storage-use-azcopy)
- [傳輸資料與 Linux 上的 AzCopy 命令列公用程式](/azure/storage/common/storage-use-azcopy-linux)
- [設定 Azure 儲存體連接字串](/azure/storage/common/storage-configure-connection-string)
- [Azure 儲存體團隊部落格](https://blogs.msdn.microsoft.com/windowsazurestorage/)

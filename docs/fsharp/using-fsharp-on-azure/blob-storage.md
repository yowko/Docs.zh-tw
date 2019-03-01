---
title: 開始使用 Azure Blob 儲存體使用F#
description: 使用 Azure Blob 儲存體在雲端中儲存非結構化的資料。
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: e38f58fefa63f922bcb1a78254249a3626bfac43
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981903"
---
# <a name="get-started-with-azure-blob-storage-using-f"></a>開始使用 Azure Blob 儲存體使用 F\#

Azure Blob 儲存體是可將非結構化的資料儲存在雲端作為物件/Blob 的服務。 Blob 儲存體可以儲存任何類型的文字或二進位資料，例如文件、媒體檔案或應用程式安裝程式。 Blob 儲存體也稱為物件儲存體。

這篇文章會示範如何使用 Blob 儲存體執行一般工作。 這些範例撰寫使用F#使用 Azure Storage Client Library for.NET。 涵蓋的工作包括如何上傳、 列出、 下載及刪除 blob。

Blob 儲存體概念的概觀，請參閱 < [blob 儲存體的.NET 指南](/azure/storage/storage-dotnet-how-to-use-blobs)。

## <a name="prerequisites"></a>必要條件

若要使用本指南，您必須先[建立 Azure 儲存體帳戶](/azure/storage/storage-create-storage-account)。 您也會需要此帳戶的儲存體存取金鑰。

## <a name="create-an-f-script-and-start-f-interactive"></a>建立F#指令碼，然後啟動F#互動

這篇文章中的範例可以用於在F#應用程式或F#指令碼。 若要建立F#指令碼，建立的檔案`.fsx`擴充功能，例如`blobs.fsx`，請在您F#開發環境。

接下來，使用[套件管理員](package-management.md)這類[Paket](https://fsprojects.github.io/Paket/)或[NuGet](https://www.nuget.org/)安裝`WindowsAzure.Storage`並`Microsoft.WindowsAzure.ConfigurationManager`套件和參考`WindowsAzure.Storage.dll`和`Microsoft.WindowsAzure.Configuration.dll`在指令碼中使用`#r`指示詞。

### <a name="add-namespace-declarations"></a>加入命名空間宣告

新增下列`open`陳述式的`blobs.fsx`檔案：

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>取得連接字串

您在本教學課程需要 Azure 儲存體連接字串。 如需有關連接字串的詳細資訊，請參閱 <<c0> [ 設定儲存體連接字串](/azure/storage/storage-configure-connection-string)。

教學課程中，您可以輸入您的連接字串中您的指令碼，就像這樣：

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

不過，這是**不建議使用**實際的專案。 儲存體帳戶金鑰很類似儲存體帳戶的根密碼。 請務必小心保護您的儲存體帳戶金鑰。 請避免轉發給其他使用者，硬式編碼，或將它儲存在其他人可以存取純文字檔案。 您可以重新產生您使用 Azure 入口網站，如果您認為可能已遭盜用的金鑰。

實際的應用程式，來維護您的儲存體連接字串的最佳方式是在組態檔中。 若要從組態檔擷取連接字串，您可以這樣做：

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

使用 Azure Configuration Manager 是選擇性的。 您也可以使用 API，例如.NET Framework 的`ConfigurationManager`型別。

### <a name="parse-the-connection-string"></a>剖析連接字串

若要剖析的連接字串，請使用：

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

這會傳回`CloudStorageAccount`。

### <a name="create-some-local-dummy-data"></a>建立一些本機的 dummy 資料

開始之前，請在我們的指令碼的目錄中建立一些假的本機資料。 稍後您上傳此資料。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a>建立 Blob 服務用戶端

`CloudBlobClient`類型可讓您擷取容器和 Blob 儲存體中的 blob。 若要建立服務用戶端的其中一個方法如下：

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

現在您已準備好撰寫程式碼來讀取資料，並將資料寫入至 Blob 儲存體。

## <a name="create-a-container"></a>建立容器

此範例示範如何建立容器，如果不存在：

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

根據預設，新容器屬私人的這表示您必須指定您的儲存體存取金鑰才能從此容器下載 blob。 如果您想要在容器內的檔案提供給所有人，您可以將容器設定公開使用下列程式碼：

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

在網際網路上的任何人都可以看到公用容器中的 blob，但您可以修改或刪除它們，只有當您擁有適當的帳戶存取金鑰或共用的存取簽章。

## <a name="upload-a-blob-into-a-container"></a>將 blob 上傳至容器

Azure Blob 儲存體支援區塊 blob 和分頁 blob。 在大部分情況下，區塊 blob 是要使用的建議的類型。

將檔案上傳至區塊 blob，取得容器參考，並使用它來取得區塊 blob 參考。 Blob 參考之後，您可以上傳任何資料流，藉由呼叫`UploadFromFile`方法。 如果先前未存在，或覆寫它，如果檔案存在，此作業就會建立 blob。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a>列出容器中的 blob

若要列出容器中的 blob，請先取得容器參考。 然後，您可以使用容器的`ListBlobs`方法來擷取 blob 和/或目錄。 若要存取的屬性和方法傳回一組豐富`IListBlobItem`，您必須將它轉換成`CloudBlockBlob`， `CloudPageBlob`，或`CloudBlobDirectory`物件。 如果類型是未知，您可以使用類型檢查來決定要將它轉換成。 下列程式碼示範如何擷取和輸出中的每個項目的 URI`mydata`容器：

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

您也可以在其名稱中的路徑資訊的 blob 名稱。 這會建立虛擬目錄結構，您能夠組織及周遊，就像使用傳統檔案系統。 請注意，只是虛擬目錄結構-唯一的 Blob 儲存體中的可用資源為容器和 blob。 不過，儲存體用戶端程式庫提供`CloudBlobDirectory`物件來參照虛擬目錄，以及簡化這種方式組織 blob 所使用的程序。

例如，請考慮下列一組區塊 blob 容器內`photos`:

*photo1.jpg*
*2015/architecture/description.txt*
*2015/architecture/photo3.jpg*
*2015/architecture/photo4.jpg*
*2016/architecture/photo5.jpg*
*2016/architecture/photo6.jpg*
*2016/architecture/description.txt*
*2016/photo7.jpg*

當您呼叫`ListBlobs`（如同上述範例中） 的容器，會傳回階層式清單。 如果它同時包含`CloudBlobDirectory`和`CloudBlockBlob`物件，代表目錄和 blob 容器中，分別則產生的輸出看起來如下所示：

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

您可以選擇性地設定`UseFlatBlobListing`的參數`ListBlobs`方法，以`true`。 在此情況下，每個 blob 容器中的會傳回為`CloudBlockBlob`物件。 若要呼叫`ListBlobs`傳回簡單列表看起來像這樣：

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

而且，根據您的容器目前的內容，結果看起來像這樣：

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

若要下載 blob，請先擷取 blob 參考，然後呼叫`DownloadToStream`方法。 下列範例會使用`DownloadToStream`方法，以將 blob 內容傳送到您可接著保留本機檔案的串流物件。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

您也可以使用`DownloadToStream`方法來下載 blob 的內容當成文字字串。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a>刪除 blob

若要刪除 blob，請先取得 blob 參考，然後呼叫`Delete`在其上的方法。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a>以非同步方式列出在頁面中的 blob

如果您要列出大量 blob，或您想要控制您在單一列出作業所傳回的結果數目，您可以列出結果頁面中的 blob。 此範例會示範如何以非同步方式分頁傳回結果，以便等待傳回大型結果集而不會封鎖執行。

此範例示範一般 blob 列出方式，但您也可以藉由設定執行階層式清單中，`useFlatBlobListing`的參數`ListBlobsSegmentedAsync`方法，以`false`。

此範例會定義非同步方法，使用`async`區塊。 ``let!``關鍵字會暫停執行範例的方法，直到列出工作完成。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

我們現在可以使用這個非同步常式，如下所示。 第一次您上傳一些假的資料 （使用稍早在本教學課程中建立的本機檔案）。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

現在，呼叫的常式。 您使用`Async.RunSynchronously`來強制執行非同步作業。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a>寫入至附加 blob

附加 blob 已針對附加作業，例如記錄最佳化。 如同區塊 blob、 附加 blob 由區塊組成，但當您將新區塊加入附加 blob 時，它一律會附加到 blob 結尾。 您無法更新或刪除附加 blob 中的現有區塊。 附加 blob 的區塊識別碼不會公開的區塊 blob。

附加 blob 中的每個區塊可以是不同的大小，最多為 4 MB，並附加 blob 可包含最多 50,000 個區塊。 附加 blob 的大小上限，因此是稍高於 195 GB （4 MB 個區塊）。

下列範例會建立新的附加 blob，並附加一些資料，來模擬簡單的記錄作業。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

請參閱[了解區塊 Blob、 分頁 Blob 和附加 Blob](https://msdn.microsoft.com/library/azure/ee691964.aspx)如需有關 blob 的三種類型之間的差異。

## <a name="concurrent-access"></a>並行存取

若要支援並行存取的 blob，從多個用戶端或多個處理序執行個體，您可以使用**Etag**或是**租用**。

* **Etag** -提供一個方式來偵測 blob 或容器，已修改另一個處理序

* **租用**-可用來取得獨佔、 可更新、 寫入或刪除 blob 的存取權的一段時間

如需詳細資訊，請參閱 <<c0> [ 管理 Microsoft Azure 儲存體中的並行存取](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/)。

## <a name="naming-containers"></a>命名的容器

Azure 儲存體中的每個 blob 必須位於一個容器。 此容器會組成 blob 名稱的一部分。 比方說，`mydata`的這些範例 blob Uri 中的容器名稱：

    https://storagesample.blob.core.windows.net/mydata/blob1.txt
    https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg

容器名稱必須是有效的 DNS 名稱，且符合下列命名規則：

1. 容器名稱必須以字母或數字開頭，並且可包含字母、 數字和虛線 （-） 字元。
1. 每個虛線 （-） 字元必須是立即前面和後面接著字母或數字，容器名稱中不允許連續虛線。
1. 容器名稱中的所有字母必須都是小寫。
1. 容器名稱必須介於 3 至 63 個字元。

請注意，容器的名稱一律必須小寫。 如果您輸入容器名稱中包含大寫字母或其他違反容器命名規則，您可能會收到 400 錯誤 （不正確的要求）。

## <a name="managing-security-for-blobs"></a>管理 blob 安全性

根據預設，Azure 儲存體會保持資料安全限制的存取帳戶擁有者的帳戶存取金鑰的擁有權。 當您需要共用儲存體帳戶中的 blob 資料時，很重要，若要這樣做不會危及您帳戶存取金鑰的安全性。 此外，您可以加密 blob 資料，以確保它是安全會透過網路與 Azure 儲存體中。

### <a name="controlling-access-to-blob-data"></a>控制對 blob 資料的存取

根據預設，在儲存體帳戶的 blob 資料是只有儲存體帳戶擁有者可以存取。 根據預設，驗證對 Blob 儲存體的要求需要帳戶存取金鑰。 不過，您可能會想讓其他使用者使用特定的 blob 資料。

### <a name="encrypting-blob-data"></a>加密 blob 資料

Azure 儲存體支援加密在用戶端和伺服器上的 blob 資料。

## <a name="next-steps"></a>後續步驟

既然您已了解 Blob 儲存體的基本概念，請遵循下列連結以了解更多。

### <a name="tools"></a>工具

- [F# AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/)\
F#型別提供者可用來瀏覽 Blob、 資料表和佇列的 Azure 儲存體資產，並輕鬆地套用在其上的 CRUD 作業。

- [FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage)\
F#使用 Microsoft Azure 資料表儲存體服務 API

- [Microsoft Azure 儲存體總管 (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)\
可讓您以視覺化方式處理 Azure 儲存體的資料在 Windows、 OSX 和 Linux 上的 Microsoft 免費的獨立應用程式。

### <a name="blob-storage-reference"></a>Blob 儲存體參考

- [適用於.NET 的 azure 儲存體 Api](/dotnet/api/overview/azure/storage)
- [Azure 儲存體服務 REST API 參考](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)

### <a name="related-guides"></a>相關的輔助線

- [開始使用 C# 中的 Azure Blob 儲存體](https://azure.microsoft.com/resources/samples/storage-blob-dotnet-getting-started/)
- [Windows 上的 AzCopy 命令列公用程式傳輸資料](/azure/storage/common/storage-use-azcopy)
- [使用 AzCopy 命令列公用程式 on Linux 傳送資料](/azure/storage/common/storage-use-azcopy-linux)
- [設定 Azure 儲存體連接字串](/azure/storage/common/storage-configure-connection-string)
- [Azure 儲存體團隊部落格](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [快速入門：使用.NET 來建立 blob 物件儲存體中](/azure/storage/blobs/storage-quickstart-blobs-dotnet)
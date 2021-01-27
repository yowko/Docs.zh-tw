---
title: 以 F 開始使用 Azure Blob 儲存體#
description: 使用 Azure Blob 儲存體將非結構化資料儲存在雲端。
author: sylvanc
ms.date: 09/20/2016
ms.custom: devx-track-fsharp
ms.openlocfilehash: 58c120c26a1e99481b49ae3a0fb096a2188f359e
ms.sourcegitcommit: 4d5e25a46aa7cd0d29b4b9227b92987354d444c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2021
ms.locfileid: "98794803"
---
# <a name="get-started-with-azure-blob-storage-using-f"></a>以 F 開始使用 Azure Blob 儲存體\#

Azure Blob 儲存體是將非結構化資料儲存在雲端作為物件/blob 的服務。 Blob 儲存體可以儲存任何類型的文字或二進位資料，例如文件、媒體檔案或應用程式安裝程式。 Blob 儲存體也稱為物件儲存體。

本文說明如何使用 Blob 儲存體執行一般工作。 這些範例是使用適用于 .NET 的 Azure 儲存體用戶端程式庫，以 F # 撰寫。 涵蓋的工作包括如何上傳、列出、下載和刪除 blob。

如需 blob 儲存體的概念總覽，請參閱 [適用于 blob 儲存體的 .net 指南](/azure/storage/blobs/storage-quickstart-blobs-dotnet)。

## <a name="prerequisites"></a>先決條件

若要使用本指南，您必須先 [建立 Azure 儲存體帳戶](/azure/storage/common/storage-account-create)。 您也需要此帳戶的儲存體存取金鑰。

## <a name="create-an-f-script-and-start-f-interactive"></a>建立 F # 腳本並開始 F# 互動

本文中的範例可用於 F # 應用程式或 F # 腳本。 若要建立 F # 腳本，請 `.fsx` `blobs.fsx` 在您的 f # 開發環境中建立副檔名為的檔案，例如。

接下來，使用 [套件管理員](package-management.md) （例如 [Paket](https://fsprojects.github.io/Paket/) 或 [NuGet](https://www.nuget.org/) ）， `WindowsAzure.Storage` `Microsoft.WindowsAzure.ConfigurationManager` `WindowsAzure.Storage.dll` `Microsoft.WindowsAzure.Configuration.dll` 在您的腳本中使用指示詞安裝和封裝和參考 `#r` 。

### <a name="add-namespace-declarations"></a>新增命名空間宣告

在 `blobs.fsx` 檔案頂端新增下列 `open` 陳述式：

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>取得您的連接字串

在本教學課程中，您需要 Azure 儲存體連接字串。 如需連接字串的詳細資訊，請參閱 [設定儲存體連接字串](/azure/storage/storage-configure-connection-string)。

在本教學課程中，您會在腳本中輸入連接字串，如下所示：

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

不過，這不 **建議** 用於實際的專案。 儲存體帳戶金鑰很類似儲存體帳戶的根密碼。 請務必小心保護您的儲存體帳戶金鑰。 請避免轉發給其他使用者、進行硬式編碼，或將它儲存在其他人可以存取的純文字檔案。 如果您認為金鑰可能已遭盜用，您可以使用 Azure 入口網站重新產生金鑰。

針對實際的應用程式，維護儲存體連接字串的最佳方式是在設定檔中。 若要從設定檔提取連接字串，您可以執行下列動作：

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

是否使用 Azure Configuration Manager 可由您選擇。 您也可以使用 API，例如 .NET Framework 的型別 `ConfigurationManager` 。

### <a name="parse-the-connection-string"></a>解析連接字串

若要剖析連接字串，請使用：

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

這會傳回 `CloudStorageAccount` 。

### <a name="create-some-local-dummy-data"></a>建立一些本機虛擬資料

開始之前，請在腳本的目錄中建立一些虛擬本機資料。 稍後，您可以上傳此資料。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a>建立 Blob 服務用戶端

此 `CloudBlobClient` 類型可讓您取出儲存在 Blob 儲存體中的容器和 blob。 以下是建立服務用戶端的其中一種方式：

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

您現在可以開始撰寫程式碼，以讀取 Blob 儲存體的資料並將資料寫入其中。

## <a name="create-a-container"></a>建立容器

此範例說明如何建立尚不存在的容器：

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

根據預設，新容器屬私人性質，這表示您必須指定儲存體存取金鑰才能從此容器下載 Blob。 若要讓所有人都能使用容器中的檔案，您可以使用下列程式碼將容器設定為公用容器：

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

網際網路上的任何人都可以看到公用容器中的 Blob，但要有適當的帳戶存取金鑰或共用存取簽章，才能修改或刪除這些 Blob。

## <a name="upload-a-blob-into-a-container"></a>將 Blob 上傳至容器

Azure Blob 儲存體支援區塊 Blob 和頁面 Blob。 在大多數情況下，區塊 blob 是建議使用的類型。

若要將檔案上傳至區塊 Blob，請取得容器參照，並使用該參照來取得區塊 Blob 參照。 當您有 blob 參考之後，就可以藉由呼叫方法，將任何資料流程上傳至其中 `UploadFromFile` 。 如果 blob 不存在，此作業會建立 blob，如果存在，則會加以覆寫。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a>列出容器中的 Blob

若要列出容器中的 Blob，請先取得容器參照。 然後，您可以使用容器的 `ListBlobs` 方法來取得 blob 和（或）其中的目錄。 若要針對傳回的，存取一組豐富的屬性和方法 `IListBlobItem` ，您必須將它轉換成 `CloudBlockBlob` 、 `CloudPageBlob` 或 `CloudBlobDirectory` 物件。 如果不清楚類型，可使用類型檢查來決定要將其轉換至何種類型。 下列程式碼示範如何擷取和輸出 `mydata` 容器中每個項目的 URI：

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

您也可以使用名稱的路徑資訊來命名 blob。 這會建立虛擬目錄結構，讓您能夠組織及周遊，就像使用傳統檔案系統一樣。 目錄結構僅限虛擬，Blob 儲存體中唯一可用的資源是容器和 blob。 不過，儲存體用戶端程式庫會提供 `CloudBlobDirectory` 物件來參考虛擬目錄，並簡化使用以這種方式組織之 blob 的處理常式。

例如，假設名為 `photos`的容器中有下面這一組區塊 blob：

*photo1.jpg*\
*2015/架構/description.txt*\
*2015/架構/photo3.jpg*\
*2015/架構/photo4.jpg*\
*2016/架構/photo5.jpg*\
*2016/架構/photo6.jpg*\
*2016/架構/description.txt*\
*2016/photo7.jpg*\

當您在 `ListBlobs` 容器上呼叫 (如上述範例) 所示，會傳回階層式清單。 如果它同時包含 `CloudBlobDirectory` 和 `CloudBlockBlob` 物件，分別代表容器中的目錄和 blob，則產生的輸出看起來會像這樣：

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

（選擇性）您可以將 `UseFlatBlobListing` 方法的參數設定 `ListBlobs` 為 `true` 。 在此情況下，容器中的每個 blob 都會以物件的形式傳回 `CloudBlockBlob` 。 的呼叫會傳回一般清單，如下所 `ListBlobs` 示：

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

而且，視容器目前的內容而定，結果看起來像這樣：

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

## <a name="download-blobs"></a>下載 Blob

若要下載 blob，請先取得 blob 參考，然後呼叫 `DownloadToStream` 方法。 下列範例 `DownloadToStream` 會使用方法，將 blob 內容傳送給資料流程物件，您接著可以將這些內容保存到本機檔案。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

您也可以使用 `DownloadToStream` 方法，將 blob 的內容下載為文字字串。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a>刪除 Blob

若要刪除 blob，請先取得 blob 參考，然後 `Delete` 在其上呼叫方法。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a>以非同步方式分頁列出 Blob

如果您要列出大量的 Blob，或是要控制在單一列出作業中傳回的結果數，您可以在結果頁面中列出 Blob。 此範例說明如何以非同步方式分頁傳回結果，使執行不會因為等待大型結果集傳回而中斷。

此範例顯示一般 blob 清單，但您也可以將方法的參數設定為，以執行階層式清單 `useFlatBlobListing` `ListBlobsSegmentedAsync` `false` 。

此範例會使用區塊來定義非同步方法 `async` 。 ``let!``關鍵字會暫停執行範例方法，直到清單工作完成為止。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

我們現在可以使用這個非同步常式，如下所示。 首先，使用本教學課程稍早所建立的本機檔案，上傳一些虛擬資料 () 。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

現在，呼叫常式。 您可以使用 `Async.RunSynchronously` 來強制執行非同步作業。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a>寫入附加 Blob

附加 Blob 已針對附加作業 (例如紀錄) 最佳化。 如同區塊 blob，附加 blob 是由區塊所組成，但當您將新區塊新增至附加 blob 時，它一律會附加至 blob 的結尾。 您無法更新或刪除附加 Blob 中的現有區塊。 附加 Blob 的區塊識別碼不會公開顯示，因為該識別碼適用於區塊 Blob。

附加 Blob 中的每個區塊大小都不同，最大為 4 MB，而附加 Blob 可包含高達 50,000 個區塊。 因此，附加 Blob 的大小上限稍高於 195 GB (4 MB X 50,000 個區塊)。

下列範例會建立新的附加 blob，並在其中附加一些資料，以模擬簡單的記錄作業。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

如需了解有關 Blob 的三種類型間差異的資訊，請參閱 [了解區塊 Blob、分頁 Blob 和附加 Blob](/rest/api/storageservices/Understanding-Block-Blobs--Append-Blobs--and-Page-Blobs) 。

## <a name="concurrent-access"></a>並行存取

若要支援從多個用戶端或多個程序執行個體並行存取 Blob，您可以使用 **ETags** 或「租用」。

- **Etag** - 提供方法來偵測 Blob 或容器已被另一個程序修改過

- **租用** -提供一段時間來取得對 blob 的獨佔、可再生、寫入或刪除存取權的方法。

如需詳細資訊，請參閱 [管理 Microsoft Azure 儲存體中的並行](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/)存取。

## <a name="naming-containers"></a>命名容器

儲存體 Blob 中的每個 Blob 必須位於一個容器中。 此容器會組成 blob 名稱的一部分。 例如， `mydata` 是這些範例 blob URI 中容器的名稱：

- `https://storagesample.blob.core.windows.net/mydata/blob1.txt`
- `https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg`

容器名稱必須是有效的 DNS 名稱，且符合下列命名規則：

1. 容器名稱必須以字母或數字開頭，並且只能包含字母、數字和虛線 (-) 字元。
1. 每個虛線 (-) 字元前後必須立即接著字母或數字；容器名稱中不允許連續虛線。
1. 容器名稱的所有字母必須都是小寫。
1. 容器名稱必須介於 3 至 63 個字元長。

容器的名稱必須一律為小寫。 如果在容器名稱中含有大寫字母，或其他違反容器命名規則，您可能會收到「400 錯誤 (不正確的要求)」錯誤訊息。

## <a name="managing-security-for-blobs"></a>管理 Blob 安全性

根據預設，Azure 儲存體會限制擁有帳戶存取金鑰的帳戶擁有者的存取權來保持資料安全。 當您需要共用儲存體帳戶中的 Blob 資料時，請注意不可危及您帳戶存取金鑰的安全性。 此外，您可以加密 blob 資料以確保透過網路與 Azure 儲存體中的安全。

### <a name="controlling-access-to-blob-data"></a>控制對 blob 資料的存取

根據預設，您儲存體帳戶中的 blob 資料僅供儲存體帳戶擁有者使用。 依預設，驗證對 Blob 儲存體的要求需要帳戶存取金鑰。 不過，您可能會想要將某些 blob 資料提供給其他使用者。

### <a name="encrypting-blob-data"></a>加密 blob 資料

Azure 儲存體支援在用戶端和伺服器上加密 blob 資料。

## <a name="next-steps"></a>後續步驟

了解 Blob 儲存體的基礎概念之後，請使用下列連結深入了解。

### <a name="tools"></a>工具

- [F # AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/)\
F # 型別提供者，可用來流覽 Blob、資料表和佇列 Azure 儲存體資產，並輕鬆地對其套用 CRUD 作業。

- [Fsharp.core](https://github.com/fsprojects/FSharp.Azure.Storage)\
使用 Microsoft Azure 資料表儲存體服務的 F # API

- [Microsoft Azure 儲存體總管 (MASE) ](/azure/vs-azure-tools-storage-manage-with-storage-explorer)\
Microsoft 提供的免費獨立應用程式，可讓您在 Windows、OS X 和 Linux 上以視覺化方式處理 Azure 儲存體資料。

### <a name="blob-storage-reference"></a>Blob 儲存體參考

- [適用於 .NET 的 Azure 儲存體 API](/dotnet/api/overview/azure/storage)
- [Azure 儲存體服務 REST API 參考](/rest/api/storageservices/)

### <a name="related-guides"></a>相關指南

- [適用於 .NET 的 Azure Blob 儲存體範例](/samples/azure-samples/storage-blob-dotnet-getting-started/storage-blob-dotnet-getting-started/)
- [開始使用 AzCopy](/azure/storage/common/storage-use-azcopy-v10)
- [設定 Azure 儲存體連接字串](/azure/storage/common/storage-configure-connection-string)
- [Azure 儲存體團隊部落格](/archive/blogs/windowsazurestorage/)
- [快速入門：使用 .NET 在物件儲存體中建立 Blob](/azure/storage/blobs/storage-quickstart-blobs-dotnet)

---
title: 使用 F# 開始使用 Azure Blob 儲存體
description: 使用 Azure Blob 儲存體, 將非結構化資料儲存在雲端。
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: c765f38cba7642e813a5966d3b7754c5ce45abbd
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107114"
---
# <a name="get-started-with-azure-blob-storage-using-f"></a>開始使用 F 來使用 Azure Blob 儲存體\#

Azure Blob 儲存體是可將非結構化的資料儲存在雲端作為物件/Blob 的服務。 Blob 儲存體可以儲存任何類型的文字或二進位資料，例如文件、媒體檔案或應用程式安裝程式。 Blob 儲存體也稱為物件儲存體。

本文說明如何使用 Blob 儲存體執行一般工作。 這些範例是使用F#適用于 .net 的 Azure 儲存體用戶端程式庫來撰寫。 涵蓋的工作包括如何上傳、列出、下載和刪除 blob。

如需 blob 儲存體的概念總覽, 請參閱[blob 儲存體的 .net 指南](/azure/storage/storage-dotnet-how-to-use-blobs)。

## <a name="prerequisites"></a>必要條件

若要使用本指南, 您必須先[建立 Azure 儲存體帳戶](/azure/storage/storage-create-storage-account)。 您也需要此帳戶的儲存體存取金鑰。

## <a name="create-an-f-script-and-start-f-interactive"></a>建立F#腳本並啟動F#互動式

本文中的範例可用於F#應用程式或F#腳本中。 若要建立F#腳本, 請在`.fsx` F#開發環境中建立`blobs.fsx`副檔名為的檔案, 例如。

接下來, 使用[Paket](https://fsprojects.github.io/Paket/)或`WindowsAzure.Storage` [NuGet](https://www.nuget.org/)之類的[套件管理員](package-management.md), 在您的`Microsoft.WindowsAzure.ConfigurationManager`腳本`Microsoft.WindowsAzure.Configuration.dll`中使用`WindowsAzure.Storage.dll` `#r`指示詞安裝和封裝和參考。

### <a name="add-namespace-declarations"></a>新增命名空間宣告

將下列`open`語句新增至檔案頂端`blobs.fsx` :

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>取得您的連接字串

在本教學課程中, 您需要 Azure 儲存體連接字串。 如需連接字串的詳細資訊, 請參閱[設定儲存體連接字串](/azure/storage/storage-configure-connection-string)。

在本教學課程中, 您會在腳本中輸入連接字串, 如下所示:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

不過, 這**不建議**用於實際的專案。 您的儲存體帳戶金鑰類似于儲存體帳戶的根密碼。 請務必小心保護您的儲存體帳戶金鑰。 請避免將它散發給其他使用者、進行硬式編碼, 或將它儲存在其他人可以存取的純文字檔案中。 如果您認為金鑰可能遭到入侵, 您可以使用 Azure 入口網站重新產生金鑰。

對於實際的應用程式而言, 維護儲存體連接字串的最佳方式是在設定檔中。 若要從設定檔提取連接字串, 您可以執行下列動作:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

使用 Azure Configuration Manager 是選擇性的。 您也可以使用 API (例如 .NET Framework 的`ConfigurationManager`類型)。

### <a name="parse-the-connection-string"></a>剖析連接字串

若要剖析連接字串, 請使用:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

這會傳回`CloudStorageAccount`。

### <a name="create-some-local-dummy-data"></a>建立一些本機虛擬資料

在開始之前, 請在腳本的目錄中建立一些虛擬的本機資料。 稍後您將上傳此資料。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a>建立 Blob 服務用戶端

`CloudBlobClient`型別可讓您抓取 blob 儲存體中儲存的容器和 blob。 以下是建立服務用戶端的其中一種方式:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

現在您已準備好撰寫程式碼, 以讀取資料並將資料寫入至 Blob 儲存體。

## <a name="create-a-container"></a>建立容器

這個範例示範如何建立容器 (如果尚未存在):

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

根據預設, 新的容器是私用的, 這表示您必須指定儲存體存取金鑰, 才能從此容器下載 blob。 如果您想要讓所有人都能使用容器中的檔案, 您可以使用下列程式碼將容器設定為公用:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

網際網路上的任何人都可以看到公用容器中的 blob, 但只有在您擁有適當的帳戶存取金鑰或共用存取簽章時, 才可以修改或刪除它們。

## <a name="upload-a-blob-into-a-container"></a>將 blob 上傳至容器

Azure Blob 儲存體支援區塊 blob 和分頁 blob。 在大部分情況下, 建議使用區塊 blob 的類型。

若要將檔案上傳至區塊 blob, 請取得容器參考, 並使用它來取得區塊 blob 參考。 一旦擁有 blob 參考之後, 您就可以藉由呼叫`UploadFromFile`方法, 將任何資料流程上傳至其中。 如果 blob 先前不存在, 此作業會加以建立, 如果存在, 則會加以覆寫。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a>列出容器中的 blob

若要列出容器中的 blob, 請先取得容器參考。 然後, 您可以使用容器的`ListBlobs`方法來抓取 blob 和 (或) 其中的目錄。 若要`IListBlobItem`存取所傳回之的一組豐富屬性和方法, 您必須將它轉換`CloudBlockBlob`成、 `CloudPageBlob`或`CloudBlobDirectory`物件。 如果類型是未知的, 您可以使用類型檢查來決定要將它轉換成哪一個。 下列程式碼示範如何抓取和輸出`mydata`容器中每個專案的 URI:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

您也可以在名稱中命名包含路徑資訊的 blob。 這會建立一個虛擬目錄結構, 您可以像使用傳統檔案系統一樣進行組織和進行管理。 請注意, 目錄結構僅限虛擬, Blob 儲存體中唯一可用的資源為容器和 blob。 不過, 儲存體用戶端程式庫提供`CloudBlobDirectory`一個物件來參照虛擬目錄, 並簡化以這種方式組織之 blob 的處理常式。

例如, 在名為`photos`的容器中, 請考慮下列一組區塊 blob:

*photo1.jpg*\
*2015/架構/描述 .txt*\
*2015/架構/photo3 .jpg*\
*2015/架構/photo4 .jpg*\
*2016/架構/photo5 .jpg*\
*2016/架構/photo6 .jpg*\
*2016/架構/描述 .txt*\
*2016/photo7.jpg*\

當您在`ListBlobs`容器上呼叫 (如上述範例所示) 時, 會傳回階層式清單。 如果它同時`CloudBlobDirectory`包含和`CloudBlockBlob`物件, 分別代表容器中的目錄和 blob, 則產生的輸出看起來會像這樣:

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

(選擇性) 您可以將`UseFlatBlobListing` `ListBlobs`方法的參數設定為`true`。 在此情況下, 容器中的每個 blob 都會以`CloudBlockBlob`物件的形式傳回。 對的呼叫`ListBlobs`會傳回一般清單, 如下所示:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

而且, 視容器的目前內容而定, 結果如下所示:

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

若要下載 blob, 請先取出 blob 參考, 然後再`DownloadToStream`呼叫方法。 下列範例會使用`DownloadToStream`方法, 將 blob 內容傳送給資料流程物件, 然後您可以將它保存到本機檔案。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

您也可以使用`DownloadToStream`方法, 將 blob 的內容下載為文字字串。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a>刪除 blob

若要刪除 blob, 請先取得 blob 參考, 然後在其`Delete`上呼叫方法。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a>以非同步方式列出頁面中的 blob

如果您要列出大量的 blob, 或想要控制在一個列出作業中傳回的結果數目, 您可以在結果頁面中列出 blob。 這個範例示範如何以非同步方式傳回頁面中的結果, 以便在等候傳回大量結果時不會封鎖執行。

這個範例會顯示一般 blob 清單, 但您也可以藉由將`useFlatBlobListing` `ListBlobsSegmentedAsync`方法的參數設定為`false`, 來執行階層式清單。

此範例會使用`async`區塊來定義非同步方法。 ``let!``關鍵字會暫停執行範例方法, 直到清單工作完成為止。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

我們現在可以使用這個非同步常式, 如下所示。 首先上傳一些虛擬資料 (使用本教學課程稍早建立的本機檔案)。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

現在, 請呼叫常式。 您可以`Async.RunSynchronously`使用來強制執行非同步作業。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a>寫入附加 blob

附加 blob 已針對附加作業優化, 例如記錄。 如同區塊 blob, 附加 blob 是由區塊所組成, 但當您將新區塊新增至附加 blob 時, 一律會將它附加至 blob 的結尾。 您無法更新或刪除附加 blob 中的現有區塊。 附加 blob 的區塊識別碼不會公開, 因為它們是用於區塊 blob。

附加 blob 中的每個區塊可以是不同的大小, 最多 4 MB, 而附加 blob 最多可包含50000個區塊。 因此, 附加 blob 的大小上限會稍微超過 195 GB (4 MB X 50000 區塊)。

下列範例會建立新的附加 blob, 並在其中附加一些資料, 以模擬簡單的記錄作業。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

如需這三種 blob 類型之間差異的詳細資訊, 請參閱[瞭解區塊 blob、分頁 blob 和附加 blob](https://msdn.microsoft.com/library/azure/ee691964.aspx) 。

## <a name="concurrent-access"></a>平行存取

若要支援從多個用戶端或多個進程實例平行存取 blob, 您可以使用**etag**或**租用**。

- **Etag** -提供方法來偵測 blob 或容器已由另一個進程修改過

- **租用**-提供一段時間取得對 blob 的獨佔、可續訂、寫入或刪除存取權的方法

如需詳細資訊, 請參閱[管理 Microsoft Azure 儲存體中的並行](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/)存取。

## <a name="naming-containers"></a>命名容器

Azure 儲存體中的每個 blob 都必須位於容器中。 容器會形成 blob 名稱的一部分。 例如, `mydata`是這些範例 blob uri 中容器的名稱:

- https://storagesample.blob.core.windows.net/mydata/blob1.txt
- https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg

容器名稱必須是有效的 DNS 名稱, 符合下列命名規則:

1. 容器名稱必須以字母或數位開頭, 且只能包含字母、數位和虛線 (-) 字元。
1. 每個虛線 (-) 字元的前後都必須是字母或數位;容器名稱中不允許連續的連字號。
1. 容器名稱中的所有字母都必須是小寫。
1. 容器名稱的長度必須介於3到63個字元之間。

請注意, 容器的名稱必須一律為小寫。 如果您在容器名稱中包含大寫字母, 或違反容器命名規則, 您可能會收到400錯誤 (不正確的要求)。

## <a name="managing-security-for-blobs"></a>管理 blob 的安全性

根據預設, Azure 儲存體會限制擁有帳戶存取金鑰的帳戶擁有者存取權, 以確保您的資料安全。 當您需要共用儲存體帳戶中的 blob 資料時, 請務必這麼做, 而不會危及帳戶存取金鑰的安全性。 此外, 您可以加密 blob 資料, 以確保它在網路上和 Azure 儲存體中都是安全的。

### <a name="controlling-access-to-blob-data"></a>控制 blob 資料的存取

根據預設, 儲存體帳戶中的 blob 資料只能供儲存體帳戶擁有者存取。 根據預設, 對 Blob 儲存體驗證要求時需要帳戶存取金鑰。 不過, 您可能會想要將某些 blob 資料提供給其他使用者。

### <a name="encrypting-blob-data"></a>加密 blob 資料

Azure 儲存體支援在用戶端和伺服器上加密 blob 資料。

## <a name="next-steps"></a>後續步驟

既然您已瞭解 Blob 儲存體的基本概念, 請參考下列連結以深入瞭解。

### <a name="tools"></a>工具

- [F#AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/)\
一F#種類型提供者, 可用來探索 Blob、資料表和佇列 Azure 儲存體資產, 並輕鬆地對其套用 CRUD 作業。

- [FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage)\
使用F# Microsoft Azure 表格儲存體服務的 API

- [Microsoft Azure 儲存體總管 (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)\
Microsoft 提供的免費獨立應用程式, 可讓您在 Windows、OS X 和 Linux 上以視覺化方式處理 Azure 儲存體資料。

### <a name="blob-storage-reference"></a>Blob 儲存體參考

- [適用于 .NET 的 Azure 儲存體 Api](/dotnet/api/overview/azure/storage)
- [Azure 儲存體 Services REST API 參考](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)

### <a name="related-guides"></a>相關指南

- [使用 Azure Blob 儲存體的消費者入門C#](https://azure.microsoft.com/resources/samples/storage-blob-dotnet-getting-started/)
- [在 Windows 上使用 AzCopy 命令列公用程式傳輸資料](/azure/storage/common/storage-use-azcopy)
- [使用 Linux 上的 AzCopy 命令列公用程式傳輸資料](/azure/storage/common/storage-use-azcopy-linux)
- [設定 Azure 儲存體連接字串](/azure/storage/common/storage-configure-connection-string)
- [Azure 儲存體小組的 Blog](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [快速入門：使用 .NET 在物件儲存體中建立 blob](/azure/storage/blobs/storage-quickstart-blobs-dotnet)

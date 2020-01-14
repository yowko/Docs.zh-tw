---
title: 使用 F# 開始使用 Azure 檔案儲存體
description: 使用 Azure 檔案儲存體在雲端中儲存檔案資料，並從 Azure 虛擬機器 (VM) 或執行 Windows 的內部部署應用程式掛接雲端檔案共用。
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: d58417e1e3161b958754e01423136a9cdd6a08a6
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2020
ms.locfileid: "75935621"
---
# <a name="get-started-with-azure-file-storage-using-f"></a>使用 F\# 開始使用 Azure 檔案儲存體

Azure 檔案儲存體是使用標準 [伺服器訊息區塊 (SMB) 通訊協定](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx)，在雲端中提供檔案共用功能的服務。 SMB 2.1 和 SMB 3.0 皆受到支援。 使用 Azure 檔案儲存體時，您可以快速地將依賴檔案共用功能的舊式應用程式移轉至 Azure，而不必浪費成本來重新撰寫程式。 在 Azure 虛擬機器、雲端服務或內部部署中執行的應用程式，可掛接雲端中的檔案共用，就像桌面應用程式掛接一般 SMB 共用一樣。 可同時掛接和存取檔案儲存體共用的應用程式元件數量沒有限制。

如需檔案儲存體的概念總覽，請參閱[.net guide for file storage](/azure/storage/storage-dotnet-how-to-use-files)。

## <a name="prerequisites"></a>必要條件：

若要使用本指南，您必須先[建立 Azure 儲存體帳戶](/azure/storage/storage-create-storage-account)。
您也需要此帳戶的儲存體存取金鑰。

## <a name="create-an-f-script-and-start-f-interactive"></a>建立F#腳本並啟動F#互動式

本文中的範例可用於F#應用程式或F#腳本中。 若要建立F#腳本，請在您F#的開發環境中建立具有 `.fsx` 副檔名的檔案，例如 `files.fsx`。

接下來，使用[套件管理員](package-management.md)（例如[Paket](https://fsprojects.github.io/Paket/)或[NuGet](https://www.nuget.org/) ），在您的腳本中使用 `#r` 指示詞來安裝 `WindowsAzure.Storage` 封裝和參考 `WindowsAzure.Storage.dll`。

### <a name="add-namespace-declarations"></a>加入命名空間宣告

在 `files.fsx` 檔案頂端新增下列 `open` 陳述式：

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>取得您的連接字串

在本教學課程中，您將需要 Azure 儲存體連接字串。 如需連接字串的詳細資訊，請參閱[設定儲存體連接字串](/azure/storage/storage-configure-connection-string)。

在本教學課程中，您將在腳本中輸入連接字串，如下所示：

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

不過，這**不建議**用於實際的專案。 儲存體帳戶金鑰很類似儲存體帳戶的根密碼。 請務必小心保護您的儲存體帳戶金鑰。 請避免轉發給其他使用者、進行硬式編碼，或將它儲存在其他人可以存取的純文字檔案。 如果您認為金鑰可能遭到入侵，您可以使用 Azure 入口網站重新產生金鑰。

對於實際的應用程式而言，維護儲存體連接字串的最佳方式是在設定檔中。 若要從設定檔提取連接字串，您可以執行下列動作：

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

是否使用 Azure Configuration Manager 可由您選擇。 您也可以使用 API，例如 .NET Framework 的 `ConfigurationManager` 類型。

### <a name="parse-the-connection-string"></a>解析連接字串

若要剖析連接字串，請使用：

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

這會傳回 `CloudStorageAccount`。

### <a name="create-the-file-service-client"></a>建立檔案服務用戶端

`CloudFileClient` 類型可讓您以程式設計方式使用儲存在檔案儲存體中的檔案。 以下是建立服務用戶端的其中一種方式：

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

現在您已準備好撰寫程式碼，以讀取資料，並將資料寫入檔案儲存體。

## <a name="create-a-file-share"></a>建立檔案共用

這個範例示範如何建立檔案共用（如果尚未存在）：

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a>建立根目錄和子目錄

在這裡，您會取得根目錄，並取得根目錄的子目錄。 如果兩者都不存在，您可以建立兩者。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a>將文字上傳為檔案

這個範例示範如何將文字上傳為檔案。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a>將檔下載至檔案的本機複本

在這裡，您會下載剛建立的檔案，並將內容附加至本機檔案。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a>設定檔案共用的大小上限

下列範例示範如何檢查共用的目前使用狀況，以及如何設定共用的配額。 必須呼叫 `FetchAttributes` 以填入共用的 `Properties`，並 `SetProperties` 將本機變更傳播至 Azure 檔案儲存體。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a>產生檔案或檔案共用的共用存取簽章

您可以為檔案共用或個別檔案產生共用存取簽章 (SAS)。 您也可以在檔案共用上建立共用存取原則，以管理共用存取簽章。 建議您建立共用存取原則，因為如果必須洩漏 SAS，它提供了一種撤銷 SAS 的方式。

在這裡，您會在共用上建立共用存取原則，然後使用該原則為共用中的檔案提供 SAS 的條件約束。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

如需建立與使用共用存取簽章的詳細資訊，請參閱[共用存取簽章 (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1)和[透過 Blob 儲存體建立與使用 SAS](/azure/storage/storage-dotnet-shared-access-signature-part-2)。

### <a name="copy-files"></a>複製檔案

您可以將檔案複製到另一個檔案或 blob，或將 blob 複製到檔案。 如果您要將 blob 複製到檔案，或將檔案複製到 blob，您*必須*使用共用存取簽章（SAS）來驗證來源物件，即使您是在相同的儲存體帳戶內進行複製也一樣。

### <a name="copy-a-file-to-another-file"></a>將檔案複製到另一個檔案

在這裡，您會將檔案複製到相同共用中的另一個檔案。 由於此複製作業是在相同儲存體帳戶中的檔案間進行複製，所以您可以使用共用金鑰驗證執行複製。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a>將檔案複製到 blob

在這裡，您會建立檔案，並將它複製到相同儲存體帳戶內的 blob。 您會建立來源檔案的 SAS，服務會在複製作業期間使用該檔案來驗證來源檔案的存取權。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

您可以用相同方式將 Blob 複製到檔案。 如果來源物件為 Blob，則請建立 SAS，以便在複製作業期間驗證該 Blob 存取權。

## <a name="troubleshooting-file-storage-using-metrics"></a>使用度量疑難排解檔案儲存體

Azure 儲存體分析支援檔案儲存體的計量。 利用度量資料，您可以追蹤要求及診斷問題。

您可以從[Azure 入口網站](https://portal.azure.com)啟用檔案儲存體的計量，也可以從F#下列方式進行：

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a>後續步驟

請參閱這些連結以取得 Azure 檔案儲存體的相關詳細資訊。

### <a name="conceptual-articles-and-videos"></a>概念性文章和影片

- [Azure 檔案儲存體：適用於 Windows 和 Linux 的無摩擦雲端 SMB 檔案系統](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [如何搭配使用 Azure 檔案儲存體與 Linux](/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a>檔案儲存體的工具支援

- [搭配使用 Azure PowerShell 與 Azure 儲存體](/azure/storage/storage-powershell-guide-full)
- [如何搭配使用 AzCopy 與 Microsoft Azure 儲存體](/azure/storage/storage-use-azcopy)
- [使用 Azure CLI 搭配 Azure 儲存體](/azure/storage/storage-azure-cli#create-and-manage-file-shares)

### <a name="reference"></a>參考資料

- [Storage Client Library for .NET 參考資料](https://msdn.microsoft.com/library/azure/mt347887.aspx)
- [檔案服務 REST API 參考](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a>部落格文章

- [Azure 檔案儲存體現已公開推出](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [Azure 檔案儲存體內部](https://azure.microsoft.com/blog/inside-azure-file-storage/)
- [Microsoft Azure 檔案服務簡介](https://docs.microsoft.com/archive/blogs/windowsazurestorage/introducing-microsoft-azure-file-service)
- [保留與 Microsoft Azure 檔案的連線](https://docs.microsoft.com/archive/blogs/windowsazurestorage/persisting-connections-to-microsoft-azure-files)

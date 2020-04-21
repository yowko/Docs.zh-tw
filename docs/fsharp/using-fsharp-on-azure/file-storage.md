---
title: 使用 F# 開始使用 Azure 檔案儲存體
description: 使用 Azure 檔案儲存體在雲端中儲存檔案資料，並從 Azure 虛擬機器 (VM) 或執行 Windows 的內部部署應用程式掛接雲端檔案共用。
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 1b38ee53f2f73f7b7f4ee12f712f487cb726d41e
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739600"
---
# <a name="get-started-with-azure-file-storage-using-f"></a>使用 F 開始使用 Azure 檔案儲存\#

Azure 檔案儲存是使用標準[伺服器訊息塊 (SMB) 協定](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx)在雲端中提供檔案共享的服務。 SMB 2.1 和 SMB 3.0 皆受到支援。 使用 Azure 檔案儲存體時，您可以快速地將依賴檔案共用功能的舊式應用程式移轉至 Azure，而不必浪費成本來重新撰寫程式。 在 Azure 虛擬機器、雲端服務或內部部署中執行的應用程式，可掛接雲端中的檔案共用，就像桌面應用程式掛接一般 SMB 共用一樣。 可同時掛接和存取檔案儲存體共用的應用程式元件數量沒有限制。

有關檔案儲存的概念概述[,請參閱檔案存儲的 .NET 指南](https://docs.microsoft.com/azure/storage/storage-dotnet-how-to-use-files)。

## <a name="prerequisites"></a>Prerequisites

要使用本指南,必須首先建立[Azure 儲存帳戶](https://docs.microsoft.com/azure/storage/storage-create-storage-account)。
您還需要此帳戶的儲存存取金鑰。

## <a name="create-an-f-script-and-start-f-interactive"></a>建立 F# 文稿與開始 F# 互動式

本文中的範例可用於 F# 應用程式或 F# 文稿。 要建立 F# 文稿,請建立`.fsx`一個 包含副`files.fsx`檔名的檔案 ,例如,在 F# 開發環境中。

接下來,使用[Paket](https://fsprojects.github.io/Paket/)或[NuGet](https://www.nuget.org/)等`WindowsAzure.Storage``#r`[套件管理器](package-management.md)使用 指令在文稿`WindowsAzure.Storage.dll`中安裝包和引用。

### <a name="add-namespace-declarations"></a>新增命名空間宣告

在 `files.fsx` 檔案頂端新增下列 `open` 陳述式：

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>取得您的連接字串

本教程需要 Azure 儲存連接字串。 有關連接字串的詳細資訊,請參考[設定儲存連線字串](https://docs.microsoft.com/azure/storage/storage-configure-connection-string)。

在本教學中,您將在文稿中輸入連接字串,如下所示:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

但是,**不建議**對實際項目進行此類使用。 儲存體帳戶金鑰很類似儲存體帳戶的根密碼。 請務必小心保護您的儲存體帳戶金鑰。 請避免轉發給其他使用者、進行硬式編碼，或將它儲存在其他人可以存取的純文字檔案。 如果您認為密鑰可能已洩露,則可以使用 Azure 門戶重新生成密鑰。

對於實際應用程式,維護存儲連接字串的最佳方法是在配置檔中。 要從設定檔中取得連接字串,可以執行以下操作:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

是否使用 Azure Configuration Manager 可由您選擇。 您還可以使用 API,如 .NET`ConfigurationManager`框架的類型 。

### <a name="parse-the-connection-string"></a>解析連接字串

要分析連接字串,請使用:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

這會傳回`CloudStorageAccount`。

### <a name="create-the-file-service-client"></a>建立檔案服務用戶端

該`CloudFileClient`類型使您能夠以程式設計方式使用儲存在檔案儲存中的檔案。 以下是建立服務用戶端的其中一種方式：

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

現在,您可以編寫從檔案儲存讀取數據並將數據寫入檔案存儲的代碼。

## <a name="create-a-file-share"></a>建立檔案共用

此範例展示如何建立檔案分享(如果檔案分享不存在):

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a>建立根目錄與子目錄

在這裡,您將獲得根目錄,並獲得根的子目錄。 如果它們不存在,則建立兩者。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a>將文字作為檔案上載

此示例演示如何將文本上傳為檔。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a>將檔案下載到檔案的本地複本

在這裡,您可以下載剛剛創建的檔,將內容追加到本地檔案中。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a>設定檔案共用的大小上限

下列範例示範如何檢查共用的目前使用狀況，以及如何設定共用的配額。 `FetchAttributes`必須呼叫 以填充共用`Properties`的`SetProperties`,並將本地更改傳播到 Azure 檔案儲存。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a>產生檔案或檔案共用的共用存取簽章

您可以為檔案共用或個別檔案產生共用存取簽章 (SAS)。 您也可以在檔案共用上建立共用存取原則，以管理共用存取簽章。 建議您建立共用存取原則，因為如果必須洩漏 SAS，它提供了一種撤銷 SAS 的方式。

在這裡,在共用上創建共享存取策略,然後使用該策略為共用中的檔上的 SAS 提供約束。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

如需建立與使用共用存取簽章的詳細資訊，請參閱[共用存取簽章 (SAS)](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1)和[透過 Blob 儲存體建立與使用 SAS](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-2)。

### <a name="copy-files"></a>複製檔案

您可以將檔案複製到其他檔案或 Blob,或將 Blob 複製到檔案。 如果要將 Blob 複製到檔案或檔案複製到 Blob,*則必須*使用共享存取簽名 (SAS) 對來源物件進行身份驗證,即使您正在同一儲存帳戶複製也是如此。

### <a name="copy-a-file-to-another-file"></a>將檔案複製到另一個檔案

在這裡,您將檔案複製到同一共用中的另一個檔。 由於此複製作業是在相同儲存體帳戶中的檔案間進行複製，所以您可以使用共用金鑰驗證執行複製。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a>將檔案複製到 Blob

在這裡,您將創建一個檔並將其複製到同一存儲帳戶中的 Blob。 為源文件創建 SAS,服務用於在複製操作期間對源文件的訪問進行身份驗證。

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

您可以用相同方式將 Blob 複製到檔案。 如果來源物件為 Blob，則請建立 SAS，以便在複製作業期間驗證該 Blob 存取權。

## <a name="troubleshooting-file-storage-using-metrics"></a>使用度量疑難排解檔案儲存體

Azure 儲存分析支援檔案存儲的指標。 利用度量資料，您可以追蹤要求及診斷問題。

可以從[Azure 門戶](https://portal.azure.com)啟用檔案存儲的指標,也可以從 F# 執行此操作,如下所示:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a>後續步驟

有關 Azure 檔存儲的詳細資訊,請參閱這些連結。

### <a name="conceptual-articles-and-videos"></a>概念性文章和影片

- [Azure 檔案儲存體：適用於 Windows 和 Linux 的無摩擦雲端 SMB 檔案系統](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [如何使用 Azure 檔案儲存與 Linux](https://docs.microsoft.com/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a>檔案儲存體的工具支援

- [搭配使用 Azure PowerShell 與 Azure 儲存體](https://docs.microsoft.com/azure/storage/storage-powershell-guide-full)
- [如何搭配使用 AzCopy 與 Microsoft Azure 儲存體](https://docs.microsoft.com/azure/storage/storage-use-azcopy)
- [使用 Azure CLI 上傳、下載及列出 Blob](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-cli#create-and-manage-file-shares)

### <a name="reference"></a>參考

- [Storage Client Library for .NET 參考資料](https://msdn.microsoft.com/library/azure/mt347887.aspx)
- [檔案服務 REST API 參考](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a>部落格文章

- [Azure 檔案儲存體現已公開推出](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [在 Azure 檔案儲存中](https://azure.microsoft.com/blog/inside-azure-file-storage/)
- [Microsoft Azure 檔案服務簡介](https://docs.microsoft.com/archive/blogs/windowsazurestorage/introducing-microsoft-azure-file-service)
- [保留與 Microsoft Azure 檔案的連線](https://docs.microsoft.com/archive/blogs/windowsazurestorage/persisting-connections-to-microsoft-azure-files)

---
title: '開始使用 Azure 檔案儲存體使用 F #'
description: 搭配 Azure 檔案儲存在雲端中儲存檔案資料，而且從 Azure 虛擬機器 (VM) 掛接您雲端的檔案共用或從內部部署應用程式執行 Windows。
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: conceptual
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: f4eb02bc3e4aca0653a4fa991c1593f988f1d1af
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="get-started-with-azure-file-storage-using-f"></a>開始使用 Azure 檔案儲存體使用 F # #

Azure 檔案儲存體是一項服務，提供在雲端中使用標準的檔案共用[伺服器訊息區塊 (SMB) 通訊協定](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx)。 支援 SMB 2.1 和 SMB 3.0。 使用 Azure 檔案儲存體，您可以移轉快速且昂貴的撰寫不依賴至 Azure 的檔案共用的舊版應用程式。 在 Azure 虛擬機器或雲端服務，或從內部部署用戶端執行的應用程式可以掛接在雲端中，將檔案共用，就像桌面應用程式裝載在典型的 SMB 共用。 任何數目的應用程式元件即可掛接或同時存取的儲存體檔案共用。

檔案儲存體概念的概觀，請參閱[檔案存放裝置的.NET 指南](/azure/storage/storage-dotnet-how-to-use-files)。

## <a name="prerequisites"></a>必要條件

若要使用本指南，您必須先[建立 Azure 儲存體帳戶](/azure/storage/storage-create-storage-account)。
您還需要此帳戶的儲存體存取金鑰。

## <a name="create-an-f-script-and-start-f-interactive"></a>建立 F # 指令碼，並開始 F # Interactive

這篇文章中的範例可以用於 F # 應用程式或 F # 指令碼。 若要建立 F # 指令碼，建立檔案之`.fsx`擴充功能，例如`files.fsx`，F # 開發環境中。

接下來，使用[封裝管理員](package-management.md)例如[Paket](https://fsprojects.github.io/Paket/)或[NuGet](https://www.nuget.org/)安裝`WindowsAzure.Storage`封裝和參考`WindowsAzure.Storage.dll`指令碼使用`#r`指示詞。

### <a name="add-namespace-declarations"></a>加入命名空間宣告

加入下列`open`上方的陳述式`files.fsx`檔案：

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>取得連接字串

此教學課程中，您將需要 Azure 儲存體連接字串。 如需連接字串的詳細資訊，請參閱[設定儲存體連接字串](/azure/storage/storage-configure-connection-string)。

教學課程中，您會輸入您的連接字串中指令碼中，像這樣：

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

不過，這是**不建議**用於真實的專案。 儲存體帳戶金鑰是類似於儲存體帳戶的根密碼。 一律為保護您的儲存體帳戶金鑰，請小心。 避免將其散發給其他使用者，硬式編碼，或將它儲存在其他人可以存取純文字檔案。 您可以重新產生您使用 Azure 入口網站，如果您認為可能已受到危害的金鑰。

用於真實的應用程式，以維護您的儲存體連接字串的最佳方式是在組態檔中。 若要從組態檔擷取連接字串，您可以：

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

使用 Azure 組態管理員是選擇性的。 您也可以使用例如.NET Framework API`ConfigurationManager`型別。

### <a name="parse-the-connection-string"></a>剖析連接字串

若要剖析的連接字串，使用：

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

這會傳回`CloudStorageAccount`。

### <a name="create-the-file-service-client"></a>建立檔案服務用戶端

`CloudFileClient`類型可讓您以程式設計方式使用檔案儲存體中儲存的檔案。 以下是如何建立服務用戶端：

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

現在您已準備好要寫入的資料來讀取和寫入資料檔案儲存體的程式碼。

## <a name="create-a-file-share"></a>建立檔案共用

這個範例示範如何建立檔案共用，如果不存在：

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a>建立根目錄和子目錄

這裡，您會取得目錄的根目錄，並取得根目錄的子目錄。 您建立這兩者如果它們不存在。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a>將文字上傳檔案

這個範例示範如何將文字當做檔案上傳。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a>將檔案下載至本機檔案的複本

這裡您下載剛才建立的檔案附加到本機檔案的內容。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a>設定檔案共用的大小上限

下列範例會示範如何檢查共用資源的目前使用量以及如何設定共用的配額。 `FetchAttributes` 必須先呼叫填入共用`Properties`，和`SetProperties`將本機變更傳播至 Azure 檔案儲存體。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a>產生的檔案或檔案共用的共用的存取簽章

您可以產生共用的存取簽章 (SAS) 的檔案共用，或針對個別檔案。 您也可以建立共用的存取原則來管理共用的存取簽章的檔案共用上。 建立共用的存取原則被建議，因為它提供撤銷 SAS，如果它應該會受到危害的方法。

在這裡，您建立共用存取原則共用上，，然後使用該原則的條件約束提供共用中的檔案上的 SAS。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

如需有關建立和使用共用的存取簽章的詳細資訊，請參閱[使用共用存取簽章 (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1)和[建立並使用 SAS，以使用 Blob 儲存體](/azure/storage/storage-dotnet-shared-access-signature-part-2)。

### <a name="copy-files"></a>將檔案複製

您可以將檔案複製到另一個檔案或 blob 或 blob 檔案。 如果您將 blob 複製到檔案或檔案的 blob，您*必須*使用共用的存取簽章 (SAS) 驗證來源物件，即使您要複製之相同的儲存體帳戶。

### <a name="copy-a-file-to-another-file"></a>將檔案複製到另一個檔案

在這裡，您將檔案複製到相同的共用中的另一個檔案。 因為相同的儲存體帳戶中的檔案之間，複製此複製操作，您可以使用共用金鑰驗證來進行複製。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a>將檔案複製到 blob

在這裡，您可以建立檔案並將它複製到相同的儲存體帳戶內的 blob。 您建立 SAS，使原始程式檔，以便讓服務使用在複製作業期間驗證來源檔案的存取權。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

您可以將 blob 複製檔案相同的方式。 如果來源物件是 blob，然後建立複製作業期間驗證存取該 blob 的 SAS。

## <a name="troubleshooting-file-storage-using-metrics"></a>疑難排解檔案存放裝置使用度量

Azure 儲存體分析度量資訊支援檔案存放裝置。 度量資料，您可以追蹤要求，以及診斷問題。

您可以啟用 從檔案儲存體度量[Azure 入口網站](https://portal.azure.com)，或您可以從 F # 中執行它，像這樣：

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a>後續步驟

請參閱下列連結取得 Azure 檔案儲存體的詳細資訊。

### <a name="conceptual-articles-and-videos"></a>概念性文章和影片

- [Azure 檔案儲存體： 格局的無耗損雲端 SMB 檔案系統的 Windows 和 Linux](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [如何使用 Linux 的 Azure 檔案儲存體](/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a>工具檔案存放裝置的支援

- [使用 Azure 儲存體的 Azure PowerShell](/azure/storage/storage-powershell-guide-full)
- [如何使用 Microsoft Azure 儲存體的 AzCopy](/azure/storage/storage-use-azcopy)
- [使用 Azure CLI 搭配 Azure 儲存體](/azure/storage/storage-azure-cli#create-and-manage-file-shares)

### <a name="reference"></a>參考資料

- [儲存體用戶端程式庫.NET 參考](https://msdn.microsoft.com/library/azure/mt347887.aspx)
- [檔案服務 REST API 參考](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a>部落格文章

- [Azure 檔案儲存體已上市](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [在 Azure 檔案儲存體](https://azure.microsoft.com/blog/inside-azure-file-storage/) 
- [介紹 Microsoft Azure 檔案服務](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/12/introducing-microsoft-azure-file-service/)
- [Microsoft Azure 檔案的持續連線](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/26/persisting-connections-to-microsoft-azure-files/)

---
title: 開始使用 Azure 檔案儲存體使用F#
description: 使用 Azure 檔案儲存體，在雲端中儲存檔案資料和從 Azure 虛擬機器 (VM) 掛接雲端檔案共用，或從內部部署應用程式執行 Windows。
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: fa6dadc863bb9116cfac5afd7cd22a724bc7afe2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62031222"
---
# <a name="get-started-with-azure-file-storage-using-f"></a>開始使用 Azure 檔案儲存體使用 F\#

Azure 檔案儲存體是一項服務，提供在雲端中使用標準的檔案共用[伺服器訊息區塊 (SMB) 通訊協定](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx)。 支援 SMB 2.1 和 SMB 3.0。 使用 Azure 檔案儲存體，您可以移轉舊版應用程式需要在 azure 檔案共用，快速且沒有成本高昂的重寫。 在 Azure 虛擬機器或雲端服務，或從內部部署用戶端執行的應用程式可以掛接雲端中的檔案共用，就像桌面應用程式掛接一般 SMB 共用。 任意數目的應用程式元件，然後掛接及同時存取檔案儲存體共用。

檔案儲存體概念的概觀，請參閱[檔案儲存體的.NET 指南](/azure/storage/storage-dotnet-how-to-use-files)。

## <a name="prerequisites"></a>必要條件

若要使用本指南，您必須先[建立 Azure 儲存體帳戶](/azure/storage/storage-create-storage-account)。
儲存體存取金鑰也需要此帳戶。

## <a name="create-an-f-script-and-start-f-interactive"></a>建立F#指令碼，然後啟動F#互動

這篇文章中的範例可以用於在F#應用程式或F#指令碼。 若要建立F#指令碼，建立的檔案`.fsx`擴充功能，例如`files.fsx`，請在您F#開發環境。

接下來，使用[套件管理員](package-management.md)這類[Paket](https://fsprojects.github.io/Paket/)或是[NuGet](https://www.nuget.org/)安裝`WindowsAzure.Storage`封裝和參考`WindowsAzure.Storage.dll`使用指令碼中`#r`指示詞。

### <a name="add-namespace-declarations"></a>加入命名空間宣告

新增下列`open`陳述式的`files.fsx`檔案：

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>取得連接字串

在本教學課程需要 Azure 儲存體連接字串。 如需有關連接字串的詳細資訊，請參閱 <<c0> [ 設定儲存體連接字串](/azure/storage/storage-configure-connection-string)。

教學課程中，您會輸入您的連接字串中您的指令碼，就像這樣：

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

不過，這是**不建議使用**實際的專案。 儲存體帳戶金鑰很類似儲存體帳戶的根密碼。 請務必小心保護您的儲存體帳戶金鑰。 請避免轉發給其他使用者，硬式編碼，或將它儲存在其他人可以存取純文字檔案。 您可以重新產生您使用 Azure 入口網站，如果您認為可能已遭盜用的金鑰。

實際的應用程式，來維護您的儲存體連接字串的最佳方式是在組態檔中。 若要從組態檔擷取連接字串，您可以這樣做：

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

使用 Azure Configuration Manager 是選擇性的。 您也可以使用 API，例如.NET Framework 的`ConfigurationManager`型別。

### <a name="parse-the-connection-string"></a>剖析連接字串

若要剖析的連接字串，請使用：

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

這會傳回`CloudStorageAccount`。

### <a name="create-the-file-service-client"></a>建立檔案服務用戶端

`CloudFileClient`類型可讓您以程式設計方式使用檔案儲存體中儲存的檔案。 若要建立服務用戶端的其中一個方法如下：

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

現在您已準備好撰寫程式碼來讀取資料，並將資料寫入至檔案儲存體。

## <a name="create-a-file-share"></a>建立檔案共用

此範例示範如何建立檔案共用，如果不存在：

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a>建立根目錄和子目錄

在這裡，您可以目錄的根目錄，並取得子目錄的根目錄。 如果您建立兩者已不存在。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a>將文字上載檔案

此範例示範如何上傳做為檔案的文字。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a>將檔案下載至本機檔案的複本

您在此下載剛才建立的檔案附加到本機檔案的內容。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a>設定檔案共用的大小上限

下列範例會示範如何檢查共用的目前使用量以及如何設定共用的配額。 `FetchAttributes` 必須先呼叫來填入共用`Properties`，和`SetProperties`將本機變更傳播至 Azure 檔案儲存體。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a>產生的檔案或檔案共用的共用的存取簽章

您可以產生共用的存取簽章 (SAS) 的檔案共用或個別的檔案。 您也可以建立共用的存取原則來管理共用的存取簽章的檔案共用上。 建立共用的存取原則建議，因為它提供一種撤銷 SAS，如果必須洩漏。

在這裡，您建立共用存取原則上的共用，然後使用該原則上的檔案共用中的 sas 提供條件約束。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

如需有關建立和使用共用的存取簽章的詳細資訊，請參閱 <<c0> [ 使用共用存取簽章 (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1)並[建立及使用具有 Blob 儲存體的 SAS](/azure/storage/storage-dotnet-shared-access-signature-part-2)。

### <a name="copy-files"></a>將檔案複製

您可以將檔案複製到另一個檔案或 blob 或 blob 檔案。 如果您將 blob 複製到檔案或檔案的 blob，您*必須*使用共用的存取簽章 (SAS) 驗證來源物件，即使您要複製相同的儲存體帳戶內。

### <a name="copy-a-file-to-another-file"></a>將檔案複製到另一個檔案

在這裡，您將檔案複製到相同共用中的另一個檔案。 因為此複製作業在相同的儲存體帳戶中的檔案間進行複製，您可以使用共用金鑰驗證來執行複製。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a>將檔案複製到 blob

在這裡，您會建立檔案並將它複製到相同的儲存體帳戶內的 blob。 您建立原始程式檔，供服務用來在複製作業期間驗證來源檔案的權限的 SAS。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

您可以相同的方式，將 blob 複製到檔案中。 如果來源物件是 blob，請建立 SAS，以便在複製作業期間驗證該 blob 的存取權。

## <a name="troubleshooting-file-storage-using-metrics"></a>使用度量疑難排解檔案儲存體

Azure 儲存體分析可支援檔案儲存體的度量。 利用度量資料，您可以追蹤要求，並診斷問題。

您可以從檔案儲存體度量[Azure 入口網站](https://portal.azure.com)，或者，您可以從F#如下所示：

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a>後續步驟

請參閱下列連結以取得 Azure 檔案儲存體的詳細資訊。

### <a name="conceptual-articles-and-videos"></a>概念性文章和影片

- [Azure 檔案儲存體： 無摩擦雲端 SMB 檔案系統的 Windows 和 Linux](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [如何搭配 Linux 使用 Azure 檔案儲存體](/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a>檔案儲存體的工具支援

- [使用 Azure PowerShell 與 Azure 儲存體](/azure/storage/storage-powershell-guide-full)
- [如何使用 AzCopy 與 Microsoft Azure 儲存體](/azure/storage/storage-use-azcopy)
- [使用 Azure CLI 搭配 Azure 儲存體](/azure/storage/storage-azure-cli#create-and-manage-file-shares)

### <a name="reference"></a>參考資料

- [For.NET 參考資料的儲存體用戶端程式庫](https://msdn.microsoft.com/library/azure/mt347887.aspx)
- [檔案服務 REST API 參考](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a>部落格文章

- [Azure 檔案儲存體現已正式推出](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [深入探討 Azure 檔案儲存體](https://azure.microsoft.com/blog/inside-azure-file-storage/) 
- [Microsoft Azure 檔案服務簡介](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/12/introducing-microsoft-azure-file-service/)
- [保留與 Microsoft Azure 檔案連線](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/26/persisting-connections-to-microsoft-azure-files/)

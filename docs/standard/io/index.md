---
title: "檔案和資料流 I-O | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IO namespace
- files, I/O
- System.IO namespace
- I/O [.NET Framework]
- streams, I/O
- data streams, I/O
ms.assetid: 4f4a33a9-66b7-4cd7-a285-4ad3e4276cd2
caps.latest.revision: 33
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 1fabc43044b6e0fa765a7c2f225add8b7eb923f5
ms.openlocfilehash: 1d0c203313b33aeba26aded268467b1a1b181118
ms.contentlocale: zh-tw
ms.lasthandoff: 05/02/2017

---
# <a name="file-and-stream-io"></a>檔案和資料流 I/O
檔案和資料流 I/O (輸入/輸出) 是指對儲存媒體來回傳輸資料。 在 .NET Framework 中，[System.IO](http://go.microsoft.com/fwlink/?LinkId=231142) 命名空間包含能夠以同步和非同步方式在資料流和檔案上進行讀取和寫入的類型。 這些命名空間還包含對檔案進行壓縮和解壓縮的類型，以及透過管道和序列埠進行通訊的類型。  
  
 檔案是具有永續性存放裝置的已排序具名位元組集合。 當您使用檔案時，也會處理目錄路徑、磁碟存放裝置，以及檔案和目錄名稱。 相反地，資料流是可以用來讀取和寫入備份存放區的位元組序列，這類備份存放區可以是數種儲存媒體的其中一種 (例如磁碟或記憶體)。 就像除了磁碟以外，還有多種備份存放區一樣，資料流的種類除了檔案資料流之外，還有其他數種，例如網路、記憶體和管道資料流。  
  
## <a name="files-and-directories"></a>檔案和目錄  
 您可以使用 <xref:System.IO?displayProperty=fullName> 命名空間中的類型與檔案和目錄互動。 例如，您可以取得及設定檔案和目錄的屬性，並且根據搜尋條件擷取檔案和目錄集合。  
  
 以下是常用的檔案和目錄類別：  
  
-   <xref:System.IO.File> - 提供建立、複製、刪除、移動和開啟檔案的靜態方法，並協助建立 <xref:System.IO.FileStream> 物件。  
  
-   <xref:System.IO.FileInfo> - 提供建立、複製、刪除、移動和開啟檔案的執行個體方法，並協助建立 <xref:System.IO.FileStream> 物件。  
  
-   <xref:System.IO.Directory> - 提供建立、移動和列舉目錄和子目錄的靜態方法。  
  
-   <xref:System.IO.DirectoryInfo> - 提供建立、移動和列舉目錄和子目錄的執行個體方法。  
  
-   <xref:System.IO.DirectoryInfo> - 提供以跨平台方式處理目錄字串的方法和屬性。  
  
 除了使用這些類別之外，Visual Basic 使用者還可以使用 <xref:Microsoft.VisualBasic.FileIO.FileSystem?displayProperty=fullName> 類別針對檔案 I/O 提供的方法。  
  
 請參閱[如何：複製目錄](../../../docs/standard/io/how-to-copy-directories.md)、[如何：建立目錄清單](http://msdn.microsoft.com/en-us/4d2772b1-b991-4532-a8a6-6ef733277e69)，以及[如何：列舉目錄和檔案](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)。  
  
## <a name="streams"></a>資料流  
 抽象基底類別 <xref:System.IO.Stream> 支援讀取和寫入位元組。 代表繼承自 <xref:System.IO.Stream> 類別之資料流的所有類別。 <xref:System.IO.Stream> 類別和它的衍生類別提供了資料來源和儲存機制的一般觀點，並且將程式設計人員與作業系統和基礎裝置的特有詳細資料加以隔離。  
  
 資料流包含三項基本作業：  
  
-   讀取 - 從資料流將資料傳送至資料結構，例如位元組陣列。  
  
-   寫入 - 從資料來源將資料傳送至資料流。  
  
-   搜尋 - 查詢和修改資料流內的目前位置。  
  
 依據基礎資料來源或儲存機制而定，資料流可能只支援其中部分功能。 例如，<xref:System.IO.Pipes.PipeStream> 類別不支援搜尋。 資料流的 <xref:System.IO.Stream.CanRead%2A>、<xref:System.IO.Stream.CanWrite%2A> 和 <xref:System.IO.Stream.CanSeek%2A> 屬性可指定資料流所支援的作業。  
  
 以下是部分常用的資料流類別：  
  
-   <xref:System.IO.FileStream> – 用於讀取和寫入檔案。  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> – 用於讀取和寫入至隔離儲存區中的檔案。  
  
-   <xref:System.IO.FileStream> – 用於讀取和寫入做為備份存放區的記憶體。  
  
-   <xref:System.IO.BufferedStream> – 用於改善讀取和寫入作業的效能。  
  
-   <xref:System.Net.Sockets.NetworkStream> – 用於透過網路通訊端讀取和寫入。  
  
-   <xref:System.IO.Pipes.PipeStream> – 用於透過匿名和具名管道讀取和寫入。  
  
-   <xref:System.Security.Cryptography.CryptoStream> – 用於將資料流連結至密碼編譯的轉換作業。  
  
 以非同步方式處理資料流的範例，請參閱[非同步檔案 I/O](../../../docs/standard/io/asynchronous-file-i-o.md)。  
  
## <a name="readers-and-writers"></a>讀取器和寫入器  
 <xref:System.IO?displayProperty=fullName> 命名空間提供從資料流讀取編碼字元以及將編碼字元寫入資料流的類型。 通常資料流是針對位元組輸入和輸出所設計。 讀取器和寫入器類型會處理編碼字元與位元組之間的轉換，讓資料流能夠完成作業。 每個讀取器和寫入器類別都會與資料流相關聯，可透過類別的 `BaseStream` 屬性擷取。  
  
 以下是常用的讀取器和寫入器類別：  
  
-   <xref:System.IO.BinaryReader> 和 <xref:System.IO.BinaryWriter> – 用於將基本資料類型當做二進位值讀取和寫入。  
  
-   <xref:System.IO.StreamReader> 和 <xref:System.IO.StreamWriter> – 使用編碼值在字元與位元組之間進行轉換的方式讀取和寫入字元。  
  
-   <xref:System.IO.StringReader> 和 <xref:System.IO.StringWriter> – 用於讀取和寫入字串中的字元。  
  
-   <xref:System.IO.TextReader> 和 <xref:System.IO.TextWriter> – 做為其他讀取和寫入二進位資料以外的字元與字串之讀取器和寫入器的抽象基底類別。  
  
 請參閱[如何：從檔案讀取文字](../../../docs/standard/io/how-to-read-text-from-a-file.md)、[如何：將文字寫入檔案](../../../docs/standard/io/how-to-write-text-to-a-file.md)、[如何：從字串讀取字元](../../../docs/standard/io/how-to-read-characters-from-a-string.md)，以及[如何：將字元寫入字串](../../../docs/standard/io/how-to-write-characters-to-a-string.md)。  
  
## <a name="asynchronous-io-operations"></a>非同步 I/O 作業  
 讀取或寫入大量資料可能會耗用大量資源。 如果您的應用程式需要保持對使用者的回應能力，您應該以非同步方式執行這些工作。 進行同步 I/O 作業時，UI 執行緒會遭到封鎖，直至耗用資源的作業完成為止。  開發 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式時請使用非同步 I/O 作業，避免造成應用程式停止運作的印象。  
  
 非同步成員在其名稱中包含 `Async`例如 <xref:System.IO.Stream.CopyToAsync%2A>、<xref:System.IO.Stream.FlushAsync%2A>、<xref:System.IO.Stream.ReadAsync%2A> 和 <xref:System.IO.Stream.WriteAsync%2A> 方法。 這些方法可搭配 `async` 和 `await` 關鍵字使用。  
  
 如需詳細資訊，請參閱[非同步檔案 I/O](../../../docs/standard/io/asynchronous-file-i-o.md)。  
  
## <a name="compression"></a>壓縮  
 壓縮是指縮減檔案大小以便儲存的程序。 解壓縮則是指擷取壓縮檔的內容使其成為可使用格式的程序。 <xref:System.IO.Compression?displayProperty=fullName> 命名空間包含壓縮及解壓縮檔案和資料流的類型。  
  
 以下是壓縮和解壓縮檔案和資料流時經常使用的類別：  
  
-   <xref:System.IO.Compression.ZipArchive> – 用於建立和解壓縮 zip 封存中的項目。  
  
-   <xref:System.IO.Compression.ZipArchiveEntry> – 用於表示已壓縮的檔案。  
  
-   <xref:System.IO.Compression.ZipFile> – 用於建立、解壓縮和開啟已壓縮的套件。  
  
-   <xref:System.IO.Compression.ZipFileExtensions> – 用於建立和解壓縮已壓縮套件中的項目。  
  
-   <xref:System.IO.Compression.DeflateStream> – 使用 Deflate 演算法來壓縮和解壓縮資料流。  
  
-   <xref:System.IO.Compression.GZipStream> – 以 gzip 資料格式壓縮和解壓縮資料流。  
  
 請參閱[如何：壓縮與解壓縮檔案](../../../docs/standard/io/how-to-compress-and-extract-files.md)。  
  
## <a name="isolated-storage"></a>隔離儲存區  
 隔離儲存區 (Isolated Storage) 為資料儲存機制，藉著定義標準化方式，將程式碼與儲存的資料產生關聯，以提供隔離和安全。 儲存區提供依使用者、組件和 (選擇性) 網域隔離的虛擬檔案系統。 隔離儲存區在應用程式未具備存取使用者檔案的權限時特別實用。 您可以藉由電腦的安全性原則所控制的方式儲存應用程式的設定或檔案。  
  
 隔離儲存區不適用於 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式，請改用 [Windows.Storage](http://msdn.microsoft.com/library/windows/apps/windows.storage.aspx) 命名空間中的應用程式資料類別。 如需詳細資訊，請參閱 Windows 開發人員中心的[應用程式資料](http://go.microsoft.com/fwlink/?LinkId=229175)。  
  
 以下是實作隔離儲存區時經常使用的類別：  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorage> – 提供隔離儲存區實作所使用的基底類別。  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFile> – 提供包含檔案和目錄的隔離存放區域。  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> – 公開隔離儲存區內的檔案。  
  
 請參閱[隔離儲存區](../../../docs/standard/io/isolated-storage.md)。  
  
## <a name="io-operations-in-windows-store-apps"></a>Windows 市集應用程式中的 I/O 作業  
 [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] 包含許多用於讀取和寫入資料流的類型，不過這個集合並未包含所有 .NET Framework I/O 類型。  
  
 以下是在 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式中使用 I/O 作業時要注意的一些重要差異：  
  
-   與檔案作業特別相關的類型 (例如 <xref:System.IO.File>、<xref:System.IO.FileInfo>、<xref:System.IO.Directory> 和 <xref:System.IO.DirectoryInfo>) 不包含在 [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] 中。 因此，請改用 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 的 [Windows.Storage](http://msdn.microsoft.com/library/windows/apps/windows.storage.aspx) 命名空間中的類型，例如 [StorageFile](http://msdn.microsoft.com/library/windows/apps/windows.storage.storagefile.aspx) 和 [StorageFolder](http://msdn.microsoft.com/library/windows/apps/windows.storage.storagefolder.aspx)。  
  
-   無法使用隔離儲存區，請改用[應用程式資料](http://go.microsoft.com/fwlink/?LinkId=229175)。  
  
-   使用非同步方法 (例如 <xref:System.IO.Stream.ReadAsync%2A> 和 <xref:System.IO.Stream.WriteAsync%2A>) 來防止封鎖 UI 執行緒。  
  
-   無法使用以路徑為基礎的壓縮類型 <xref:System.IO.Compression.ZipFile> 和 <xref:System.IO.Compression.ZipFileExtensions>。 因此，請改用 [Windows.Storage.Compression](http://msdn.microsoft.com/library/windows/apps/windows.storage.compression.aspx) 命名空間中的類型。  
  
 如有需要，您可以在 .NET Framework 資料流和 Windows 執行階段資料流之間進行轉換。 如需詳細資訊，請參閱[如何：在 .NET Framework 資料流與 Windows 執行階段資料流之間轉換](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)或 [System.IO.WindowsRuntimeStreamExtensions (英文)](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.aspx)。 <!--zz TODO: <xref:System.IO.WindowsRuntimeStreamExtensions>--> 
  
 如需 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式中 I/O 作業的詳細資訊，請參閱 Windows 開發人員中心的[快速入門：讀取和寫入檔案](http://go.microsoft.com/fwlink/p/?LinkId=243072)。  
  
## <a name="io-and-security"></a>I/O 和安全性  
 當您使用 <xref:System.IO?displayProperty=fullName> 命名空間中的類別時，必須遵循作業系統安全性需求，例如存取控制清單 (ACL)，以控制對檔案和目錄的存取。 除了 <xref:System.Security.Permissions.FileIOPermission> 需求，還有這項需求。 您可以用程式設計的方式管理 ACL。 如需詳細資訊，請參閱[如何：新增或移除存取控制清單項目](../../../docs/standard/io/how-to-add-or-remove-access-control-list-entries.md)。  
  
 預設安全性原則可避免網際網路或內部網路應用程式存取使用者電腦上的檔案。 因此，撰寫將透過網際網路或內部網路下載的程式碼時，請不要使用需要實體檔案路徑的 I/O 類別。 對於傳統 .NET Framework 應用程式請改用[隔離儲存區](../../../docs/standard/io/isolated-storage.md)，對於 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式則改用[應用程式資料](http://go.microsoft.com/fwlink/?LinkId=229175)。  
  
 只會對已建構的資料流進行安全性檢查。 因此，請不要開啟資料流，然後將它傳遞至較不受信任的程式碼或應用程式定義域。  
  
## <a name="related-topics"></a>相關主題  
  
-   [一般 I/O 工作](../../../docs/standard/io/common-i-o-tasks.md)  
  
 提供與檔案、目錄和資料流相關聯的 I/O 工作清單，並且連結至每一項工作的相關內容和範例。  
  
-   [非同步檔案 I/O](../../../docs/standard/io/asynchronous-file-i-o.md)  
  
 描述非同步 I/O 的效能利益和基本作業。  
  
-   [隔離儲存區](../../../docs/standard/io/isolated-storage.md)  
  
 描述資料儲存機制，此機制藉著定義標準化方式將程式碼與儲存的資料產生關聯，以提供隔離和安全。  
  
-   [管道](../../../docs/standard/io/pipe-operations.md)  
  
 描述 .NET Framework 中的非同步與具名管道作業。  
  
-   [記憶體對應檔案](../../../docs/standard/io/memory-mapped-files.md)  
  
 描述記憶體對應檔案，這些檔案包含磁碟檔案在虛擬記憶體中的內容。 您可以使用記憶體對應檔案來編輯超大的檔案，以及建立供處理序間通訊使用的共用記憶體。


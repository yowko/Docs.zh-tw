---
title: 檔案與資料流 I/O - .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- IO namespace
- files, I/O
- System.IO namespace
- I/O [.NET Framework]
- streams, I/O
- data streams, I/O
ms.assetid: 4f4a33a9-66b7-4cd7-a285-4ad3e4276cd2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a8d95a347237b15dfa55586bb15fe605bd5c7a94
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947117"
---
# <a name="file-and-stream-io"></a>檔案和資料流 I/O

檔案和資料流 I/O (輸入/輸出) 是指對儲存媒體來回傳輸資料。 在 .NET Framework 中，`System.IO` 命名空間包含能夠以同步和非同步方式在資料流和檔案上進行讀取和寫入的類型。 這些命名空間還包含對檔案進行壓縮和解壓縮的類型，以及透過管道和序列埠進行通訊的類型。

檔案是具有永續性存放裝置的已排序具名位元組集合。 當您使用檔案時，也會處理目錄路徑、磁碟存放裝置，以及檔案和目錄名稱。 相反地，資料流是可以用來讀取和寫入備份存放區的位元組序列，這類備份存放區可以是數種儲存媒體的其中一種 (例如磁碟或記憶體)。 就像除了磁碟以外，還有多種備份存放區一樣，資料流的種類除了檔案資料流之外，還有其他數種，例如網路、記憶體和管道資料流。

## <a name="files-and-directories"></a>檔案及目錄

您可以使用 <xref:System.IO?displayProperty=nameWithType> 命名空間中的類型與檔案和目錄互動。 例如，您可以取得及設定檔案和目錄的屬性，並且根據搜尋條件擷取檔案和目錄集合。

如需 Windows 系統的路徑命名慣例及檔案路徑表達方式，包括 .NET Core 1.1 及更新版本和 .NET Framework 4.6.2 及更新版本中支援的 DOS 裝置語法，請參閱 [Windows 系統上的檔案路徑格式](file-path-formats.md)。

以下是常用的檔案和目錄類別：

- <xref:System.IO.File> - 提供建立、複製、刪除、移動和開啟檔案的靜態方法，並協助建立 <xref:System.IO.FileStream> 物件。

- <xref:System.IO.FileInfo> - 提供建立、複製、刪除、移動和開啟檔案的執行個體方法，並協助建立 <xref:System.IO.FileStream> 物件。

- <xref:System.IO.Directory> - 提供建立、移動和列舉目錄和子目錄的靜態方法。

- <xref:System.IO.DirectoryInfo> - 提供建立、移動和列舉目錄和子目錄的執行個體方法。

- <xref:System.IO.Path> - 提供以跨平台方式處理目錄字串的方法和屬性。

您應該在呼叫檔案系統方法時，一律提供強固的例外狀況處理。 如需詳細資訊，請參閱[處理 I/O 錯誤](handling-io-errors.md)。

除了使用這些類別之外，Visual Basic 使用者還可以使用 <xref:Microsoft.VisualBasic.FileIO.FileSystem?displayProperty=nameWithType> 類別針對檔案 I/O 提供的方法。

請參閱[如何：複製目錄](how-to-copy-directories.md)，[如何：建立目錄清單](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))，及[如何：列舉目錄與檔案](how-to-enumerate-directories-and-files.md)。

## <a name="streams"></a>資料流

抽象基底類別 <xref:System.IO.Stream> 支援讀取和寫入位元組。 代表繼承自 <xref:System.IO.Stream> 類別之資料流的所有類別。 <xref:System.IO.Stream> 類別和它的衍生類別提供了資料來源和儲存機制的一般觀點，並且將程式設計人員與作業系統和基礎裝置的特有詳細資料加以隔離。

資料流包含三項基本作業：

- 讀取 - 從資料流將資料傳送至資料結構，例如位元組陣列。

- 寫入 - 從資料來源將資料傳送至資料流。

- 搜尋 - 查詢和修改資料流內的目前位置。

依據基礎資料來源或儲存機制而定，資料流可能只支援其中部分功能。 例如，<xref:System.IO.Pipes.PipeStream> 類別不支援搜尋。 資料流的 <xref:System.IO.Stream.CanRead%2A>、<xref:System.IO.Stream.CanWrite%2A> 和 <xref:System.IO.Stream.CanSeek%2A> 屬性會指定資料流支援的作業。

以下是部分常用的資料流類別：

- <xref:System.IO.FileStream> – 用於讀取和寫入檔案。

- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> – 用於讀取和寫入位於隔離儲存區中的檔案。

- <xref:System.IO.MemoryStream> – 用於讀取和寫入做為備份存放區的記憶體。

- <xref:System.IO.BufferedStream> – 用於改善讀取和寫入作業的效能。

- <xref:System.Net.Sockets.NetworkStream> – 用於透過網路通訊端讀取和寫入。

- <xref:System.IO.Pipes.PipeStream> – 用於透過匿名和具名管道讀取和寫入。

- <xref:System.Security.Cryptography.CryptoStream> – 用於將資料流連結至密碼編譯的轉換作業。

以非同步方式處理資料流的範例，請參閱[非同步檔案 I/O](asynchronous-file-i-o.md)。

## <a name="readers-and-writers"></a>讀取器及寫入器

<xref:System.IO?displayProperty=nameWithType> 命名空間提供從資料流讀取編碼字元以及將編碼字元寫入資料流的類型。 通常資料流是針對位元組輸入和輸出所設計。 讀取器和寫入器類型會處理編碼字元與位元組之間的轉換，讓資料流能夠完成作業。 每個讀取器和寫入器類別都會與資料流相關聯，可透過類別的 `BaseStream` 屬性擷取。

以下是常用的讀取器和寫入器類別：

- <xref:System.IO.BinaryReader> 和 <xref:System.IO.BinaryWriter> – 用於將基本資料類型當做二進位值讀取和寫入。

- <xref:System.IO.StreamReader> 和 <xref:System.IO.StreamWriter> – 使用編碼值在字元與位元組之間進行轉換的方式讀取和寫入字元。

- <xref:System.IO.StringReader> 和 <xref:System.IO.StringWriter> – 從字串讀取字元以及將字元寫入字串。

- <xref:System.IO.TextReader> 和 <xref:System.IO.TextWriter> – 做為其他讀取和寫入二進位資料以外的字元與字串之讀取器和寫入器的抽象基底類別。

請參閱[如何：從檔案讀取文字](how-to-read-text-from-a-file.md)，[如何：將文字寫入檔案](how-to-write-text-to-a-file.md)，[如何：從字串讀取字元](how-to-read-characters-from-a-string.md)，及[如何：將字元寫入字串](how-to-write-characters-to-a-string.md)。

## <a name="asynchronous-io-operations"></a>非同步 I/O 作業

讀取或寫入大量資料可能會耗用大量資源。 如果您的應用程式需要保持對使用者的回應能力，您應該以非同步方式執行這些工作。 進行同步 I/O 作業時，UI 執行緒會遭到封鎖，直至耗用資源的作業完成為止。  開發 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式時請使用非同步 I/O 作業，避免造成應用程式停止運作的印象。

非同步成員的名稱中包含 `Async`，例如 <xref:System.IO.Stream.CopyToAsync%2A>、<xref:System.IO.Stream.FlushAsync%2A>、<xref:System.IO.Stream.ReadAsync%2A> 和 <xref:System.IO.Stream.WriteAsync%2A> 方法。 這些方法可搭配 `async` 和 `await` 關鍵字使用。

如需詳細資訊，請參閱[非同步檔案 I/O](asynchronous-file-i-o.md)。

## <a name="compression"></a>壓縮

壓縮是指縮減檔案大小以便儲存的程序。 解壓縮則是指擷取壓縮檔的內容使其成為可使用格式的程序。 <xref:System.IO.Compression?displayProperty=nameWithType> 命名空間包含壓縮及解壓縮檔案和資料流的類型。

以下是壓縮和解壓縮檔案和資料流時經常使用的類別：

- <xref:System.IO.Compression.ZipArchive> – 用於建立和擷取 zip 封存中的項目。

- <xref:System.IO.Compression.ZipArchiveEntry> – 用於表示壓縮檔。

- <xref:System.IO.Compression.ZipFile> – 用於建立、擷取和開啟壓縮的封裝。

- <xref:System.IO.Compression.ZipFileExtensions> – 用於建立和擷取壓縮封裝中的項目。

- <xref:System.IO.Compression.DeflateStream> – 使用 Deflate 演算法壓縮及解壓縮資料流。

- <xref:System.IO.Compression.GZipStream> – 以 gzip 資料格式壓縮和解壓縮資料流。

請參閱[如何：壓縮與解壓縮檔案](how-to-compress-and-extract-files.md)。

## <a name="isolated-storage"></a>隔離儲存區 (Isolated Storage)

隔離儲存區 (Isolated Storage) 為資料儲存機制，藉著定義標準化方式，將程式碼與儲存的資料產生關聯，以提供隔離和安全。 儲存區提供依使用者、組件和 (選擇性) 網域隔離的虛擬檔案系統。 隔離儲存區在應用程式未具備存取使用者檔案的權限時特別實用。 您可以藉由電腦的安全性原則所控制的方式儲存應用程式的設定或檔案。

隔離儲存區 (Isolated Storage) 不適用於 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式，請改為使用 <xref:Windows.Storage?displayProperty=nameWithType> 命名空間中的應用程式資料類別。 如需詳細資訊，請參閱[應用程式資料](https://docs.microsoft.com/previous-versions/windows/apps/hh464917%28v=win.10%29)。

以下是實作隔離儲存區時經常使用的類別：

- <xref:System.IO.IsolatedStorage.IsolatedStorage> – 提供隔離儲存區實作所使用的基底類別。

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile> – 提供包含檔案和目錄的隔離存放區域。

- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> - 公開隔離儲存區內的檔案。

請參閱[隔離儲存區](isolated-storage.md)。

## <a name="io-operations-in-windows-store-apps"></a>在 Windows 市集應用程式中的 I/O 作業

[!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] 包含許多用於讀取和寫入資料流的類型，不過這個集合並未包含所有 .NET Framework I/O 類型。

以下是在 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式中使用 I/O 作業時要注意的一些重要差異：

- <xref:System.IO.File> 中未包含與檔案作業特別相關的類型，例如 <xref:System.IO.FileInfo>、<xref:System.IO.Directory>、<xref:System.IO.DirectoryInfo> 和 [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]。 您應該改為使用 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 之 <xref:Windows.Storage?displayProperty=nameWithType> 命名空間中的型別，例如 <xref:Windows.Storage.StorageFile> 與 <xref:Windows.Storage.StorageFolder>。

- 無法使用隔離儲存區，請改用[應用程式資料](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10))。

- 使用非同步方法，例如 <xref:System.IO.Stream.ReadAsync%2A> 和 <xref:System.IO.Stream.WriteAsync%2A>，防止封鎖 UI 執行緒。

- 無法使用路徑壓縮類型 <xref:System.IO.Compression.ZipFile> 和 <xref:System.IO.Compression.ZipFileExtensions>。 您應該改為使用 <xref:Windows.Storage.Compression?displayProperty=nameWithType> 命名空間中的型別。

如有需要，您可以在 .NET Framework 資料流和 Windows 執行階段資料流之間進行轉換。 如需詳細資訊，請參閱[如何：在 .NET Framework 資料流及 Windows 執行階段資料流之間](how-to-convert-between-dotnet-streams-and-winrt-streams.md)或 <xref:System.IO.WindowsRuntimeStreamExtensions> 之間轉換。

如需有關在 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式中 I/O 作業的詳細資訊，請參閱[快速入門：讀取及寫入檔案](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10))。

## <a name="io-and-security"></a>I/O 及安全性

當您使用 <xref:System.IO?displayProperty=nameWithType> 命名空間中的類別時，必須遵循作業系統安全性需求，例如存取控制清單 (ACL)，以控制對檔案和目錄的存取。 任何 <xref:System.Security.Permissions.FileIOPermission> 需求上都會附加這個需求。 您可以用程式設計的方式管理 ACL。 如需詳細資訊，請參閱[如何：新增或移除存取控制清單項目](how-to-add-or-remove-access-control-list-entries.md)。

預設安全性原則可避免網際網路或內部網路應用程式存取使用者電腦上的檔案。 因此，撰寫將透過網際網路或內部網路下載的程式碼時，請不要使用需要實體檔案路徑的 I/O 類別。 對於傳統 .NET Framework 應用程式請改用[隔離儲存區](isolated-storage.md)，對於 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式則改用[應用程式資料](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10))。

只會對已建構的資料流進行安全性檢查。 因此，請不要開啟資料流，然後將它傳遞至較不受信任的程式碼或應用程式定義域。

## <a name="related-topics"></a>相關主題

- [一般 I/O 工作](common-i-o-tasks.md)\
提供與檔案、目錄和資料流相關聯的 I/O 工作清單，並且連結至每一項工作的相關內容和範例。

- [非同步檔案 I/O](asynchronous-file-i-o.md)\
描述非同步 I/O 的效能利益和基本作業。

- [隔離儲存區](isolated-storage.md)\
描述資料儲存機制，此機制藉著定義標準化方式將程式碼與儲存的資料產生關聯，以提供隔離和安全。

- [管道](pipe-operations.md)\
描述 .NET Framework 中的非同步與具名管道作業。

- [與記憶體對應的檔案](memory-mapped-files.md)\
描述記憶體對應檔案，這些檔案包含磁碟檔案在虛擬記憶體中的內容。 您可以使用記憶體對應檔案來編輯超大的檔案，以及建立供處理序間通訊使用的共用記憶體。
---
title: ".NET Framework 4.5 中的應用程式相容性 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application compatibility, .NET Framework
- breaking changes [.NET Framework]
ms.assetid: 5c50747c-806c-44a9-ac58-5bbe12a284fa
caps.latest.revision: 76
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 19006cc5f24ffc66b92e53e8174c6bd33c249679
ms.openlocfilehash: 5f63c3217b6def96240447501247d22a1058cacf
ms.contentlocale: zh-tw
ms.lasthandoff: 05/22/2017

---
# <a name="application-compatibility-in-the-net-framework-45"></a>.NET Framework 4.5 中的應用程式相容性
本主題描述 .NET Framework 4 與 4.5 之間的應用程式相容性問題，包括依據客戶意見所做的修正和變更。 大多數變更都不需要您的應用程式進行任何設計修改。 對於可能涉及修改的變更，請參閱表格的 [影響] 一欄。  
  
> [!IMPORTANT]
>  請注意，[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 不支援 [!INCLUDE[winxp](../../../includes/winxp-md.md)]。  
  
 如需 .NET Framework 4.5 和 4.5.1 之間的相容性問題，請參閱 [4.5.1 中的應用程式相容性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-1.md)。  
  
 本主題描述下列領域中值得注意的變更：  
  
-   [核心](#core)  
  
-   [Data](#sql)  
  
-   [網路](#network)  
  
-   [序列化](#serialize)  
  
-   [列印](#Printing)  
  
-   [工具和資源](#tools)  
  
-   [ASP.NET](#asp)  
  
-   [ClickOnce](#ClickOnce)  
  
-   [Managed Extensibility Framework (MEF)](#mef)  
  
-   [Web 應用程式](#web)  
  
-   [Windows Communication Foundation (WCF)](#wcf)  
  
-   [Windows Forms](#winForms)  
  
-   [Windows Presentation Foundation (WPF)](#wpf)  
  
-   [Windows Workflow Foundation (WF)](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5.md#wwf)  
  
-   [XML、XSLT](#xml)  
  
 本主題的討論範圍將不會涵蓋 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中已宣告為過時的類型和成員。 如需這些項目的清單，請參閱[類別庫中的過時功能](../../../docs/framework/whats-new/whats-obsolete.md)。 如需新功能的詳細資訊，請參閱[新功能](../../../docs/framework/whats-new/index.md)。  
  
<a name="core"></a>   
## <a name="core"></a>核心  
 除了下列的應用程式相容性問題之外，也請參閱序列化相關問題的[序列化](#serialize)區段。  
  
|功能|變更|影響|  
|-------------|------------|------------|  
|<xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%28System.Collections.Concurrent.BlockingCollection%7B%600%7D%5B%5D%2C%600%40%29?displayProperty=fullName> 和 <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny%2A?displayProperty=fullName> 方法|<xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%28System.Collections.Concurrent.BlockingCollection%7B%600%7D%5B%5D%2C%600%40%29?displayProperty=fullName> 方法不再傳回 -1 或擲回例外狀況。 如果其中一個集合標記為已完成，則 <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny%2A?displayProperty=fullName> 方法將不再擲回例外狀況。|這項變更能夠讓您在其中一個集合為空集合或已完成，而另一個集合仍有可擷取的項目時處理集合。|  
|<xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=fullName>|如果使用 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 建置編譯之規則運算式的組件，但以 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]為目標，嘗試在安裝 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 的系統上執行該組件中的其中一個規則運算式時，會擲回例外狀況。|若要解決這個問題，您可以執行下列任何一項操作：<br /><br /> 使用 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 建置包含規則運算式的組件。<br /><br /> 使用解譯的規則運算式。|  
|<xref:System.Threading.Tasks.Task?displayProperty=fullName> 處置|除了 `Task.IAsyncResult.AsyncWaitHandle` 以外，<xref:System.Threading.Tasks.Task?displayProperty=fullName> 方法將不再於處置物件之後擲回 <xref:System.ObjectDisposedException> 例外狀況。|這項變更支援使用快取的工作。 例如，方法可能傳回快取的工作來表示已完成的作業，而不配置新的工作。 舊版的 .NET Framework 並未提供這項功能，因為工作的任何消費者都可能會處置它，使它變得無法使用。|  
|<xref:System.Threading.Tasks.Task?displayProperty=fullName> 作業中未觀察到的例外狀況|由於 <xref:System.Threading.Tasks.Task?displayProperty=fullName> 類別代表非同步作業，因此它會攔截非同步處理期間發生的所有非嚴重的例外狀況。 在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中，如果未觀察到某個例外狀況，而您的程式碼絕不會等候這項工作，則該例外狀況將不再於完成項執行緒上傳播，並且會在記憶體回收期間損毀處理序。|這項變更可以增強使用 <xref:System.Threading.Tasks.Task> 類別執行未觀察到的非同步處理之應用程式的可靠性。 前述行為可以藉著為 <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=fullName> 事件提供適當的處理常式進行還原。|  
|含逾時引數的 <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=fullName> 方法|在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 中，這些方法的行為不一致。 逾時過期時，如果在方法呼叫之前已完成或取消一個或多個工作，則方法會擲回 <xref:System.AggregateException> 例外狀況。 當逾時過期時，如果在方法呼叫之前沒有任何已完成或取消的工作，但是有一個或多個工作在方法呼叫之後進入這兩種狀態，則方法會傳回 `false`。<br /><br /> 在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中，如果逾時間隔到期時仍有任何工作正在執行，這些方法多載現在會傳回 `false`，而只有在取消輸入工作 (不論是在方法呼叫之前或之後取消)，且沒有其他工作仍在執行時，才會擲回 <xref:System.AggregateException> 例外狀況。|這項變更可以讓方法的行為一致。 不過，如果至少有一項工作已發生錯誤，或是在逾時過期之前就已取消，則應用程式程式碼有可能 (但不常見) 倚賴已啟用逾時的 <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=fullName> 多載來擲回例外狀況。 在這種情況下，可針對相同目的使用 <xref:System.Threading.Tasks.Task.IsCanceled%2A?displayProperty=fullName> 屬性。|  
|支援多目標時的類型轉送|新的 CodeDOM 功能可讓編譯器針對鎖定的 mscorlib.dll 版本而非 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 版的 mscorlib.dll 進行編譯。|這項變更可在 CodeDOM 找到已進行類型轉送的兩個類型定義時，阻止發出編譯器警告 (若警告視為錯誤，則會阻止編譯失敗)。 只有在同一個位置中混用不同的參考組件版本時，這項變更才會出現非預期的副作用。|  
|<xref:System.Collections.Generic.List%601.ForEach%2A?displayProperty=fullName>|如果集合中的元素經過修改，則列舉值會擲回 <xref:System.InvalidOperationException> 例外狀況。|這項變更只適用於以 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 為目標的應用程式，而且應該不會有負面影響。 這樣可保護資料的完整性，並且更能識別出競爭條件。|  
|<xref:System.Uri?displayProperty=fullName>|國際資源識別項 (IRI) 剖析中有兩項變更會影響以 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 為目標之應用程式中的 URI：<br /><br /> [\<iriParsing>](../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md) 預設為啟用，而且無法關閉。 以往它是預設為停用。<br /><br /> 將不再對 URI 的非主機部分執行 Unicode 正規化表單 C (NFC)。 以往在 `<iriParsing>` 啟用時，會對整個 URI 執行 NFC。|未來將不會對包含非 NFC (正規化表單 C) 正規化檔案名稱的 URI 進行表單 C 正規化。 如果 IRI 剖析使用非正規化字串存取具有正規化檔案名稱的檔案，就可能導致應用程式失敗。 這種情況只會影響以 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 為目標的應用程式。|  
|<xref:System.Uri?displayProperty=fullName>|無效的 `mailto:` URL 會在 <xref:System.Uri> 類別建構函式中擲回例外狀況。|這種情況只會影響重新編譯且以 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 為目標的應用程式。|  
|<xref:System.Uri?displayProperty=fullName>|若是以 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]為目標的應用程式，則會保留原始 URI 字串中路徑區段結尾的點 (例如 `http://www.proseware.com/LLC./About.aspx`)。 請注意，剛好包含一個或兩個點的路徑區段 (例如 `http://www.proseware.com/..` 或 `http://www.proseware.com/./default.htm`) 會遭到移除，但是包含兩個以上連續點的路徑區段 (例如 `http://localhost/dir1/.../dir2`) 則會保留。|這項變更只會影響以 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 為目標的應用程式。 倚賴將會遭移除之結尾點的應用程式可能會失敗。|  
|<xref:System.Uri?displayProperty=fullName>|在鎖定 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]為目標的應用程式中，允許在 `file://` URI 中進行查詢。由於 ? 字元會解譯為路徑的一部分，因此不會逸出該字元。|這項變更只會影響以 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 為目標的應用程式。 依賴逸出 ? 字元的應用程式可能會失敗。|  
|<xref:System.Uri?displayProperty=fullName>|在鎖定 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]為目標的應用程式中，從 U+0080 到 U+009F 的 Unicode 控制字元編碼不正確。|一般而言，不會在 URI 中使用 Unicode 控制字元。|  
|<xref:System.Uri.EscapeDataString%2A?displayProperty=fullName>、<xref:System.Uri.EscapeUriString%2A?displayProperty=fullName> 和 <xref:System.Uri.UnescapeDataString%2A?displayProperty=fullName>|保留和非保留字元的清單現在支援 [RFC 3986](http://tools.ietf.org/html/rfc3986)。|特定變更：<br /><br /> <xref:System.Uri.EscapeDataString%2A> 會根據 RFC 3986 逸出保留字元。<br /><br /> <xref:System.Uri.EscapeUriString%2A> 不會逸出保留字元。<br /><br /> 如果 <xref:System.Uri.UnescapeDataString%2A> 遇到無效的逸出序列，則不會擲回例外狀況。<br /><br /> 非保留的逸出字元不逸出。|  
|<xref:System.Uri.IsWellFormedUriString%2A?displayProperty=fullName>|從 .NET Framework 4.5 開始，字串一律根據 [RFC 3986](http://tools.ietf.org/html/rfc3986) 和 [RFC 3987](http://tools.ietf.org/html/rfc3987)視為語式正確。 在舊版 .NET Framework 中，只有在啟用 URI 剖析和 IDN 剖析時，字串才會根據 RFC 3986 和 RFC 3987 視為語式正確。|對於目標為 .NET Framework 4.5 或更新版本的應用程式，此方法會替目標為舊版 .NET Framework 的應用程式視為語式正確的部分 URI 傳回 `false`。 例如，第一個區段包括冒號的相對 URI ("2013.05.29_14:33:41") 不會再視為語式正確。<br /><br /> 請注意，這項變更只會影響目標為 .NET Framework 4.5 或更新版本的應用程式。|  
|<xref:System.Threading.Tasks.TaskFactory.FromAsync%2A?displayProperty=fullName>|<xref:System.Threading.Tasks.TaskFactory.FromAsync%2A?displayProperty=fullName> 現在可以存取 <xref:System.IAsyncResult.CompletedSynchronously%2A?displayProperty=fullName> 屬性。 現在 <xref:System.IAsyncResult.CompletedSynchronously%2A?displayProperty=fullName> 的實作不正確，可能造成 <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A?displayProperty=fullName> 方法呼叫中未定義的行為。|如果 <xref:System.IAsyncResult.CompletedSynchronously%2A?displayProperty=fullName> 屬性的實作不當傳回 `true`，則產生的工作將不會完成。|  
  
<a name="sql"></a>   
## <a name="data"></a>資料  
  
### <a name="sqlclient"></a>SQLClient  
  
|功能|變更|影響|  
|-------------|------------|------------|  
|可從 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 下執行 Managed 程式碼連接至 SQL Server 資料庫的功能。|現有的同步處理應用程式開發介面程式碼路徑已經過修改，並加入非同步支援。|若非 IFS Winsock Base Service Provider (BSP) 或 Layered Service Provider (LSP) 存在，可能會干擾連接至 SQL Server 的功能。 如需詳細資訊，請參閱 Microsoft 技術支援網站上的[安裝非 IFS LSP 之後 SetFileCompletionNotificationModes 應用程式開發介面會造成 IO 完成連接埠無法正常運作](http://go.microsoft.com/fwlink/p/?LinkId=256032)。|  
|<xref:System.Data.SqlClient.SqlConnection?displayProperty=fullName> 類型|不再支援連接至 SQL Server 1997 資料庫。|在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 下執行的應用程式無法連接至 SQL Server 1997 資料庫。|  
|<xref:System.Data.SqlClient.SqlConnection?displayProperty=fullName> 類型|不再支援使用虛擬介面配接器 (VIA) 通訊協定連接至 SQL Server 資料庫。|在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 下執行的應用程式無法使用 VIA 連接至 SQL Server 資料庫。|  
|<xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName> 類型|將資料插入資料行時，<xref:System.Data.SqlClient.SqlBulkCopy> 會使用目的地資料行的編碼方式，而不是 `VARCHAR` 和 `CHAR` 類型的預設編碼方式。|這項變更可排除當目的地資料行未使用預設編碼方式時，使用預設編碼方式可能造成的資料損毀。 在某些鮮少發生的情況下，如果變更編碼方式後產生的資料太大而不適用於目的地資料行，現有的應用程式可能會擲回 <xref:System.Data.SqlClient.SqlException> 例外狀況。|  
|<xref:System.Data.SqlClient?displayProperty=fullName> 定序|`sql_variant` 資料使用的是 `sql_variant` 定序，而不是資料庫定序。|這項變更可以解決資料庫定序與 `sql_variant` 定序不同時，可能發生的資料毀損。 依賴損毀資料的應用程式可能會失敗。|  
  
### <a name="entity-framework"></a>Entity Framework  
  
|功能|變更|影響|  
|-------------|------------|------------|  
|<xref:System.Data.Objects.ObjectContext.CreateDatabase%2A?displayProperty=fullName> 方法所建立的記錄檔|無論是直接呼叫 <xref:System.Data.Objects.ObjectContext.CreateDatabase%2A> 方法，或在連接字串中使用 Code First 搭配 SqlClient 提供者和 `AttachDBFilename` 值進行呼叫，該方法都會建立名為 *filename*_log.ldf 的記錄檔，而不是 *filename*.ldf (其中 *filename* 是 `AttachDBFilename` 值所指定的檔案名稱)。|這項變更可透過提供依據 SQL Server 規格命名的記錄檔改善偵錯功能。 這項變更應該不會有非預期的副作用。|  
|資料定義語言 (DDL) 應用程式開發介面|指定 `AttachDBFilename` 時，DDL 應用程式開發介面的行為已變更如下：<br /><br /> 連接字串不需要指定 `Initial Catalog` 值。 以往 `AttatchDBFilename` 和 `Initial Catalog` 都是必要項。<br /><br /> 如果同時指定 `AttatchDBFilename` 和 `Initial Catalog`，且指定的 MDF 檔案存在，則 <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A?displayProperty=fullName> 方法會傳回 `true`。 以往它會傳回 `false`。<br /><br /> 如果同時指定 `AttatchDBFilename` 和 `Initial Catalog`，且指定的 MDF 檔案存在，則呼叫 <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A?displayProperty=fullName> 方法會刪除檔案。<br /><br /> 如果是在連接字串指定 <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A?displayProperty=fullName> 值，而其中 MDF 不存在且 `AttachDBFilename` 也不存在時呼叫 `Initial Catalog`，則方法會擲回 <xref:System.InvalidOperationException> 例外狀況。 以往它會擲回 <xref:System.Data.SqlClient.SqlException> 例外狀況。|這些變更可讓您更容易建置使用 DDL 應用程式開發介面的工具和應用程式。 在下列情節中，這些變更可能會影響應用程式相容性：<br /><br /> 如果 `DROP DATABASE` 傳回 <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A?displayProperty=fullName>，使用者撰寫的程式碼會直接執行 <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A?displayProperty=fullName> 命令，而不是呼叫 `true`。 如果未附加資料庫，但 MDF 檔案存在，則會使現有的程式碼中斷。<br /><br /> 當 <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A?displayProperty=fullName> 和 MDF 檔案不存在時，使用者撰寫的程式碼預期 <xref:System.Data.SqlClient.SqlException> 方法擲回 <xref:System.InvalidOperationException> 例外狀況，而不是 `Initial Catalog` 例外狀況。|  
|<xref:System.Data.Objects.ObjectContext.CreateDatabase%2A?displayProperty=fullName> 和 <xref:System.Data.Common.DbProviderServices.CreateDatabase%2A?displayProperty=fullName> 方法|如果在建立空資料庫之後建立資料庫物件失敗，方法會嘗試放棄建立資料庫，並傳播原始 <xref:System.Data.SqlClient.SqlException> 例外狀況。 如果嘗試卸除資料庫失敗，方法會擲回 <xref:System.InvalidOperationException> 例外狀況。|這項變更可防止建立無法使用的空資料庫。 由於成功移除資料庫現在會傳播原始 <xref:System.Data.SqlClient.SqlException> 例外狀況，因此例外狀況處理可能會稍有變更。|  
|<xref:System.Data.Objects.ObjectContext.Translate%2A?displayProperty=fullName> 和 <xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%2A?displayProperty=fullName> 方法|如果 `T` 是列舉類型，則方法會從資料庫正確傳回資料。  以往不支援列舉類型，因此結果會一律轉型為零或是轉換成列舉類型。 Entity Framework 不支援基礎類型 (例如 <xref:System.UInt16>、<xref:System.UInt32> 和 <xref:System.UInt64>) 仍會傳回零，或轉換成基礎值為零的列舉類型。|支援列舉是 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 的 Entity Framework 中的新功能。 不過，如果開發人員程式碼倚賴轉型為零的結果，就可能產生應用程式錯誤 (取決於特定程式碼)。|  
  
### <a name="linq"></a>LINQ  
  
|功能|變更|影響|  
|-------------|------------|------------|  
|<xref:System.Linq.Enumerable.Empty%2A?displayProperty=fullName> 方法|這個方法會傳回已快取的內部執行個體，而不是傳回新的 <xref:System.Collections.Generic.IEnumerable%601> 類型。|這項變更會導致效能提升。 不過，依賴從多次呼叫 <xref:System.Linq.Enumerable.Empty%2A?displayProperty=fullName> 取得兩個唯一空類型的程式碼將會失敗。|  
  
<a name="network"></a>   
## <a name="networking"></a>網路  
  
|功能|變更|影響|  
|-------------|------------|------------|  
|<xref:System.Net.PeerToPeer.Collaboration?displayProperty=fullName> 命名空間的類型和成員|[!INCLUDE[win8](../../../includes/win8-md.md)] 不支援類型和成員。 嘗試呼叫它們會擲回 <xref:System.PlatformNotSupportedException> 例外狀況。|應用程式將無法在 [!INCLUDE[win8](../../../includes/win8-md.md)] 上使用這些類型和成員。|  
|<xref:System.Net.Mail.MailMessage> 物件的序列化與還原序列化。|在 .NET Framework 4.5 中，郵件可以包含非 ASCII 字元。 在 .NET Framework 4 中，僅支援 ASCII 字元。|包含非 ASCII 字元且在 .NET Framework 4.5 下序列化的 <xref:System.Net.Mail.MailMessage> 物件，無法在 .NET Framework 4 下還原序列化。|  
  
<a name="Printing"></a>   
## <a name="printing"></a>列印  
  
|功能|變更|影響|  
|-------------|------------|------------|  
|<xref:System.Printing.PrintSystemJobInfo.JobStream%2A?displayProperty=fullName>|這個屬性會公開列印工作的資料流，可讓使用者寫入此資料流，將原始資料傳送至基礎作業系統列印元件。<br /><br /> 從 Windows 8 和更新版本的 Windows 作業系統上的 .NET Framework 4.5 開始，寫入此資料流的資料必須是做為封裝資料流的 XPS 格式。|若要輸出列印的內容，您可以執行下列任何一項操作：<br /><br /> 使用 <xref:System.Windows.Xps.XpsDocumentWriter> 類別來輸出列印的內容。 這是建議的替代方案。<br /><br /> 請確定傳送至 <xref:System.Printing.PrintSystemJobInfo.JobStream%2A?displayProperty=fullName> 屬性所傳回資料流的資料是做為封裝資料流的 XPS 格式。|  
  
<a name="serialize"></a>   
## <a name="serialization"></a>序列化  
  
|功能|變更|影響|  
|-------------|------------|------------|  
|使用 <xref:System.Xml.Serialization.XmlSerializer> 類別的序列化|在 WCF 4.5，<xref:System.Xml.Serialization.XmlSerializer> 類別已最佳化，以移除其在 C# 編譯器的相依性。 這項變更使冷啟動情節的效能大幅提升。|這項變更可能對在 WCF 4 編譯但針對 WCF 4.5 執行的 XML 序列化程式碼造成問題。 如果您遇到任何 WCF 4.5 中執行現有 XML 序列化程式碼的問題，可使用下列的組態項目，以還原至 WCF 4 的 XmlSerializer 行為：<br /><br /> `<configuration>    <system.xml.serialization>    <xmlSerializer useLegacySerializerGeneration="true"/>    </system.xml.serialization> </configuration>`|  
|使用 <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=fullName> 類別的序列化及還原序列化|使用 <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> 的序列化可以編碼物件的內部狀態，而此狀態在 .NET Framework 版本之間不保證相同。  如果不同，則在某個 .NET Framework 版本中序列化的內容可能無法在其他版本上進行還原序列化。|<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> 類別無法保證提供跨版本的相容性。 請改用 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> 和 <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> 類別。|  
  
<a name="tools"></a>   
## <a name="tools-and-resources"></a>工具和資源  
  
|功能|變更|影響|  
|-------------|------------|------------|  
|MSBuild|您在命令提示字元中執行 MSBuild 時，它會採用停用建置特定專案的方案組態檔。|使用 Visual Studio 呼叫與在命令提示字元中執行時，MSBuild 的行為相同。 您不必另外建立方案或是從方案中移除專案，就能在方案中建置專案的子集。|  
|MSBuild|MSBuild 專案檔中的 `TreatAsLocalProperty` 屬性會防止特定屬性 (包括 `OutDir` 屬性) 在全域層級遭到覆寫。|如果 `OutDir` 是在匯入 MS.Common.Targets 檔案之後覆寫的全域屬性，則覆寫 `OutDir` 屬性可能造成中斷。|  
|Windows 錯誤報告：Watson Bucket。|Managed 損毀會根據一些準則 (其中一項是組件版本) 分組至各種分類。 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中會使用檔案版本，而不是組件版本。|由於組件版本只會在主要版本之間變更，因此使用檔案版本而不使用組件版本做為分類，就可以判斷與 Managed 損毀有關的特定組件版本。|  
|MSBuild|記憶體回收行程不會自動回收 <xref:Microsoft.Build.Evaluation.ProjectCollection?displayProperty=fullName> 集合中的專案資料。|如果您將專案明確載入 <xref:Microsoft.Build.Evaluation.ProjectCollection> 集合中，您應該針對集合的每個成員呼叫 <xref:Microsoft.Build.Evaluation.ProjectCollection.UnloadProject%28Microsoft.Build.Evaluation.Project%29> 方法。|  
  
<a name="asp"></a>   
## <a name="aspnet"></a>ASP.NET  
  
|功能|變更|影響|  
|-------------|------------|------------|  
|ASP.NET IIS 註冊工具 (aspnet_regiis.exe)|在 [!INCLUDE[win8](../../../includes/win8-md.md)] 上，不支援使用 `–i` 和 `–u` 選項來安裝和解除安裝 ASP.NET。|若要安裝或解除安裝 ASP.NET 4.5 (含 IIS 8)，請使用 [開啟或關閉 Windows 功能] 對話方塊、伺服器管理工具或 `dism.exe` 命令列工具。|  
|<xref:System.Web.UI.WebControls.EntityDataSource?displayProperty=fullName> 控制項|<xref:System.Web.UI.Page.LoadComplete?displayProperty=fullName> 事件不再使 <xref:System.Web.UI.WebControls.EntityDataSource?displayProperty=fullName> 控制項叫用資料繫結，讓變更建立/更新/刪除參數。|這項變更可以消除來回存取資料庫的額外作業，防止重設控制項的值，並且產生與其他資料控制項 (例如 <xref:System.Web.UI.WebControls.SqlDataSource> 和 <xref:System.Web.UI.WebControls.ObjectDataSource>) 一致的行為。 在像是應用程式倚賴於 <xref:System.Web.UI.Page.LoadComplete?displayProperty=fullName> 事件中叫用資料繫結這類不常見的情況下，這項變更會產生不同的行為。|  
|<xref:System.Net.WebUtility.HtmlDecode%2A?displayProperty=fullName>、<xref:System.Net.WebUtility.UrlDecode%2A?displayProperty=fullName> 和 [System.Web.Helpers.Json.Decode](https://msdn.microsoft.com/library/system.web.helpers.json.decode.aspx) 方法|根據預設，解碼方法不再將無效的輸入序列解碼為無效的 UTF-16 字串， 而是改為傳回原始輸入。|解碼器輸出的變更只有在您於字串中儲存二進位資料而不是 UTF-16 資料時才相關。 若要明確控制這個行為，請將 [\<appSettings>](http://msdn.microsoft.com/en-us/0d65a3f1-c522-423d-89b6-44921b6daebb) 元素的 `aspnet:AllowRelaxedUnicodeDecoding` 屬性設為 `true` 以啟用舊版行為，或是設為 `false` 以啟用目前的行為。|  
|<xref:System.Net.WebUtility.HtmlEncode%2A?displayProperty=fullName> 方法|若是目標為 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 的應用程式，基本多語文字面 (Basic Multilingual Plane，BMP) 以外的字元傳遞至 <xref:System.Net.WebUtility.HtmlDecode%2A?displayProperty=fullName> 方法時，會正確地來回轉譯。|這項變更對目前的應用程式應該不會造成影響。 若要還原原始行為，請將 [\<httpRuntime>](http://msdn.microsoft.com/library/e1f13641\(v=vs.100\).aspx) 元素的 `targetFramework` 屬性設定為 "4.5" 以外的字串。 您也可以設定 `unicodeEncodingConformance` 組態項目的 `unicodeDecodingConformance` 和 `<webUtility>` 屬性，以與目標 .NET Framework 版本不相關的方式控制這個行為。|  
|<xref:System.Web.HttpRequest.ContentEncoding%2A?displayProperty=fullName> 屬性|禁止使用 UTF-7 編碼。|在某些情況下，倚賴傳入 UTF-7 資料的應用程式資料將無法正確解碼。 這種情況應該很少見，不過您可以使用 [\<appSettings>](http://msdn.microsoft.com/en-us/0d65a3f1-c522-423d-89b6-44921b6daebb) 元素的 `aspnet:AllowUtf7RequestContentEncoding` 屬性還原舊版行為。|  
|<xref:System.Web.HttpUtility.JavaScriptStringEncode%2A?displayProperty=fullName>|從 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 開始，這個方法會逸出 & 字元。|如果您的應用程式倚賴這個方法的舊有行為，可以將 `aspnet:JavaScriptDoNotEncodeAmpersand` 設定加入至組態檔中的 [ASP.NET appSettings 元素](http://msdn.microsoft.com/en-us/bb60e711-0669-4118-a54d-8dd71e009a00) 。|  
|<xref:System.Web.Security.MachineKey.Encode%2A?displayProperty=fullName> 和 <xref:System.Web.Security.MachineKey.Decode%2A?displayProperty=fullName> 方法|這些方法現在已經過時。|編譯呼叫這些方法的程式碼會產生編譯器警告。 建議的替代方式為 <xref:System.Web.Security.MachineKey.Protect%2A?displayProperty=fullName> 和 <xref:System.Web.Security.MachineKey.Unprotect%2A?displayProperty=fullName>。|  
  
<a name="ClickOnce"></a>   
## <a name="clickonce"></a>ClickOnce  
  
|功能|變更|影響|  
|-------------|------------|------------|  
|透過 ClickOnce 發行的應用程式，這些應用程式使用 SHA-256 程式碼簽署憑證。|這個可執行檔使用 SHA256 簽署。 之前，不論程式碼簽署憑證為 SHA-1 或 SHA-256，都會使用 SHA1 簽署。 這適用於：<br /><br /> 使用 Visual Studio 2012 (含) 以後版本建置的所有應用程式。<br /><br /> 使用 Visual Studio 2010 (含) 以前版本，在具有 .NET Framework 4.5 的系統上建置應用程式。<br /><br /> 此外，如果有 .NET Framework 4.5 (含) 以後版本，也會針對 SHA-256 憑證使用 SHA-256 來簽署 ClickOnce 資訊清單，而不論編譯的 .NET Framework 版本為何。|對簽署 ClickOnce 可執行檔所做的變更只會影響 Windows Server 2003 系統；這些變更需要安裝 [KB 938397](http://support.microsoft.com/kb/938397)。<br /><br /> 對使用 SHA-256 簽署資訊清單所做的變更還會引進 .NET Framework 4.5 (含) 以後版本的執行階段相依性，即使應用程式是以 .NET Framework 4 (含) 以前版本為目標亦然。 這個問題已經在 Visual Studio 2013 Update 3 和 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 中解決。 針對 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 的解決方案，請參閱[執行階段變更](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)。|  
  
<a name="mef"></a>   
## <a name="managed-extensibility-framework-mef"></a>Managed Extensibility Framework (MEF)  
  
|功能|變更|影響|  
|-------------|------------|------------|  
|<xref:System.ComponentModel.Composition.Primitives.ComposablePartCatalog?displayProperty=fullName> 和其衍生類別|從 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 開始，MEF 目錄會實作 <xref:System.Collections.IEnumerable>，因此不能再用來建立序列化程式 (<xref:System.Xml.Serialization.XmlSerializer> 物件)。|嘗試序列化 MEF 目錄會擲回例外狀況。|  
  
<a name="web"></a>   
## <a name="web-applications"></a>Web 應用程式  
  
|功能|變更|影響|  
|-------------|------------|------------|  
|.NET Framework 1.1 和 2.0 的 Managed 瀏覽器裝載控制項|Internet Explorer 中已封鎖裝載這些控制項。|Internet Explorer 將無法啟動使用 Managed 瀏覽器裝載控制項的應用程式。 可還原先前行為的方式包括：在 x86 系統和 x64 系統的 32 位元處理序上，將登錄子機碼 HKLM/SOFTWARE/MICROSOFT/.NETFramework 的 EnableIEHosting 值設為 1，在 x64 系統的 64 位元處理序上，將登錄子機碼 HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework 的 EnableIEHosting 值設為 1。|  
  
<a name="wcf"></a>   
## <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)  
 除了下列的應用程式相容性問題之外，也請參閱序列化相關問題的[序列化](#serialize)區段。  
  
|功能|變更|影響|  
|-------------|------------|------------|  
|Internet Information Services (IIS) 或 ASP.NET 程式開發伺服器裝載的 WCF Web 服務中，超過 `maxRequestLength` (在 ASP.NET 中) 或 `maxReceivedMessageSize` (在 WCF 中) 的訊息|HTTP 狀態碼已從 400 (錯誤的要求) 變更為 413 (要求的實體太大)，而且超過 `maxRequestLength` 或 `maxReceivedMessageSize` 設定的訊息會擲回 <xref:System.ServiceModel.ProtocolException> 例外狀況。 傳輸模式為 <xref:System.ServiceModel.TransferMode> 的案例也包括在內。|這項變更有助於在訊息長度超過 ASP.NET 或 WCF 所允許之限制的情況下進行偵錯。<br /><br /> 您必須修改任何依據 HTTP 400 狀態碼執行處理的程式碼。|  
|OData URL 中的`Replace`|OData URL 中的 `Replace` 方法預設為停用。|當 OData `Replace` 停用 (現在為預設) 時，使用者要求將會擲回例外狀況，而且要求將會失敗。|  
|<xref:System.ServiceModel.Web.WebServiceHost?displayProperty=fullName>|如果應用程式程式碼加入明確的端點，<xref:System.ServiceModel.Web.WebServiceHost?displayProperty=fullName> 物件將不再加入預設端點。|如果用戶端應用程式嘗試連接到不再預設加入的端點，則會產生 HTTP 錯誤。|  
  
<a name="winForms"></a>   
## <a name="windows-forms"></a>Windows Form  
  
|功能|變更|影響|  
|-------------|------------|------------|  
|System.Drawing.dll|組件的 `CheckForOverflowUnderflow` 屬性會設定為 `true`。|以往發生溢位時，結果會以無訊息模式截斷。 現在則會擲回 <xref:System.OverflowException> 例外狀況。|  
|<xref:System.Drawing.Imaging.EncoderParameter.%23ctor%28System.Drawing.Imaging.Encoder%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=fullName> 建構函式|這個建構函式已被取代。|建構函式無法在 64 位元系統上運作。 請改用 <xref:System.Drawing.Imaging.EncoderParameter.%23ctor%28System.Drawing.Imaging.Encoder%2CSystem.Int32%2CSystem.Drawing.Imaging.EncoderParameterValueType%2CSystem.IntPtr%29?displayProperty=fullName> 建構函式。|  
  
<a name="wpf"></a>   
## <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)  
 除了下列的應用程式相容性問題之外，也請參閱序列化相關問題的[序列化](#serialize)區段。  
  
|功能|變更|影響|  
|-------------|------------|------------|  
|<xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit%2A?displayProperty=fullName> 屬性|<xref:System.Windows.Controls.TextBox> 和 <xref:System.Windows.Controls.RichTextBox> 類別的預設最大復原作業數限制已從 -1 (沒有限制) 變更為 100。|這項變更應該不會有負面影響。 不過，您可以在具現化控制項之後明確設定 <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit%2A> 屬性。|  
|<xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> 列舉類型|<xref:System.Windows.Controls.PageRangeSelection> 及 <xref:System.Windows.Controls.PageRangeSelection> 成員已加入至列舉。|這項變更對現有的應用程式應該不會造成影響。 對於使用這個列舉的現有成員，預設值為 <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName>。|  
|<xref:System.Windows.DataTemplate> 項目|<xref:System.Windows.DataTemplate> 項目現在會出現在 UI 自動化 (UIA) 樹狀目錄的控制項檢視中。|這項變更可以改善存取範圍。 不過，這會影響依賴先前 UIA 樹狀目錄結構尋找相鄰項目的測試工具。|  
|同步處理 <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=fullName> 屬性與其所繫結的屬性|在某些情況下，如果屬性在資料繫結寫入作業期間經過修改，<xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=fullName> 屬性會反映資料繫結屬性值先前的值。|這應該不會產生負面影響。 不過，您可以藉由將 <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty%2A?displayProperty=fullName> 屬性設為 `false` 還原舊有行為。|  
|<xref:System.Windows.Controls.TextBox?displayProperty=fullName> 屬性|當 <xref:System.Windows.Controls.TextBox?displayProperty=fullName> 控制項為非作用中時，方塊中所選取文字的顯示色彩會與文字方塊使用中時的顯示色彩不同。|您可以藉由將 <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported%2A?displayProperty=fullName> 屬性設為 `false` 還原舊有行為。|  
|<xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A?displayProperty=fullName>|如果衍生自 <xref:System.Windows.Controls.Primitives.MultiSelector> 且 <xref:System.Windows.Controls.Primitives.MultiSelector.CanSelectMultipleItems%2A> 設為 `true` 的控制項在其 <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A?displayProperty=fullName> 集合中有重複項，則重複的項目會出現一次以上。 從資料來源移除這些項目 (例如，藉由呼叫 `Items.Clear`) 無法從 <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A?displayProperty=fullName> 集合中加以移除；只會移除第一個執行個體。<br /><br /> 後續使用 <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A?displayProperty=fullName> 集合 (例如呼叫 `SelectedItems.Clear`)，可能會發生像是 <xref:System.ArgumentException> 的問題，因為 <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A?displayProperty=fullName> 集合包含已不在資料來源中的項目。|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 中已解決這個問題。 如果 <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A?displayProperty=fullName> 集合有重複的項目，而您從資料來源加以移除，並想要繼續使用 <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A?displayProperty=fullName> 集合，請升級至 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]。|  
|<xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy%2A?displayProperty=fullName>|在 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 中，方法會傳回目前執行個體的參考。 在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中，它會傳回新的執行個體。|若程式碼假設同等參考，表示執行中執行緒是在正確內容中，則該程式碼現在將會正確執行。 不過，由於這項變更，您應該測試呼叫 <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy%2A?displayProperty=fullName> 的程式碼。|  
|藉由呼叫 <xref:System.Windows.Interop.HwndSource.AddHook%2A?displayProperty=fullName> 方法使用所加入的處理常式來監視 `WM_POWERBROADCAST` 訊息。|視窗必須將其控制代碼傳遞給 [RegisterPowerSettingNotification](https://msdn.microsoft.com/library/windows/desktop/aa373196.aspx) 函式，明確註冊 `WM_POWERBROADCAST` 通知。 WPF 會透過 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 自動為所有視窗執行此作業。 自 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 起，WPF 只會自動註冊一個特殊的視窗，而不會自動註冊大部分的應用程式視窗，|而且也不會執行處理 `WM_POWERBROADCAST` 通知的程式碼。<br /><br /> 若要繼續接收 `WM_POWERBROADCAST` 通知，請呼叫 [RegisterPowerSettingNotification](https://msdn.microsoft.com/library/windows/desktop/aa373196.aspx) 函式，為 WPF 視窗 (通常是主應用程式視窗) 註冊 `WM_POWERBROADCAST` 通知。 在使用 C# 開發的 WPF 應用程式中，您還必須選取專案屬性 [建置]  索引標籤上的 [容許 Unsafe 程式碼]  方塊，才能執行此作業。<br /><br /> 此外，若您要註冊的視窗不會一直保存到應用程式關閉，應呼叫 [UnregisterPowerSettingNotification](https://msdn.microsoft.com/library/windows/desktop/aa373237.aspx) 函式，並將其傳遞給呼叫 `HPOWERNOTIFY` RegisterPowerSettingNotification [函式所傳回的](https://msdn.microsoft.com/library/windows/desktop/aa373196.aspx) 控制代碼，以取消註冊。|  
  
<a name="wwf"></a>   
## <a name="windows-workflow-foundation-wf"></a>Windows Workflow Foundation (WF)  
  
|功能|變更|影響|  
|-------------|------------|------------|  
|System.Activities.dll 安全性|該組件會以 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 屬性標記。|衍生類別無法以 <xref:System.Security.SecurityCriticalAttribute> 標記。 以往衍生類型必須以 <xref:System.Security.SecurityCriticalAttribute> 標記。 不過，這項變更應該不會產生實際影響。|  
|WF 3.0 類型和成員|WF 3.0 的類型和成員現在已標記為過時。|嘗試編譯使用 WF 3.0 類型或成員的原始程式碼會產生編譯器錯誤。 您應該在 <xref:System.Activities> 命名空間中使用 WF 4 類型和成員。|  
|<xref:System.Activities.Presentation.DragDropHelper?displayProperty=fullName> 類別|<xref:System.Activities.Presentation.DragDropHelper> 類別包括新方法，可支援使用多個物件的拖放作業。 現有的拖放方法僅支援拖曳單一物件，該方法已過時  (如需詳細資訊，請參閱[類別庫中的過時功能](../../../docs/framework/whats-new/whats-obsolete.md))。|雖然舊方法已被取代，但是編譯器和通用語言執行平台仍繼續支援這些方法。 不過，新方法可提供更強大的功能。 以下是部分現有方法的建議替代方法：<br /><br /> 使用 <xref:System.Activities.Presentation.DragDropHelper.DoDragMove%28System.Activities.Presentation.WorkflowViewElement%2CSystem.Windows.Point%29?displayProperty=fullName> 取代 <xref:System.Activities.Presentation.DragDropHelper.DoDragMove%28System.Activities.Presentation.WorkflowViewElement%2CSystem.Windows.Point%29?displayProperty=fullName>。<br /><br /> 使用 <xref:System.Activities.Presentation.DragDropHelper.GetCompositeView%28System.Activities.Presentation.WorkflowViewElement%29> 取代 <xref:System.Activities.Presentation.DragDropHelper.GetCompositeView%28System.Windows.DragEventArgs%29>。<br /><br /> 使用 <xref:System.Activities.Presentation.DragDropHelper.GetDraggedModelItems%28System.Windows.DragEventArgs%29> 取代 <xref:System.Activities.Presentation.DragDropHelper.GetDraggedModelItem%28System.Windows.DragEventArgs%29>。<br /><br /> 使用 <xref:System.Activities.Presentation.DragDropHelper.GetDroppedObjects%28System.Windows.DependencyObject%2CSystem.Windows.DragEventArgs%2CSystem.Activities.Presentation.EditingContext%29> 取代 <xref:System.Activities.Presentation.DragDropHelper.GetDroppedObject%28System.Windows.DependencyObject%2CSystem.Windows.DragEventArgs%2CSystem.Activities.Presentation.EditingContext%29>。|  
|對 <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=fullName> 方法之呼叫的多載解析|[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 加入了包含 <xref:System.Action?displayProperty=fullName> 類型參數的新多載。 重新編譯現有的程式碼時，編譯器可能會將呼叫解析為具有 <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=fullName> 參數的 <xref:System.Delegate> 方法，就像呼叫具有 <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=fullName> 參數的 <xref:System.Action?displayProperty=fullName> 方法。|如果將具有 <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=fullName> 參數的 <xref:System.Delegate> 多載呼叫解析成具有 <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=fullName> 參數的 <xref:System.Action?displayProperty=fullName> 多載呼叫，則可能會出現下列行為上的差異：<br /><br /> 如果發生例外狀況，則不會引發 <xref:System.Windows.Threading.Dispatcher.UnhandledExceptionFilter?displayProperty=fullName> 和 <xref:System.Windows.Threading.Dispatcher.UnhandledException?displayProperty=fullName> 事件。 而是由 <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> 事件處理例外狀況。<br /><br /> 對某些成員 (例如 <xref:System.Windows.Threading.DispatcherOperation.Result%2A?displayProperty=fullName>) 的呼叫會遭到封鎖，直到作業完成為止。|  
|<xref:System.Activities.Expressions.Literal%601?displayProperty=fullName> 類別|相關聯的 <xref:System.Windows.Markup.ValueSerializer> 物件會將 <xref:System.DateTime> 和 <xref:System.DateTimeOffset> 元件為非零，且 (針對 `Second` 值) `Millisecond` 屬性不是 <xref:System.DateTime> 的 <xref:System.DateTime.Kind%2A?displayProperty=fullName> 或 <xref:System.DateTimeKind> 物件轉換為屬性項目語法，而非字串。|這項變更會允許往返 <xref:System.DateTime> 和 <xref:System.DateTimeOffset> 值。 假設輸入 XAML 是使用屬性語法的自訂 XAML 剖析器將無法正常運作。|  
  
<a name="xml"></a>   
## <a name="xml-xslt"></a>XML、XSLT  
  
|功能|變更|影響|  
|-------------|------------|------------|  
|`XDocument.Validate` 方法|如果將 <xref:System.Xml.Linq.LoadOptions?displayProperty=fullName> 值傳遞至 <xref:System.Xml.Linq.XDocument.Load%2A> 方法且發生驗證錯誤，則 <xref:System.Xml.Schema.XmlSchemaException.LineNumber%2A?displayProperty=fullName> 和 <xref:System.Xml.Schema.XmlSchemaException.LinePosition%2A?displayProperty=fullName> 屬性現在會包含行資訊。|倚賴 <xref:System.Xml.Schema.XmlSchemaException.LineNumber%2A?displayProperty=fullName> 及 <xref:System.Xml.Schema.XmlSchemaException.LinePosition%2A?displayProperty=fullName> 屬性值的例外狀況處理程式碼將會無法運作。|  
|使用 <xref:System.Xml.XmlTextReader?displayProperty=fullName> 載入 XML 檔案|DTD 實體展開限制為 10,000,000 個字元。|載入無 DTD 實體展開或 DTD 實體展開受限的 XML 檔案並不會受到影響。 若檔案具有展開至超過 10,000,000 個字元的 DTD 實體，則會載入失敗，而且現在會擲回例外狀況。|  
|<xref:System.Xml.Xsl.XslCompiledTransform?displayProperty=fullName> 類別的往後相容性模式|在 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 中，XSLT 1.0 往後相容性有下列問題：<br /><br /> 如果樣式表的版本設為 2.0，而且剖析器遇到無法辨識的 XSLT 1.0 結構，則載入樣式表會失敗。<br /><br /> 如果樣式表版本設為 1.1，`xsl:sort` 結構就無法排序資料。<br /><br /> 在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中，這些問題已獲得修正，而且 XSLT 1.0 往後相容性模式可正常運作。|XSLT 1.0 往後相容性模式現在可如舊版一般運作。|  
|XSLT 檔太複雜時的例外狀況訊息|在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中，當 XSLT 檔太複雜時，錯誤訊息的文字會是「樣式表太複雜」。 在舊版中，錯誤訊息是「XSLT 編譯錯誤」。|倚賴錯誤訊息文字的應用程式程式碼將無法運作。 不過，例外狀況類型會保持不變，因此這項變更應該不會產生實際影響。|  
|xsd:anyURI 的 XML 結構描述驗證|在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中，XML 結構描述驗證更為嚴格。 如果您使用 xsd:anyURI 驗證 URI (例如 mailto 通訊協定)，而 URI 中有空格，則驗證會失敗。 在舊版 .NET Framework 中，驗證會成功。|這項變更只會影響以 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 為目標的應用程式。|  
  
## <a name="see-also"></a>另請參閱  
 [類別庫中已淘汰的功能](../../../docs/framework/whats-new/whats-obsolete.md)   
 [新功能](../../../docs/framework/whats-new/index.md)   
 [應用程式相容性](../../../docs/framework/migration-guide/application-compatibility.md)   
 [4.5.1 中的應用程式相容性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-1.md)   
 [4.5.2 中的應用程式相容性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-2.md)

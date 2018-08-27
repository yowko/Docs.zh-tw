---
title: .NET Framework 4 移轉問題
ms.date: 05/02/2017
helpviewer_keywords:
- .NET Framework 4, migration
- application compatibility
ms.assetid: df478548-8c05-4de2-8ba7-adcdbe1c2a60
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eeb050e7741422b286c553182cea891278ac9ee7
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "42998743"
---
# <a name="net-framework-4-migration-issues"></a>.NET Framework 4 移轉問題

本主題描述 .NET Framework 版本 3.5 Service Pack 1 與 .NET Framework 版本 4 之間的移轉問題，包含修正程式、標準合規性和安全性變更，以及根據客戶意見反應的變更。 大多數變更都不需要您的應用程式進行任何設計修改。 對於可能涉及修改的變更，請參閱表格的 [建議變更] 欄。

本主題描述下列領域中值得注意的變更：

* [ASP.NET 和 Web](#asp-net-and-web)

* [核心](#core)

* [Data](#data)

* [Windows Communication Foundation (WCF)](#windows-communication-foundation-wcf)

* [Windows Presentation Foundation (WPF)](#windows-presentation-foundation-wpf)

* [XML](#xml)

如需本主題中問題的較高階概觀，請參閱 [.NET Framework 4 移轉手冊](https://msdn.microsoft.com/library/ff657133(v=vs.100).aspx)。

針對 Beta 2 之後的移轉問題，請參閱 [Migration Issues for .NET Framework 4 Applications: Beta 2 to RTM](http://go.microsoft.com/fwlink/?LinkId=191505) (.NET Framework 4 應用程式的移轉問題：Beta 2 到 RTM)。

如需新功能的資訊，請參閱 [.NET Framework 4 的新功能](https://msdn.microsoft.com/library/ms171868(v=vs.100).aspx)。

## <a name="aspnet-and-web"></a>ASP.NET 和 Web

命名空間：<xref:System.Web>、<xref:System.Web.Mobile>、<xref:System.Web.Security>、<xref:System.Web.UI.WebControls>；組件：System.Web (在 System.Web.dll 中)

| 功能 | 3.5 SP1 的差異 | 建議變更 |
| ------- | ------------------------ | ------------------- |
| **瀏覽器定義檔** | 瀏覽器定義檔已更新成包含新增和已更新瀏覽器及裝置的資訊。 已移除 Netscape Navigator 這類較舊的瀏覽器和裝置，並已新增 Google Chrome 和 Apple iPhone 這類較新的瀏覽器和裝置。<br><br>如果您的應用程式包含繼承自其中一個已移除瀏覽器定義的自訂瀏覽器定義，則您會看到錯誤。<br><br><xref:System.Web.HttpBrowserCapabilities> 物件 (由頁面的 `Request.Browse` 屬性所公開) 是透過瀏覽器定義檔所驅動。 因此，ASP.NET 4 中存取此物件的屬性所傳回的資訊，可能會與舊版 ASP.NET 中所傳回的資訊不同。 | 如果您的應用程式依賴舊的瀏覽器定義檔，則可以從下列資料夾中複製它們：<br><br>*Windows\\Microsoft.NET\\Framework\\v2.0.50727\\CONFIG\\Browsers*<br><br>將檔案複製至 ASP.NET 4 的對應 \\CONFIG\\Browsers 資料夾。 在您複製檔案之後，請執行 [Aspnet_regbrowsers.exe](https://msdn.microsoft.com/library/ms229858.aspx) 命令列工具。 如需詳細資訊，請參閱 [http://www.asp.net/mobile](http://go.microsoft.com/fwlink/?LinkId=182900) 網站。 |
| **在混合 ASP.NET 版本下執行的子應用程式** | 因為發生組態或編譯錯誤，所以可能無法啟動設定為執行舊版 ASP.NET 之應用程式子系的 ASP.NET 4 應用程式。 發生的特定錯誤取決於應用程式是在 IIS 6.0 還是 IIS 7 或 IIS 7.5 下執行。 | 您可以變更受影響應用程式的組態檔，讓組態系統正確地辨識 ASP.NET 4 應用程式。 如需您必須進行之變更的資訊，請參閱 ASP.NET 網站之 [ASP.NET 4 Breaking Changes](http://go.microsoft.com/fwlink/?LinkId=182908) (ASP.NET 4 最新變更) 文件中的＜ASP.NET 4 Child Applications Fail to Start When Under ASP.NET 2.0 or ASP.NET 3.5 Applications＞(在 ASP.NET 2.0 或 ASP.NET 3.5 應用程式下時，無法啟動 ASP.NET 4 子應用程式) 一節。 |
| **ClientID 變更** | ASP.NET 4 中的新 `clientIDMode` 設定可讓您指定 ASP.NET 如何產生 HTML 項目的 `id` 屬性。 在舊版 ASP.NET 中，預設行為相當於 `clientIDMode` 的 `AutoID` 設定。 預設設定現在為 `Predictable`。 如需詳細資訊，請參閱 [ASP.NET 網頁伺服器控制項識別](https://msdn.microsoft.com/library/1d04y8ss(v=vs.100).aspx)。 | 如果您使用 Visual Studio 2010 從 ASP.NET 2.0 或 ASP.NET 3.5 升級應用程式，則工具會自動將設定新增至 Web.config 檔案，以保留舊版 .NET Framework 的行為。 不過，如果您將 IIS 中的應用程式集區變更成以.NET Framework 4 為目標來升級應用程式，則 ASP.NET 預設會使用新模式。 若要停用新的用戶端識別碼模式，請在 Web.config 檔案中新增下列設定：<br><br>`<pages clientIDMode="AutoID" />` |
| **程式碼存取安全性 (CAS)** | 已在 ASP.NET 3.5 中新增的 ASP.NET 2.0 NET 功能使用 .NET Framework 1.1 和 .NET Framework 2.0 程式碼存取安全性 (CAS) 模型。 不過，已大幅全面檢查 ASP.NET 4 中 CAS 的實作。 因此，如果部分信任 ASP.NET 應用程式依賴在全域組件快取中執行的受信任程式碼，則可能會因各種安全性例外狀況而失敗。 依賴對電腦 CAS 原則進行大量修改的部分信任應用程式可能也會失敗，並擲回安全性例外狀況。 | 在 `trust` 組態項目中使用新 `legacyCasModel` 屬性，即可將部分信任 ASP.NET 4 應用程式還原為 ASP.NET 1.1 和 2.0 的行為，如下列範例所示：<br><br>`<trust level= "Medium" legacyCasModel="true" />`<br><br>重要事項： 還原為舊版 CAS 模型可能代表安全性降低。<br><br>如需新 ASP.NET 4 程式碼存取安全性模型的詳細資訊，請參閱 [ASP.NET 4 應用程式中的程式碼存取安全性](https://msdn.microsoft.com/library/dd984947.aspx)。 |
| **組態檔** | .NET Framework 和 ASP.NET 4 的根組態檔 (machine.config 檔案和根 Web.config 檔案) 已更新成包含 ASP.NET 3.5 之應用程式 Web.config 檔案中的大部分未定案組態資訊。 因為受管理 IIS 7 和 IIS 7.5 組態系統的複雜度，所以在 ASP.NET 4 以及 IIS 7 和 IIS 7.5 下執行 ASP.NET 3.5 應用程式可能會導致 ASP.NET 錯誤或 IIS 錯誤。 | 使用 Visual Studio 2010 中的專案升級工具，以將 ASP.NET 3.5 應用程式升級至 ASP.NET 4。 Visual Studio 2010 會自動修改 ASP.NET 3.5 應用程式的 Web.config 檔案，以包含 ASP.NET 4 的適當設定。<br><br>不過，您可以使用 .NET Framework 4 來執行 ASP.NET 3.5 應用程式，而不需要重新編譯。 在該情況下，您可能必須先手動修改應用程式的 Web.config 檔案，才能在 .NET Framework 4 和 IIS 7 或 IIS 7.5 下執行應用程式。 您必須進行的特定變更取決於正在使用的軟體組合，包含 Service Pack (SP) 版本。 如需受這項變更影響的可能軟體組合以及如何解決特定組合的問題的資訊，請參閱 ASP.NET 網站之 [ASP.NET 4 Breaking Changes](http://go.microsoft.com/fwlink/?LinkId=182908) (ASP.NET 4 最新變更) 文件中的＜Configuration Errors Related to New ASP.NET 4 Root Configuration＞(與新 ASP.NET 4 根組態相關的組態錯誤) 一節。 |
| **控制項轉譯** | 在舊版 ASP.NET 中，某些控制項已發出您無法停用的標記。 根據預設，ASP.NET 4 中不再產生這種類型的標記。 轉譯變更會影響下列控制項：<br><br>* `Image` 和 `ImageButton` 控制項不再轉譯 `border="0"` 屬性。<br>* `BaseValidator` 類別以及從中衍生的驗證控制項預設不再轉譯紅色文字。<br>* `HtmlForm` 控制項不會轉譯 `name` 屬性。<br>* `Table` 控制項不再轉譯 `border="0"` 屬性。<br><br>如果未針對使用者輸入設計的控制項 (例如，`Label` 控制項) 的 `Enabled` 屬性設定為 `false` (或者，如果它們從容器控制項繼承此設定)，則它們不再轉譯 `disabled="disabled"` 屬性。 | 如果您使用 Visual Studio 2010 從 ASP.NET 2.0 或 ASP.NET 3.5 升級應用程式，則工具會自動將設定新增至 Web.config 檔案，以保留舊版轉譯。 不過，如果您將 IIS 中的應用程式集區變更成以.NET Framework 4 為目標來升級應用程式，則 ASP.NET 預設會使用新轉譯模式。 若要停用新的轉譯模式，請在 Web.config 檔案中新增下列設定：<br><br>`<pages controlRenderingCompatibilityVersion="3.5" />` |
| **預設文件中的事件處理常式** | 已要求具有與其對應之預設文件的無副檔名 URL 時，ASP.NET 4 會將 HTML `form` 項目的 `action` 屬性值轉譯為空字串。 在舊版 ASP.NET 中，`http://contoso.com` 要求會導致 Default.aspx 要求。 在該文件中，會轉譯開啟 `form` 標記，如下列範例所示：<br><br>`<form action="Default.aspx" />`<br><br>在 ASP.NET 4 中，`http://contoso.com` 要求也會導致 Default.aspx 要求，但 ASP.NET 現在會轉譯 HTML 開啟 `form` 標記，如下列範例所示：<br><br>`<form action="" />`<br><br>`action` 屬性是空字串時，IIS `DefaultDocumentModule` 物件會建立 Default.aspx 的子要求。 在大部分的情況下，應用程式碼可以辨識此子要求，Default.aspx 頁面則會正常執行。 不過，Managed 程式碼與 IIS 7 或 IIS 7.5 整合模式之間的可能互動可能會在子要求期間讓受管理 .aspx 頁面適當地停止運作。 如果發生下列狀況，預設 .aspx 文件的子要求將會導致錯誤或未預期的行為：<br><br>* 在 `form` 項目的 `action` 屬性設定為 "" 的情況下，會將 .aspx 頁面傳送至瀏覽器。<br>* 表單會回傳至 ASP.NET。<br>* 受管理 HTTP 模組會讀取實體主體的某個部分，例如 `Request.Form` 或 `Request.Params`。 這會將 POST 要求的實體主體讀入受管理記憶體中。 因此，任何以 IIS 7 或 IIS 7.5 整合模式執行的機器碼模組都無法再使用實體主體。<br>* IIS `DefaultDocumentModule` 物件最後會執行並建立對 Default.aspx 文件的子要求。 不過，因為 Managed 程式碼的某個部分已經讀取實體主體，所以沒有實體主體可用來傳送至子要求。<br>* 針對子要求執行 HTTP 管線時，會在處理常式執行階段期間執行 .aspx 檔案的處理常式。<br><br>因為沒有實體主體，所以沒有表單變數和檢視狀態。 因此，沒有可用的 .aspx 頁面處理常式資訊，可用來判斷應該引發的事件 (如果有的話)。 因此，未執行受影響 .aspx 頁面的回傳事件處理常式。 | 如需這項變更所引發問題之解決方式的資訊，請參閱 ASP.NET 網站之 [ASP.NET 4 Breaking Changes](http://go.microsoft.com/fwlink/?LinkId=182908) (ASP.NET 4 最新變更) 文件中的＜Event Handlers Might Not Be Not Raised in a Default Document in IIS 7 or IIS 7.5 Integrated Mode＞(在預設文件中可能未以 IIS 7 或 IIS 7.5 整合模式引發事件處理常式)。 |
| **雜湊演算法** | ASP.NET 使用加密和雜湊演算法來協助保護資料，例如表單驗證 Cookie 和檢視狀態。 ASP.NET 4 預設會將 <xref:System.Security.Cryptography.HMACSHA256> 演算法用於對 Cookie 和檢視狀態的雜湊作業。 舊版 ASP.NET 使用較舊的 <xref:System.Security.Cryptography.HMACSHA1> 演算法。 | 如果您執行混合使用 ASP.NET 2.0 和 ASP.NET 4 的應用程式，其中，表單驗證 Cookie 這類資料必須跨 .NET Framework 版本作用，請在 Web.config 檔案中新增下列設定，以設定 ASP.NET 4 Web 應用程式使用較舊的 <xref:System.Security.Cryptography.HMACSHA1> 演算法：<br><br>`<machineKey validation="SHA1" />` |
| **在 Internet Explorer 中裝載控制項** | 您無法再於 Internet Explorer 中裝載 Windows Form 控制項，因為在 Web 上裝載控制項有更好的方案。 因此，IEHost.dll 和 IEExec.exe 組件已經從 .NET Framework 中予以移除。 | 您可以使用下列技術，在 Web 應用程式進行自訂控制項開發：<br><br>* 您可以建立 Silverlight 應用程式，並將它設定成在瀏覽器外部執行。 如需詳細資訊，請參閱 [Out-of-Browser Support](https://msdn.microsoft.com/library/dd550721(v=vs.100).aspx) (瀏覽器外用支援)。<br>* 您可以建置 XAML 瀏覽器應用程式 (XBAP) 來利用 WPF 功能 (用戶端電腦上需要 .NET Framework)。 如需詳細資訊，請參閱 [WPF XAML 瀏覽器應用程式概觀](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)。 |
| **HtmlEncode 和 UrlEncode 方法** | <xref:System.Web.HttpUtility> 和 <xref:System.Web.HttpServerUtility> 類別的 `HtmlEncode` 和 `UrlEncode` 方法已更新成編碼單引號字元 (')，如下所示：<br><br>* `HtmlEncode` 方法會將單引號的執行個體編碼為 `&#39;`<br>* `UrlEncode` 方法會將單引號的執行個體編碼為 `%27` | 檢查您的程式碼，找出使用 `HtmlEncode` 和 `UrlEncode` 方法的位置，並確定編碼變更不會導致影響應用程式的變更。 |
| **ASP.NET 2.0 應用程式中的 HttpException 錯誤** | 在 IIS 6 上啟用 ASP.NET 4 之後，IIS 6 上執行的 ASP.NET 2.0 應用程式 (在 Windows Server 2003 或 Windows Server 2003 R2 中) 可能會產生下列這類錯誤：`System.Web.HttpException: Path '/[yourApplicationRoot]/eurl.axd/[Value]' was not found.` | * 如果不需要 ASP.NET 4 即可執行網站，請重新對應網站以改成使用 ASP.NET 2.0。<br><br>-或-<br><br>* 如果需要 ASP.NET 4 才能執行網站，請將任何子 ASP.NET 2.0 虛擬目錄移至對應至 ASP.NET 2.0 的不同網站。<br><br>-或-<br><br>* 停用無副檔名 URL。 如需詳細資訊，請參閱 ASP.NET 網站之 [ASP.NET 4 Breaking Changes](http://go.microsoft.com/fwlink/?LinkId=182908) (ASP.NET 4 最新變更) 文件中的＜ASP.NET 2.0 Applications Might Generate HttpException Errors That Reference eurl.axd＞(ASP.NET 2.0 應用程式可以產生可參考 eurl.axd 的 HttpException 錯誤)。 |
| **成員資格類型** | ASP.NET 成員資格中使用的某些類型 (例如，<xref:System.Web.Security.MembershipProvider>) 已從 System.Web.dll 移至 System.Web.ApplicationServices.dll 組件。 已移動類型，以解析用戶端和擴充 .NET Framework SKU 中類型之間的架構層相依性。 | 在 ASP.NET 4 專案中使用時，可能無法編譯已從舊版 ASP.NET 升級並使用已移動之成員資格類型的類別庫。 如果是這樣，請將類別庫專案中的參考新增至 System.Web.ApplicationServices.dll。 |
| **功能表控制項變更** | <xref:System.Web.UI.WebControls.Menu> 控制項變更會導致下列行為：<br><br>* 如果 <xref:System.Web.UI.WebControls.MenuRenderingMode> 設定為 `List`，或者 <xref:System.Web.UI.WebControls.MenuRenderingMode> 設定為 `Default` 以及 <xref:System.Web.Configuration.PagesSection.ControlRenderingCompatibilityVersion> 設定為 `4.0` 或更新版本，則 <xref:System.Web.UI.WebControls.MenuItem.PopOutImageUrl> 屬性沒有作用。<br>* 如果 <xref:System.Web.UI.WebControls.Menu.StaticPopOutImageUrl%2A> 和 <xref:System.Web.UI.WebControls.Menu.DynamicPopOutImageUrl> 屬性中所設定的路徑包含反斜線 (\\)，則不會轉譯映像 (在舊版 ASP.NET 中，路徑可以包含反斜線)。 | * 設定父代 <xref:System.Web.UI.WebControls.Menu> 控制項的 <xref:System.Web.UI.WebControls.Menu.StaticPopOutImageUrl%2A> 或 <xref:System.Web.UI.WebControls.Menu.DynamicPopOutImageUrl>，而不是設定個別功能表項目的 <xref:System.Web.UI.WebControls.MenuItem.PopOutImageUrl> 屬性。<br><br>-或-<br><br>將 <xref:System.Web.UI.WebControls.MenuRenderingMode> 設定為 `Table`，或將 <xref:System.Web.UI.WebControls.MenuRenderingMode> 設定為 `Default` 並將 <xref:System.Web.Configuration.PagesSection.ControlRenderingCompatibilityVersion> 設定為 `3.5`。 這些設定可讓 <xref:System.Web.UI.WebControls.Menu> 控制項使用舊版 ASP.NET 中所使用的 HTML 表格型配置。<br>* 如果 <xref:System.Web.UI.WebControls.Menu.StaticPopOutImageUrl%2A> 或 <xref:System.Web.UI.WebControls.Menu.DynamicPopOutImageUrl> 屬性中的路徑包含反斜線 (\\)，請替代斜線字元 (/)。 |
| **Web.config 檔案中的行動組件** | 在舊版 ASP.NET 中，System.Web.Mobile.dll 組件參考包含在 `system.web`/`compilation` 之 `assemblies` 區段的根 Web.config 檔案中。 為了改善效能，已移除此組件的參考。<br><br>注意：System.Web.Mobile.dll 組件和 ASP.NET 行動控制項包含在 ASP.NET 4 中，但已遭取代。 | 如果您想要使用此組件中的類型，請在根 Web.config 檔案或應用程式 Web.config 檔案中新增組件參考。 |
| **輸出快取** | 在 ASP.NET 1.0 中，Bug 會讓將 `Location="ServerAndClient"` 指定為輸出快取設定的已快取頁面在回應中發出 `Vary:*` HTTP 標頭。 這會影響如何告知用戶端瀏覽器永遠不要在本機快取頁面。 在 ASP.NET 1.1 中，已新增 <xref:System.Web.HttpCachePolicy.SetOmitVaryStar%2A> 方法，其呼叫目的是要隱藏 `Vary:*` 標頭。 不過，Bug 報告會指出開發人員不知道現有 `SetOmitVaryStar` 行為。<br><br>在 ASP.NET 4 中，不再從指定下列指示詞的回應中發出 `Vary:*` HTTP 標頭：<br><br>`<%@ OutputCache Location="ServerAndClient" %>`<br><br>因此，不再需要 <xref:System.Web.HttpCachePolicy.SetOmitVaryStar%2A> 方法，即可隱藏 `Vary:*` 標頭。 在針對 `Location` 屬性指定 "ServerAndClient" 的應用程式中，將會在瀏覽器中快取頁面，而不需要您呼叫 <xref:System.Web.HttpCachePolicy.SetOmitVaryStar%2A>。 | 如果應用程式中的頁面必須發出 `Vary:*`，則請呼叫 <xref:System.Web.HttpResponse.AppendHeader%2A> 方法，如下列範例所示：<br><br>`System.Web.HttpResponse.AppendHeader("Vary","*");`<br><br>或者，您可以將輸出快取 `Location` 屬性的值變更為 "Server"。 |
| **頁面剖析** | 在 ASP.NET 4 中，ASP.NET 網頁 (.aspx 檔案) 和使用者控制項 (.ascx 檔案) 的頁面剖析器會比舊版 ASP.NET 更為嚴格，而且標示為無效的標記數目會多於舊版本。 | 檢查頁面執行時所產生的錯誤訊息，並修正從無效標記導致的錯誤。 |
| **Passport 類型** | 基於 Passport 中的變更，ASP.NET 2.0 內建的 Passport 支援過時且不再支援 (現在為 Live ID SDK)。 因此，現在會使用 `ObsoleteAttribute` 屬性標示 <xref:System.Web.Security> 中與 Passport 有關的類型。 | 變更在 <xref:System.Web.Security> 命名空間中使用 Passport 類型的任何程式碼 (例如，<xref:System.Web.Security.PassportIdentity>) 使用 [SDK](http://go.microsoft.com/fwlink/?LinkId=106346)。 |
| **FilePath 屬性中的 PathInfo 資訊** | ASP.NET 4 不再將 `PathInfo` 值包含在 <xref:System.Web.HttpRequest.FilePath>、<xref:System.Web.HttpRequest.AppRelativeCurrentExecutionFilePath> 和 <xref:System.Web.HttpRequest.CurrentExecutionFilePath> 這類屬性的傳回值中。 相反地，<xref:System.Web.HttpRequest.PathInfo> 中提供 `PathInfo` 資訊。 例如，假設有下列 URL 片段：<br><br>`/testapp/Action.mvc/SomeAction`<br><br>在舊版 ASP.NET 中，<xref:System.Web.HttpRequest> 屬性具有下列值：<br><br>* <xref:System.Web.HttpRequest.FilePath>: `/testapp/Action.mvc/SomeAction`<br>* <xref:System.Web.HttpRequest.PathInfo>：(空白)<br><br>在 ASP.NET 4 中，<xref:System.Web.HttpRequest> 屬性改為具有下列值：<br><br>* <xref:System.Web.HttpRequest.FilePath>: `/testapp/Action.mvc`<br>* <xref:System.Web.HttpRequest.PathInfo>: `SomeAction` | 檢查您的程式碼，找出依賴 <xref:System.Web.HttpRequest> 類別之屬性來傳回路徑資訊的位置；請變更程式碼以反映路徑資訊傳回方式的變更。 |
| **要求驗證** | 為了改善要求驗證，會在要求生命週期稍早叫用 ASP.NET 要求驗證。 因此，會針對不適用於 .aspx 檔案的要求執行要求驗證，例如 Web 服務和自訂處理常式。 自訂 HTTP 模組在要求處理管線中執行時，要求驗證也會使用中。<br><br>基於這項變更，.aspx 檔案以外之資源的要求可能會擲回要求驗證錯誤。 要求管線中所執行的自訂程式碼 (例如，自訂 HTTP 模組) 也可能會擲回要求驗證錯誤。 | 如果必要，您可以使用 Web 組態檔中的下列設定，還原為只有觸發要求驗證之 .aspx 頁面的舊行為：<br><br>`<httpRuntime requestValidationMode="2.0" />`<br><br>警告：如果您還原為舊版行為，請確定現有處理常式、模組和其他自訂程式碼中的所有程式碼都會檢查可能為 XSS 攻擊向量的可能不安全 HTTP 輸入。 |
| **路由傳送** | 如果您在 Visual Studio 2010 中建立檔案系統網站，而且網站位於資料夾名稱中包含點 (.) 的資料夾，則無法可靠地進行 URL 路由傳送。 從某些虛擬路徑傳回 HTTP 404 錯誤。 發生原因是 Visual Studio 2010 使用根虛擬目錄的不正確路徑來啟動 Visual Studio 程式開發伺服器 (Cassini)。 | * 在檔案式網站的 [屬性] 頁面中，將 [虛擬路徑] 屬性變更為 "/"。<br><br>-或-<br><br>* 建立 Web 應用程式專案，而不是網站專案。 Web 應用程式專案沒有這個問題，而且 URL 路由傳送會運作，即使專案資料夾的名稱中有一個點也是一樣。<br><br>-或-<br><br>* 建立裝載於 IIS 中的 HTTP 網站。 在虛擬路徑和專案檔資料夾中，裝載 IIS 的網站可以有點。 |
| **SharePoint 網站** | 如果您嘗試執行的 ASP.NET 4 網站部署為 SharePoint 網站的子系，而其包含名為 `WSS_Minimal` 的自訂部分信任層級，則會看到下列錯誤：<br><br>`Could not find permission set named 'ASP.Net'.` | 目前，沒有 SharePoint 版本與 ASP.NET 相容。 因此，您不應該嘗試將 ASP.NET 4 網站執行為 SharePoint 網站子系。 |
| **XHTML 1.1 標準** | 若要啟用新網站的 XHTML 1.1 合規性，.NET Framework 4 中的 ASP.NET 控制項會產生符合 XHTML 1.1 標準的 HTML。 在 `<system.Web>` 項目的 Web.config 檔案中使用下列選項，以啟用這項轉譯：<br><br>`<pages controlRenderingCompatibilityVersion="4.0"/>`<br><br>此選項預設為 4.0。 基於相容性，從 Visual Studio 2008 升級至 Visual Studio 的 Web 專案會啟用 3.5 設定。 | 無。 |

## <a name="core"></a>核心

### <a name="general-features"></a>一般功能

| 功能 | 3.5 SP1 的差異 | 建議變更 |
| ------- | ------------------------ | ------------------- |
| **CardSpace** | Windows CardSpace 不再包含於 .NET Framework 中；它會個別予以提供。 | 請從 [Microsoft 下載中心](http://go.microsoft.com/fwlink/?LinkId=199868)下載 Windows CardSpace。 |
| **組態檔** | 已更正 .NET Framework 如何存取應用程式組態檔。 | 如果您的應用程式組態檔命名為 *application-name.config*，請將它重新命名為 *application-name.exe.config*。例如，將 *MyApp.config* 重新命名為 *MyApp.exe.config*。 |
| **C# 程式碼編譯器** | 已在 <xref:Microsoft.CSharp> 命名空間中的 `Compiler`、`CompilerError` 和 `ErrorLevel` 類別不再可用，而其組件 (cscompmgd.dll) 不再包含於 .NET Framework 中。 | 在 <xref:System.CodeDom.Compiler> 命名空間中使用 <xref:System.CodeDom.Compiler.CodeDomProvider> 類別和其他類別。 如需詳細資訊，請參閱[使用 CodeDOM](https://msdn.microsoft.com/library/y2k85ax6(v=vs.100).aspx)。 |
| **裝載** (Unmanaged API) | 為了改善裝載功能，有些裝載啟用 API 已遭取代。 同處理序並存執行功能可讓應用程式在相同的處理序中載入和啟動多個版本的 .NET Framework。 例如，您可以執行的應用程式會在相同的處理序中載入根據 .NET Framework 2.0 SP1 的增益集 (或元件) 以及根據 .NET Framework 4 的增益集。 舊元件會繼續使用舊版 .NET Framework，新元件則會使用新版 .NET Framework。 | 使用[同處理序並存執行](/dotnet/framework/deployment/in-process-side-by-side-execution)中所述的組態。 |
| **新的安全性模型** | 程式碼存取安全性 (CAS) 原則已關閉並取代為簡化模型，如 [.NET Framework 4 中的安全性變更](https://msdn.microsoft.com/library/dd233103(v=vs.100).aspx)中所述。 | 如果您取決於應用程式中的 CAS，則可能需要修改。 如需詳細資訊，請參閱[程式碼存取安全性原則相容性和移轉](/dotnet/framework/misc/code-access-security-policy-compatibility-and-migration)。 |

### <a name="date-and-time"></a>日期和時間

命名空間：<xref:System>；組件：mscorlib (在 mscorlib.dll 中)

| 功能 | 3.5 SP1 的差異 | 建議變更 |
| ------- | ------------------------ | ------------------- |
| **日光節約時間** | 為了與系統時鐘一致，時間屬性 (例如 <xref:System.TimeZoneInfo.Local> 和 <xref:System.DateTime.Now>) 現在會使用作業系統規則，而不是日光節約時間作業的其他 .NET Framework 資料。 | 無。 |
| **格式字串** | 為了支援區分文化特性格式，除了新 `ParseExact` 和 `TryParseExact` 方法之外，<xref:System.TimeSpan> 結構還包含 `ToString`、`Parse` 和 `TryParse` 方法的新多載。 | 無。 |


### <a name="globalization"></a>全球化

如需新中性和特定文化特性的清單，請參閱[全球化和當地語系化的新功能](https://msdn.microsoft.com/library/dd997383(v=vs.100).aspx)。

命名空間：<xref:System.Globalization>；組件：mscorlib (在 mscorlib.dll 中)

| 功能 | 3.5 SP1 的差異 | 建議變更 |
| ------- | ------------------------ | ------------------- |
| **文化特性名稱** | 下列名稱變更會影響德文、迪維西文和非洲文文化特性：<br><br>* <xref:System.Globalization.CultureAndRegionInfoBuilder.CurrencyEnglishName>：德文 (瑞士) (de-CH) 文化特性的貨幣名稱已從 "sFr." 變更 為 "Fr."。<br>* <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern>：迪維西文 (馬爾地夫) (dv-MV) 文化特性的完整日期模式已從 "dd/MMMM/yyyy" 變更為 "dd/MM/yyyy"。<br>* <xref:System.Globalization.DateTimeFormatInfo.PMDesignator>： 南非荷蘭文 (南非) (af-ZA) 文化特性的 P.M. 指示項已從 "nm" 變更為 "PM"。 | 請注意文化特性名稱的變更。 |
| **LCID 參數** | 為了與自動化伺服器設定中的預期行為一致，CLR 不再將 `LCID` 參數的目前文化特性 (Culture) 傳遞給未受管理的 COM 應用程式。 相反地，它會傳遞文化特性的 1033 (en-us)。 | 不需要進行任何修改，但需要所指定文化特性的原生應用程式除外。 |
| **過時的文化特性類型** | <xref:System.Globalization.CultureTypes> 和 <xref:System.Globalization.CultureTypes> 文化特性類型現在已過時。<br><br>基於回溯相容性，<xref:System.Globalization.CultureTypes> 現在會傳回舊版 .NET Framework 所含的中性和特定文化特性，<xref:System.Globalization.CultureTypes> 現在則會傳回空清單。 | 使用 <xref:System.Globalization.CultureTypes> 列舉的其他值。 |
| **擷取文化特性** | 從 Windows 7 開始，.NET Framework 4 會從作業系統擷取文化特性資訊，而不是儲存資料本身。 此外，.NET Framework 會與 Windows 同步，以排序資料以及設定資料大小寫。 | 無。 |
| **Unicode 5.1 標準** | .NET Framework 現在支援所有 Unicode 5.1 字元，大約新增 1400 個字元。 其他字元包含新的符號、箭號、變音符號、標點符號、數學符號、CJK 筆劃和表意字元、其他馬來亞拉姆文和特拉古文數字字元，以及各種緬甸、拉丁、阿拉伯文、希臘文、蒙古文和斯拉夫字元。 Unicode 5.1 支援下列新的指令碼：巽丹文、雷布查文、桑塔爾文、瓦伊文、紹拉斯徹文、開亞里文、拉讓文、果魯穆奇文、歐迪亞文、坦米爾文、特拉古文、馬來亞拉姆文字元和查姆文。 | 無。 |

### <a name="exceptions"></a>例外狀況

命名空間：<xref:System>、<xref:System.Runtime.ExceptionServices>；組件：mscorlib (在 mscorlib.dll 中)

| 功能 | 3.5 SP1 的差異 | 建議變更 |
| ------- | ------------------------ | ------------------- |
| **損毀處理序狀態的例外狀況** | CLR 不再將損毀處理序狀態的例外狀況傳遞給 Managed 程式碼中的例外狀況處理常式。 | 這些例外狀況指出處理序狀態已損毀。 不建議您在此狀態下執行應用程式。<br><br>如需詳細資訊，請參閱 <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> 以及 CLR Inside Out 部落格中的項目[Handling Corrupted State Exceptions](http://go.microsoft.com/fwlink/?LinkID=179681) (處理損毀的狀態例外狀況)。 |
| **執行引擎例外狀況** | 因為可攔截的例外狀況允許不穩定的處理序繼續執行，所以 <xref:System.ExecutionEngineException> 現在已過時。 這項變更可改善執行階段中的預測性和可靠性。 | 使用 <xref:System.InvalidOperationException> 對條件發出信號。 |

### <a name="reflection"></a>反射

命名空間：<xref:System.Reflection>；組件：mscorlib (在 mscorlib.dll 中)

| 功能 | 3.5 SP1 的差異 | 建議變更 |
| ------- | ------------------------ | ------------------- |
| **組件雜湊演算法** | 因為執行階段在未載入所參考組件時不知道組件的雜湊演算法，所以 <xref:System.Reflection.AssemblyName.HashAlgorithm> 屬性現在會傳回 <xref:System.Configuration.Assemblies.AssemblyHashAlgorithm> (這指的是使用 <xref:System.Reflection.Assembly.GetReferencedAssemblies%2A> 方法所傳回的所參考組件的屬性)。 | 無。 |
| **組件載入** | 為了避免重複載入組件，以及儲存虛擬位址空間，CLR 現在只會使用 Win32 `MapViewOfFile` 函式載入組件。 它也不再呼叫 `LoadLibrary` 函式。<br><br>這項變更會以下列方式影響診斷應用程式：<br><br>* <xref:System.Diagnostics.ProcessModuleCollection> 將不再包含從 `Process.GetCurrentProcess().Modules` 呼叫取得之類別庫 (.dll 檔案) 中的任何模組。<br>* 使用 `EnumProcessModules` 函式的 Win32 應用程式看不到所有列出的受管理模組。 | 無。 |
| **宣告類型** | 類型沒有宣告類型時，<xref:System.Type.DeclaringType> 屬性現在會正確地傳回 Null。 | 無。 |
| **委派** | 將 Null 值傳遞給委派的建構函式時，委派現在會擲回 <xref:System.ArgumentNullException>，而不是 <xref:System.NullReferenceException>。 | 請確定任何例外狀況處理攔截到 <xref:System.ArgumentNullException>。 |
| **全域組件快取位置變更** | 針對 .NET Framework 4 組件，已將全域組件快取從 Windows 目錄 (%WINDIR%) 移至 Microsoft.Net 子目錄 (*%WINDIR%\\Microsoft.Net*)。 舊版本中的組件會保留在較舊的目錄中。<br><br>未受管理的 [ASM_CACHE_FLAGS](../unmanaged-api/fusion/asm-cache-flags-enumeration.md) 列舉包含新的 `ASM_CACHE_ROOT_EX` 旗標。 此旗標會取得 .NET Framework 4 組件的快取位置，而快取位置可以透過 [GetCachePath](../unmanaged-api/fusion/getcachepath-function.md) 函式取得。 | 無，假設應用程式未使用組件的明確路徑，這不是建議的作法。 |
| **全域組件快取工具** | [Gacutil.exe (全域組件快取工具)](https://msdn.microsoft.com/library/ex0ss12c(v=vs.100).aspx) 不再支援殼層外掛程式檢視器。 | 無。 |

### <a name="interoperability"></a>互通性

命名空間：<xref:System.Runtime.InteropServices>；組件：mscorlib (在 mscorlib.dll 中)

| 功能 | 3.5 SP1 的差異 | 建議變更 |
| ------- | ------------------------ | ------------------- |
| **緩衝區長度** (Unmanaged API) | 為了節省記憶體，[ICorProfilerInfo2::GetStringLayout](../unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) 方法之 `pBufferLengthOffset` 參數的功能已變更成符合 `pStringLengthOffset` 參數。 這兩個參數現在會指向字串長度的位移位置。 已從字串類別呈現移除緩衝區長度。 | 移除緩衝區長度的任何相依性。 |
| **JIT 偵錯** | 若要簡化 Just-In-Time (JIT) 偵錯的註冊，.NET Framework 偵錯工具現在只會使用 AeDebug 登錄機碼，以控制機器碼的 JIT 偵錯行為。 這項變更會導致下列各項：<br><br>* 您無法再針對 Managed 和機器碼註冊兩個不同的偵錯工具。<br>* 您可以不再針對非互動式處理序自動啟動偵錯工具，但可以提示使用者進行互動式處理序。<br>* 在無法啟動偵錯工具時，或沒有應該啟動的註冊偵錯工具時，不再通知您。<br>* 不再支援取決於應用程式互動性的自動啟動原則。 | 依需要調整偵錯作業。 |
| **平台叫用** | 為了改善與 Unmanaged 程式碼之互通性的效能，平台叫用中的不正確呼叫慣例現在會讓應用程式失敗。 在舊版本中，封送處理層會解析堆疊中的這些錯誤。 | 對 Microsoft Visual Studio 2010 中的應用程式進行偵錯將會警告您發生這些錯誤，因此您可以更正它們。<br><br>如果您有無法更新的二進位檔，則可以將 [\<NetFx40_PInvokeStackResilience>](../configure-apps/file-schema/runtime/netfx40-pinvokestackresilience-element.md) 項目包含在您應用程式的組態檔中，以解決舊版堆疊中的呼叫錯誤。 不過，這可能會影響應用程式的效能。 |
| **已移除介面** (Unmanaged API) | 為了避免開發人員混淆，已移除下列介面，因為它們未提供任何有用的執行階段案例，而且 CLR 未提供或接受任何實作：<br><br>* **INativeImageINativeImageDependency**<br>* **INativeImageInstallInfo**<br>* **INativeImageEvaluate**<br>* **INativeImageConverter**<br>* **ICorModule**<br>* **IMetaDataConverter** | 無。 |

## <a name="data"></a>資料

本節描述使用資料集和 SQL 用戶端、Entity Framework、LINQ to SQL 和 WCF Data Servers (先前稱為 ADO.NET Data Services) 的移轉問題。

### <a name="dataset-and-sql-client"></a>DataSet 和 SQL 用戶端

下表描述先前有限制或其他問題之功能的改善。

命名空間：<xref:System.Data>、<xref:System.Data.Objects.DataClasses>、<xref:System.Data.SqlClient>；組件：System.Data (在 System.Data.dll 中)、System.Data.Entity (在 System.Data.Entity.dll 中)

| 功能 | 3.5 SP1 的差異 |
| ------- | ------------------------ |
| **POCO 案例** | <xref:System.Data.Objects.DataClasses.IRelatedEnd> 介面有新的方法可改善其在簡單的 CLR 物件 (POCO) 案例中的使用性。 這些新方法接受 <xref:System.Object> 作為參數，而不接受 <xref:System.Data.Objects.DataClasses.IEntityWithRelationships> 實體。 |
| **編輯資料列** | <xref:System.Data.DataView> 類別所實作的 <xref:System.Collections.IList.IndexOf%2A> 方法現在會正確地傳回所編輯資料列的值，而不是傳回 -1。 |
| **事件** | 現在，資料列處於已修改狀態並呼叫 <xref:System.Data.DataRow.RejectChanges%2A> 方法時，會引發 <xref:System.Data.DataRowView.PropertyChanged> 事件。 這項變更可讓您更輕鬆地建立可公開 <xref:System.Data.DataSet> 物件內容的 UI 控制項。 |
| **例外狀況** | 未設定或開啟連線時，<xref:System.Data.SqlClient.SqlCommand.Prepare%2A> 方法現在會擲回 <xref:System.InvalidOperationException>，而不是 <xref:System.NullReferenceException>。 |
| **對應檢視** | 現在會在設計階段攔截查詢檢視對應錯誤，而不是在執行階段擲回 <xref:System.NullReferenceException>。<br><br>對應驗證現在會攔截概念結構描述 (CSDL) 中的兩個關聯集對應至相同資料行的錯誤。 |
| **異動** | 如果應用程式在交易完成 (包含已中止或已回復) 之後嘗試對連線執行陳述式，現在就會擲回 <xref:System.InvalidOperationException>。 舊版本未擲回例外狀況，並可讓您執行其他命令，即使交易已中止也是一樣。 |

### <a name="entity-framework"></a>Entity Framework

下表描述先前有限制或其他問題之功能的改善。

命名空間：<xref:System.Data>、<xref:System.Data.Objects>、<xref:System.Data.Objects.DataClasses>；組件：System.Data.Entity (在 System.Data.Entity.dll 中)

| 功能 | 3.5 SP1 的差異 |
| ------- | ------------------------ |
| **實體物件** | 呼叫 <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> 方法時，現在在 <xref:System.Data.Objects.ObjectContext.Detach%2A> 方法與實體物件狀態之間具有同位檢查。 這項改善的一致性可避免擲回未預期的例外狀況。 |
| **Entity SQL** | 已針對 Entity SQL 中的識別項解析改善規則。<br><br>Entity SQL 剖析器具有用於解析多組件識別項的改善邏輯。 |
| **結構化註解** | Entity Framework 現在可辨識結構化註解。 |
| **查詢** | 查詢中已進行下列改善：<br><br>* 不論查詢中是否有任何其他選取，在空集合上使用 Null 索引鍵的 `GroupBy` 查詢都不會傳回任何資料列。<br>* LINQ 和 Entity-SQL 查詢中的已產生 SQL 現在預設會將字串參數視為非 Unicode 值。 |

### <a name="linq-to-sql"></a>LINQ to SQL

下表描述先前有限制或其他問題之功能的改善。

命名空間：<xref:System.Data.Linq>；組件：System.Data.Linq (在 System.Data.Linq.dll 中)

| 功能 | 3.5 SP1 的差異 |
| ------- | ------------------------ |
| **事件** | 除了在載入集合時引發事件之外，如果卸載 <xref:System.Data.Linq.EntitySet%601>，<xref:System.Data.Linq.EntitySet%601> 集合現在還會對新增和移除作業引發 <xref:System.Data.Linq.EntitySet%601.ListChanged> 事件。 |
| **查詢** | LINQ to SQL 查詢中不再忽略 `Skip(0)`。 因此，具有此方法之查詢的行為可能會不同。 例如，在某些情況下，`OrderBy` 子句需要具有 `Skip(0)`，而且，如果未包含 `OrderBy` 子句，則查詢現在會擲回 <xref:System.NotSupportedException> 例外狀況。 |

### <a name="wcf-data-services"></a>WCF 資料服務

下表描述先前有限制或其他問題之功能的改善。

命名空間：<xref:System.Data.Services>、<xref:System.Data.Services.Client>、<xref:System.Data.Services.Common>、<xref:System.Data.Services.Providers>；組件：System.Data.Services (在 System.Data.Services.dll 中)、System.Data.Services.Client (在 System.Data.Services.Client.dll 中)

| 功能 | 3.5 SP1 的差異 |
| ------- | ------------------------ |
| **批次二進位內容** | WCF Data Services 現在支援要求和回應中的批次二進位內容。 |
| **變更攔截器** | 變更攔截器現在是針對刪除要求所執行。<br><br>變更攔截器是一種方法，會在每次伺服器收到修改實體集中實體的要求時執行。 它會在執行內送要求之前執行。 變更攔截器可存取所變更的實體以及對其執行的作業。 |
| **例外狀況** | 下列情況現在會擲回更有用的例外狀況，而不是 <xref:System.NullReferenceException>：<br><br>* 資料服務呼叫逾時時的 <xref:System.ServiceProcess.TimeoutException>。<br>* 對資料服務進行不正確要求時的 <xref:System.Data.Services.Client.DataServiceRequestException>。<br><br>在應用程式中，您應該變更用來攔截新例外狀況的例外狀況處理。 |
| **標頭** | 已對標頭進行下列改善：<br><br>* WCF Data Services 現在會正確地拒絕具有未指定值的 `eTag` 標頭。<br>* WCF Data Services 現在會傳回錯誤，而且 `if-*` 標頭位在要求時，不會執行連結之刪除要求的要求。<br>* WCF Data Services 現在會以用戶端在 Accept 標頭中指定的格式 (Atom, JSON) 將錯誤傳回給用戶端。 |
| **JSON 讀取器** | 現在，JavaScript 物件標記法 (JSON) 讀取器在處理傳送至 WCF 資料服務的 JSON 承載時，會於讀取單一反斜線 ("\\") 逸出字元時正確地傳回錯誤。 |
| **合併** | 已對 <xref:System.Data.Services.Client.MergeOption> 列舉進行下列改善：<br><br>* 在資料服務的任何後續回應之後，<xref:System.Data.Services.Client.MergeOption> 合併選項不再修改用戶端上的實體。<br>* 在動態 SQL 與預存程序更新之間，<xref:System.Data.Services.Client.MergeOption> 選項現在會一致。 |
| **要求** | 現在，在處理資料服務的要求之前，會呼叫 <xref:System.Data.Services.DataService%601.OnStartProcessingRequest%2A> 方法。 這可讓 <xref:System.Data.Services.Providers.ServiceOperation> 服務的要求正常運作。 |
| **資料流** | WCF Data Services 不再關閉進行讀取和寫入作業的基礎資料流。 |
| **URI** | 已修正 WCF Data Services 用戶端的 URI 逸出。 |

## <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)

下表描述先前有限制或其他問題之功能的改善。

| 功能 | 3.5 SP1 的差異 |
| ------- | ------------------------ |
| **組態檔** | 為了透過組態檔階層啟用行為繼承，WCF 現在支援跨組態檔合併。<br><br>現在已擴充組態繼承模型，讓使用者定義將套用至在電腦上執行之所有服務的行為。<br><br>如果在不同的階層層級有同名的行為，您可能會遇到行為變更。 |
| **服務裝載** | 將 `allowDefinition="MachineToApplication"` 屬性新增至項目定義，就無法再於服務層級指定 `<serviceHostingEnvironment>` 組態項目。<br><br>在服務層級指定 `<serviceHostingEnvironment>` 項目就技術上而言不正確，而且會導致不一致的行為。 |

## <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

### <a name="applications"></a>應用程式

命名空間：<xref:System.Windows>、<xref:System.Windows.Controls>；組件：PresentationFramework (在 PresentationFramework.dll 中)

| 功能 | 3.5 SP1 的差異 | 建議變更 |
| ------- | ------------------------ | ------------------- |
| **例外狀況處理** | 若要早期偵測到錯誤，WPF 會擲回 <xref:System.Reflection.TargetInvocationException> 並將 <xref:System.Exception.InnerException> 屬性設定為重大例外狀況，例如 <xref:System.NullReferenceException>、<xref:System.OutOfMemoryException>、<xref:System.StackOverflowException> 和 <xref:System.Security.SecurityException>，而不是攔截原始例外狀況。 | 無。 |
| **連結的資源** | 為了讓連結更為簡單，建置應用程式時，位於專案資料夾結構以外之位置中的資源檔 (例如影像) 會使用資源檔的完整路徑，而不是將其檔案名稱作為資源識別碼。 應用程式將能夠在執行階段找出檔案。 | 無。 |
| **部分信任應用程式** | 基於安全性考量，如果 Windows 應用程式是以部分信任執行並包含內含 HTML 的 <xref:System.Windows.Controls.WebBrowser> 控制項或 <xref:System.Windows.Controls.Frame> 控制項，則會在建立控制項時擲回 <xref:System.Security.SecurityException>。<br><br>如果符合下列所有條件，則瀏覽器應用程式會擲回例外狀況，並顯示一則訊息：<br><br>* 應用程式正在 Firefox 中執行。<br>* 應用程式是以部分信任在非受信任網站的網際網路區域中執行。<br>* 應用程式包含內含 HTML 的 <xref:System.Windows.Controls.WebBrowser> 控制項或 <xref:System.Windows.Controls.Frame> 控制項。<br><br>請注意，從信任的網站或內部網路區域執行的應用程式不會受到影響。 | 在您的瀏覽器應用程式中，您可以執行下列其中一項來簡化這項變更：<br><br>* 以完全信任執行瀏覽器應用程式。<br>* 讓客戶將應用程式的網站新增至信任的網站區域。<br>* 讓客戶在 Internet Explorer 中執行應用程式。 |
| **資源字典** | 為了改善佈景主題層級資源字典，並防止變更它們，資源字典中所定義和合併至佈景主題層級字典的可凍結資源現在一律會標示為凍結且為不變的。 這是可凍結資源的預期行為。 | 修改佈景主題層級合併字典中所定義資源的應用程式應該會複製資源，並修改複製的複本。 或者，資源可以標上 `x:Shared="false"`，因此 <xref:System.Windows.ResourceDictionary> 會在每次查詢資源時建立新的複本。 |
| **Windows 7** | 為了讓 WPF 應用程式在 Windows 7 上運作地更好，已進行下列改善，來更正視窗的行為：<br><br>* 根據使用者互動，停駐和手勢狀態現在會如預期運作。<br>* **重疊顯示視窗、堆疊顯示視窗**和**並排顯示視窗**工作列命令現在有正確的行為，並更新適當的屬性。<br>* 最大化或最小化視窗的 `Top`、`Left`, `Width` 和 `Height` 屬性現在包含視窗的正確還原位置，而不是其他值，視監視器而定。 | 無。 |
| **Windows 樣式和透明度** | <xref:System.Windows.Window.AllowsTransparency> 為 `true` 且 <xref:System.Windows.WindowState> 為 <xref:System.Windows.WindowState> 時，如果您嘗試將 <xref:System.Windows.Window.WindowStyle> 設定為 <xref:System.Windows.WindowStyle> 以外的值，則會擲回 <xref:System.InvalidOperationException>。 | 如果您必須在 <xref:System.Windows.Window.AllowsTransparency> 為 `true` 時變更 <xref:System.Windows.Window.WindowStyle>，則可以呼叫 Win32 `SetWindowLongPtr` 函式。 |
| **XPS 檢視器** | WPF 不包含 Microsoft XML Paper Specification Essentials Pack (XPSEP)。 XPSEP 包含於 Windows 7 和 Windows Vista 中。<br><br>在執行未安裝 .NET Framework 3.5 SP1 之 Windows XP 的電腦上，使用 <xref:System.Windows.Controls.PrintDialog> 中以外的 WPF API 進行列印將會依賴 WINSPOOL。 將不會報告某些印表機功能，而且在列印期間不會套用某些印表機設定。 | 如果必要，請安裝 [Microsoft XML Paper Specification Essentials Pack](http://go.microsoft.com/fwlink/?LinkId=178895)。 |

### <a name="controls"></a>控制項

命名空間：<xref:System.Windows>、<xref:System.Windows.Controls>、<xref:System.Windows.Data>、<xref:System.Windows.Input>；組件：PresentationFramework (在 PresentationFramework.dll 中)、PresentationCore (在 PresentationCore.dll 中)、WindowsBase (在 WindowsBase.dll 中)

| 功能 | 3.5 SP1 的差異 | 建議變更 |
| ------- | ------------------------ | ------------------- |
| **對話方塊** | 為了改善可靠性，會在已建立 <xref:Microsoft.Win32.FileDialog> 控制項的相同執行緒上呼叫 <xref:Microsoft.Win32.CommonDialog.ShowDialog%2A> 方法。 | 請務必建立 <xref:Microsoft.Win32.FileDialog> 控制項，並在相同的執行緒上呼叫 <xref:Microsoft.Win32.CommonDialog.ShowDialog%2A> 方法。 |
| **浮動視窗** | 為了修正不正確地持續重新啟用浮動視窗的焦點還原邏輯 (讓它看起來像是強制回應對話方塊)，現在，如果候選項目不是視窗的子系，則會避免焦點還原。 | 無。 |
| **集合中的項目** | 如果未排序 <xref:System.Windows.Data.CollectionView>，則項目在移動或新增至基礎集合後會出現在相同相對位置的 <xref:System.Windows.Data.CollectionView> 中。 這會提供項目在集合中的位置與在相關聯 <xref:System.Windows.Data.CollectionView> 中的位置之間的一致性。 | 請使用 <xref:System.Windows.Controls.ItemContainerGenerator.ContainerFromItem%2A> 或 <xref:System.Windows.Data.CollectionView.IndexOf%2A> 方法找到項目在 <xref:System.Windows.Data.CollectionView> 中的位置，而不是依賴項目的固定位置。 |
| **版面配置** | 若要去除不必要的重新版面配置，則變更 <xref:System.Windows.Controls.Page.ShowsNavigationUI> 不再讓版面配置失效，或導致另一個版面配置階段。 | 如果您預期變更 <xref:System.Windows.Controls.Page.ShowsNavigationUI> 會導致另一個版面配置階段，請在設定屬性之後呼叫 <xref:System.Windows.UIElement.InvalidateVisual%2A>。 |
| **功能表** | 若要在功能表快顯視窗中啟用 ClearType 文字，則已修改 <xref:System.Windows.Controls.ControlTemplate> 類別和 <xref:System.Windows.Controls.MenuItem> 控制項以及其他控制項。 | 應用程式不應該依賴控制項範本的視覺效果結構。 只有 <xref:System.Windows.Controls.ControlTemplate> 的具名部分才是公用合約的一部分。 如果應用程式必須在 <xref:System.Windows.Controls.ControlTemplate> 中找到特定物件，請搜尋視覺化樹狀結構中是否有特定類型，而不是依賴樹狀結構中某個物件的固定位置。 |
| **瀏覽** | 如果 <xref:System.Windows.Controls.Frame> 直接瀏覽至某個位置，則在初始瀏覽之後，<xref:System.Windows.Navigation.NavigatingCancelEventArgs.IsNavigationInitiator> 屬性是 `true`。 這項變更可防止在啟動案例期間引發其他事件。 | 無。 |
| **快顯視窗** | 在版面配置階段期間，現在可以呼叫 <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> 委派多次，而不是只呼叫一次。 | 如果您的 <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> 委派會根據先前的位置計算 <xref:System.Windows.Controls.Primitives.Popup> 的位置，則只有在 `popupSize`、`targetSize` 或 `offset` 參數的值變更時，才會重新計算位置。 |
| **屬性值** | <xref:System.Windows.DependencyObject.SetCurrentValue%2A> 方法現在可讓您將屬性設定為有效值，但仍然會接受影響該屬性的任何繫結、樣式或觸發程序。 | 只要屬性值變更為某個其他動作的副作用 (包含使用者操作)，控制項作者應該就會使用 <xref:System.Windows.DependencyObject.SetCurrentValue%2A>。 |
| **文字方塊** | 基於安全性考量，<xref:System.Windows.Forms.TextBoxBase.Copy%2A> 和 <xref:System.Windows.Forms.TextBoxBase.Cut%2A> 方法以部分信任呼叫時會以無訊息模式失敗。<br><br>此外，以程式設計方式在繼承自 <xref:System.Windows.Controls.Primitives.TextBoxBase> 的控制項上執行 <xref:System.Windows.Input.ApplicationCommands.Copy> 或 <xref:System.Windows.Input.ApplicationCommands.Cut> 屬性，將會在部分信任中予以封鎖。 不過，使用者啟動的複製和剪下命令 (例如，按一下其 <xref:System.Windows.Controls.Primitives.ButtonBase.Command> 屬性繫結至其中一個命令的按鈕) 將會運作。 透過鍵盤快速鍵和操作功能表的標準複製和剪下，仍然會如之前在部分信任中運作。 | 將 <xref:System.Windows.Input.ApplicationCommands.Copy> 或 <xref:System.Windows.Input.ApplicationCommands.Cut> 命令繫結至使用者起始的動作，例如按一下按鈕。 |

### <a name="graphics"></a>圖形

命名空間：<xref:System.Windows>、<xref:System.Windows.Controls>、<xref:System.Windows.Data>、<xref:System.Windows.Input>、<xref:System.Windows.Media.Effects>；組件：PresentationFramework (在 PresentationFramework.dll 中)、PresentationCore (在 PresentationCore.dll 中)、WindowsBase (在 WindowsBase.dll 中)

| 功能 | 3.5 SP1 的差異 | 建議變更 |
| ------- | ------------------------ | ------------------- |
| **點陣圖效果** | 為了改善效能，<xref:System.Windows.Media.Effects.BitmapEffect> 類別以及繼承自 <xref:System.Windows.Media.Effects.BitmapEffect> 類別的類別雖然仍然存在，但已予以停用。 如果下列條件成立，則會使用硬體加速轉譯管線來轉譯效果：<br><br>* 應用程式使用半徑屬性集小於 100 DIU 的 <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> 或 <xref:System.Windows.Media.Effects.BlurBitmapEffect>。<br>* 執行應用程式之電腦上的視訊卡支援像素著色器 2.0。<br><br>如果不符合這些條件，則 <xref:System.Windows.Media.Effects.BitmapEffect> 物件不會有任何作用。<br><br>此外，Visual Studio 2010 在遇到 <xref:System.Windows.Media.Effects.BitmapEffect> 物件或子類別時將會產生編譯器警告。<br><br><xref:System.Windows.Media.DrawingContext.PushEffect%2A> 方法已標示為過時。 | 停止使用舊版 <xref:System.Windows.Media.Effects.BitmapEffect> 和衍生類別，而是改成使用衍生自 <xref:System.Windows.Media.Effects.Effect> 的新類別：<xref:System.Windows.Media.Effects.BlurEffect>、<xref:System.Windows.Media.Effects.DropShadowEffect> 和 <xref:System.Windows.Media.Effects.ShaderEffect>。<br><br>您也可以繼承自 <xref:System.Windows.Media.Effects.ShaderEffect> 類別，來建立自己的效果。 |
| **點陣圖框架** | 複製的 <xref:System.Windows.Media.Imaging.BitmapFrame> 物件現在會收到 <xref:System.Windows.Media.Imaging.BitmapSource.DownloadProgress>、<xref:System.Windows.Media.Imaging.BitmapSource.DownloadCompleted> 和 <xref:System.Windows.Media.Imaging.BitmapSource.DownloadFailed> 事件。 這可讓從 Web 下載並透過 <xref:System.Windows.Style> 套用至 <xref:System.Windows.Controls.Image> 控制項的映像正常運作。<br><br>只有在下列所有陳述式都成立時，您才會看到行為變更：<br><br>* 您訂閱 <xref:System.Windows.Media.Imaging.BitmapSource.DownloadProgress>、<xref:System.Windows.Media.Imaging.BitmapSource.DownloadCompleted> 或 <xref:System.Windows.Media.Imaging.BitmapSource.DownloadFailed> 事件。<br>* <xref:System.Windows.Media.Imaging.BitmapFrame> 的來源是來自 Web。<br>* 在下載仍在進行時複製 <xref:System.Windows.Media.Imaging.BitmapFrame>。 | 只有在寄件者是原始 <xref:System.Windows.Media.Imaging.BitmapFrame> 時，才會檢查事件處理常式中的寄件者，並採取動作。 |
| **將影像解碼** | 為了防止在未解碼映像時處理 <xref:System.IO.IOException>，<xref:System.Windows.Media.Imaging.BitmapSource> 類別會在未解碼映像時引發 <xref:System.Windows.Media.Imaging.BitmapSource.DecodeFailed> 事件。 | 移除 <xref:System.IO.IOException> 的任何例外狀況處理，並使用 <xref:System.Windows.Media.Imaging.BitmapSource.DecodeFailed> 事件，以檢查解碼失敗。 |

### <a name="input"></a>輸入

命名空間：<xref:System.Windows>、<xref:System.Windows.Controls>、<xref:System.Windows.Data>、<xref:System.Windows.Input>；組件：PresentationFramework (在 PresentationFramework.dll 中)、PresentationCore (在 PresentationCore.dll 中)、WindowsBase (在 WindowsBase.dll 中)

| 功能 | 3.5 SP1 的差異 | 建議變更 |
| ------- | ------------------------ | ------------------- |
| **繫結命令執行個體** | 為了提供機制將檢視模型命令執行個體繫結至檢視輸入手勢，<xref:System.Windows.Input.InputBinding> 類別現在繼承自 <xref:System.Windows.Freezable>，而不是 <xref:System.Windows.DependencyObject>。 下列屬性現在是相依性屬性：<br><br>* <xref:System.Windows.Input.InputBinding.Command><br>* <xref:System.Windows.Input.InputBinding.CommandParameter><br>* <xref:System.Windows.Input.InputBinding.CommandTarget><br><br>這項變更會導致下列各項：<br><br>* <xref:System.Windows.Input.InputBinding> 物件現在在註冊後會予以凍結，而不是保持可變動。<br>* 因為 <xref:System.Windows.DependencyObject> 類別的限制，所以您無法從多個執行緒存取執行個體層級 <xref:System.Windows.Input.InputBinding> 物件。<br>* 因為 <xref:System.Windows.Freezable> 類別的限制，所以您無法在註冊之後變動類別層級輸入繫結。<br>* 您無法在檢視模型中所建立的命令執行個體上指定輸入繫結。 | 如果繫結是可變動的，或要凍結它們，請在個別執行緒上建立不同的 <xref:System.Windows.Input.InputBinding> 類別執行個體。 類別層級靜態 <xref:System.Windows.Input.InputBinding> 在註冊之後，就請不要進行變動。 |
| **瀏覽器應用程式** | WPF 瀏覽器應用程式 (.XBAP) 現在會處理獨立 WPF 應用程式這類重要事件，因此物件會依正確順序接收已路由傳送的重要事件。 | 無。 |
| **廢鍵組合** | WPF 會讓廢鍵模糊，因此不產生任何可見字元，而是改成指出按鍵是要與下一個字母鍵合併使用以產生一個字元。 <xref:System.Windows.Input.Keyboard.KeyDownEvent> 事件這類按鍵輸入事件，透過將 <xref:System.Windows.Input.KeyEventArgs.Key> 屬性設定為 <xref:System.Windows.Input.Key> 值報告按鍵何時是廢鍵。 因為應用程式通常不想要回應可建立合併字元的鍵盤輸入，所以這通常是預期行為。 | 預期會讀取屬於組合字元之按鍵的應用程式可以使用 <xref:System.Windows.Input.KeyEventArgs.DeadCharProcessedKey> 屬性來取得現在的模糊按鍵。 |
| **焦點管理員** | 將 [IsFocusScope](https://msdn.microsoft.com/library/system.windows.input.focusmanager.isfocusscope.aspx) 附加屬性設定為 `true` 的項目傳遞給 <xref:System.Windows.Input.FocusManager.GetFocusedElement(System.Windows.DependencyObject)?displayProperty=nameWithType> 方法時，此方法會傳回為該焦點範圍內最後一個鍵盤聚焦項目的項目，而且只有在所傳回的項目屬於與傳遞給方法的項目相同的 <xref:System.Windows.PresentationSource> 物件時。 | 無。 |

### <a name="ui-automation"></a>UI 自動化

命名空間：<xref:System.Windows>、<xref:System.Windows.Automation.Peers>、<xref:System.Windows.Automation.Provider>、<xref:System.Windows.Controls>、<xref:System.Windows.Data>、<xref:System.Windows.Input>；組件：PresentationFramework (在 PresentationFramework.dll 中)、PresentationCore (在 PresentationCore.dll 中)、UIAutomationProvider (在 UIAutomationProvider.dll 中)、WindowsBase (在 WindowsBase.dll 中)

| 功能 | 3.5 SP1 的差異 | 建議變更 |
| ------- | ------------------------ | ------------------- |
| **檢視類別階層** | <xref:System.Windows.Automation.Peers.TreeViewAutomationPeer> 和 <xref:System.Windows.Automation.Peers.TreeViewItemAutomationPeer> 類別繼承自 <xref:System.Windows.Automation.Peers.ItemsControlAutomationPeer>，而不是 <xref:System.Windows.Automation.Peers.FrameworkElementAutomationPeer>。 | 如果您繼承自 <xref:System.Windows.Automation.Peers.TreeViewItemAutomationPeer> 類別並覆寫 <xref:System.Windows.Automation.Peers.TreeViewItemAutomationPeer.GetChildrenCore%2A> 方法，請考慮傳回繼承自新 <xref:System.Windows.Automation.Peers.TreeViewDataItemAutomationPeer> 類別的物件。 |
| **移出螢幕的容器** | 為了修正不正確的傳回值，<xref:System.Windows.Automation.Peers.UIElementAutomationPeer.IsOffscreenCore%2A> 方法現在會正確傳回捲出檢視之項目容器的 `false`。 此外，其他視窗閉塞不會影響方法的值，項目是否出現在特定監視器也不會影響方法的值。 | 無。 |
| **功能表和子物件** | 若要啟用功能表的 UI 自動化，而功能表包含 <xref:System.Windows.Controls.MenuItem> 物件以外的子系，則 <xref:System.Windows.Automation.Peers.MenuItemAutomationPeer.GetChildrenCore%2A> 方法現在會傳回子系 <xref:System.Windows.UIElement> 物件的 <xref:System.Windows.Automation.Peers.AutomationPeer> 物件，而不是 <xref:System.Windows.Automation.Peers.MenuItemAutomationPeer> 物件。 | 無。 |
| **新增介面和組件** | 若要啟用 UI 自動化的新功能，已新增下列介面：<br><br>* <xref:System.Windows.Automation.Provider.IItemContainerProvider><br>* <xref:System.Windows.Automation.Provider.ISynchronizedInputProvider><br>* <xref:System.Windows.Automation.Provider.IVirtualizedItemProvider> | 任何建置 WPF 自動化對等的專案都必須新增 UIAutomationProvider.dll 的明確參考。 |
| **縮圖** | <xref:System.Windows.Automation.Peers.ThumbAutomationPeer.GetClassNameCore%2A> 方法會傳回值，而不是 Null。 因此，繼承自 <xref:System.Windows.Controls.Primitives.Thumb> 類別的 <xref:System.Windows.Controls.GridSplitter> 這類控制項會向 UI 自動化報告名稱。 | 無。 |
| **虛擬化項目** | 為了改善效能，<xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetChildrenCore%2A> 方法只會傳回實際在視覺化樹狀結構中的子物件，而不是所有子物件，不論是否已將它們視覺化。 | 使用 <xref:System.Windows.Automation.ItemContainerPattern> 反覆查看 <xref:System.Windows.Automation.Peers.ItemsControlAutomationPeer> 的所有項目。 |

### <a name="xaml"></a>XAML

命名空間：<xref:System.Windows>、<xref:System.Windows.Controls>、<xref:System.Windows.Data>、<xref:System.Windows.Input>、<xref:System.Windows.Markup>；組件：PresentationFramework (在 PresentationFramework.dll 中)、PresentationCore (在 PresentationCore.dll 中)、WindowsBase (在 WindowsBase.dll 中)

| 功能 | 3.5 SP1 的差異 | 建議變更 |
| ------- | ------------------------ | ------------------- |
| **標記延伸** | WPF 現在一律會正確地使用 <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> 方法的值，而不是在使用標記延伸來設定屬性或在集合中建立項目的特定情況下傳回 <xref:System.Windows.Markup.MarkupExtension> 物件。 在某些情況下，標記延伸可能會傳回它自己。 | 如果您的應用程式存取已在舊版本中傳回 <xref:System.Windows.Markup.MarkupExtension> 物件的資源，請參考從 <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> 所傳回的物件，而不是 <xref:System.Windows.Markup.MarkupExtension> 物件。 |
| **剖析屬性** | XAML 中的屬性現在只能有一個句點。 例如，下列有效：<br><br>`<Button Background="Red"/>` (沒有句點)<br><br>`<Button Button.Background = "Red"/>` (一個句點)<br><br>下列不再有效：<br><br>`<Button Control.Button.Background = "Red"/>` (多個句點) | 更正有多個句點的 XAML 屬性。 |

## <a name="xml"></a>XML

此表中的資料列描述先前有限制或其他問題之功能的改善。

### <a name="schema-and-transforms"></a>結構描述和轉換

命名空間：<xref:System.Xml.Linq>、<xref:System.Xml.Schema>、<xref:System.Xml.XPath>；組件：System.Xml (在 System.Xml.dll 中)、System.Xml.Linq (在 System.Xml.Linq.dll 中)

| 功能 | 3.5 SP1 的差異 |
| ------- | ------------------------ |
| **Chameleon 結構描述** | 為了避免資料損毀，現在，Chameleon 結構描述隨附於多個結構描述時會正確地進行複製。<br><br>Chameleon 結構描述是沒有目標命名空間的結構描述，而且它們包含於其他 XSD 時，會採用匯入結構描述的目標命名空間。 它們通常用來將一般類型併入結構描述中。 |
| **ID 函式** | 將 <xref:System.Xml.XmlReader> 物件傳遞給 XLST 時，XSLT [id 函式](/sql/xquery/functions-on-sequences-id)現在會傳回正確值，而不是 Null。<br><br>如果使用者已使用 <xref:System.Xml.Linq.XNode.CreateReader%2A> 方法從 LINQ to XML 類別建立 <xref:System.Xml.XmlReader> 物件，並且這個 <xref:System.Xml.XmlReader> 物件會傳遞至 XSLT，在過去，XSLT 中 `id` 函式的任何執行個體會傳回 Null。 這不是 `id` 函式的允許傳回值。 |
| **Namespace 屬性** | 為了避免資料損毀，<xref:System.Xml.XPath.XPathNavigator> 物件現在會正確地傳回 `x:xmlns` 屬性的本機名稱。 |
| **命名空間宣告** | 子樹上的 <xref:System.Xml.XmlReader> 物件不再於一個 XML 項目內建立重複的命名空間宣告。 |
| **結構描述驗證** | 為了防止錯誤的結構描述驗證，<xref:System.Xml.Schema.XmlSchemaSet> 類別允許正確且一致地編譯 XSD 結構描述。 這些結構描述可以包含其他結構描述；例如，`A.xsd` 可以包含 `B.xsd`，而後者可以包含 `C.xsd`。 編譯任何其中一個可周遊這個相依性圖表。 |
| **指令碼函式** | 函式實際可用時，[function-available 函式](https://msdn.microsoft.com/library/ms256124(v=vs.110).aspx)不再正確地傳回 `false`。 |
| **URI** | <xref:System.Xml.Linq.XElement.Load%2A> 方法現在會在 LINQ 查詢中傳回正確的 BaseURI。 |

### <a name="validation"></a>驗證

命名空間：<xref:System.Xml.Linq>、<xref:System.Xml.Schema>、<xref:System.Xml.XPath>；組件：System.Xml (在 System.Xml.dll 中)、System.Xml.Linq (在 System.Xml.Linq.dll 中)

| 功能 | 3.5 SP1 的差異 |
| ------- | ------------------------ |
| **命名空間解析程式** | <xref:System.Xml.XmlReader.ReadContentAs%2A> 方法不再忽略傳遞給它的 <xref:System.Xml.IXmlNamespaceResolver> 解析程式。<br><br>在舊版本中，已忽略指定的命名空間解析程式，並改成使用 <xref:System.Xml.XmlReader>。 |
| **空白字元** | 為了避免在建立讀取器時資料遺失，<xref:System.Xml.XmlReader.Create%2A> 方法不再捨棄明顯的空白字元。<br><br>XML 驗證會辨識混合內容模式，其中，文字可以與 XML 標記混合使用。 在混合模式中，所有空白字元都是重要且應予以回報的。 |

### <a name="writing"></a>撰寫

命名空間：<xref:System.Xml.Linq>、<xref:System.Xml.Schema>、<xref:System.Xml.XPath>；組件：System.Xml (在 System.Xml.dll 中)、System.Xml.Linq (在 System.Xml.Linq.dll 中)

| 功能 | 3.5 SP1 的差異 |
| ------- | ------------------------ |
| **實體參考** | 為了避免資料損毀，不再於 XML 屬性中實體化實體參考兩次。<br><br>如果使用者使用 <xref:System.Xml.XmlWriter.WriteEntityRef%2A> 方法嘗試將實體寫入至 `xmlns` 屬性或 `xml:lang` or `xml:space` 屬性，則會在輸出中實體化實體兩次，因此損毀資料。 |
| **換行處理** | 為了避免資料損毀，<xref:System.Xml.XmlWriter> 物件會使用 <xref:System.Xml.NewLineHandling> 選項。 |

## <a name="see-also"></a>另請參閱

### <a name="reference"></a>參考資料

[.NET Framework 4 中的新型別和成員](https://msdn.microsoft.com/library/ff641764(v=vs.100).aspx)

### <a name="concepts"></a>概念

[.NET Framework 4 移轉手冊](https://msdn.microsoft.com/library/ff657133(v=vs.100).aspx)   
[.NET Framework 4 的新功能](https://msdn.microsoft.com/library/ms171868(v=vs.100).aspx)   
[.NET Framework 的版本相容性](../../../docs/framework/migration-guide/version-compatibility.md)   
[將 Office 方案移轉至 .NET Framework 4](https://msdn.microsoft.com/library/ee207231.aspx)

### <a name="other-resources"></a>其他資源

[.NET Framework 的過時功能](https://msdn.microsoft.com/library/ee461502(v=vs.110).aspx)   
[Migration Issues for .NET Framework 4 Applications: Beta 2 to RTM](http://go.microsoft.com/fwlink/?LinkId=191505) (.NET Framework 4 應用程式的移轉問題：Beta 2 到 RTM)

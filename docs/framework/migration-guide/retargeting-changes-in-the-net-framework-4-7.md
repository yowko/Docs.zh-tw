---
title: ".NET Framework 4.7 中的重定目標變更 | Microsoft Docs"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- retargeting changes,.NET Framework
- retargeting changes,.NET Framework 4.7
- application compatibility
ms.assetid: d98bf1e3-0017-4933-8e7b-191ac3542fcc
caps.latest.revision: 14
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 2881049ee490bf0abdd8b2f0651ca3703ccae76a
ms.lasthandoff: 04/18/2017

---
# <a name="retargeting-changes-in-the-net-framework-47"></a>.NET Framework 4.7 中的重定目標變更

在某些罕見的情況下，重定目標變更可能會影響以 .NET Framework 4.7 為目標來重新編譯的應用程式。 這些變更不會影響以舊版 .NET Framework 為目標但在 4.7 版下執行的二進位檔。 .NET Framework 4.7 包含下列領域的重定目標變更：  

-   [核心](#Core)  
-   [ASP.NET](#asp) 
-   [Windows Communication Foundation (WCF)](#WCF)  
-   [Windows Presentation Foundation (WPF)](#WPF)
 
 下表中的 [範圍] 一欄指定每項變更的重要性：  
  
-   主要。 影響大量應用程式或需要大幅修改程式碼的重大變更。 請注意，重定目標變更不屬於此分類。  
  
-   次要。 影響少量應用程式或需要稍微修改程式碼的變更。  
  
-   邊緣。 在非常特定 (罕見) 的情況下影響應用程式的變更。  
  
-   透明。 此變更對應用程式的開發人員或使用者的影響不明顯。 發生此變更的應用程式應該不需要修改。  
  
## <a name="a-namecore--core"></a><a name="Core" /> 核心

| 功能 | 變更 | 影響 | 範圍 |
|----|----|----|----|
|<xref:System.Security.Cryptography.CspParameters.ParentWindowHandle%2A> | 以 .NET Framework 4.6.2 和先前版本為目標的應用程式，預期指派給這個屬性的值是 HWND 值所在記憶體中之指定位置的 <xref:System.IntPtr>。<br/></br>從以 .NET Framework 4.7 為目標的應用程式開始，Windows Forms 應用程式可透過以下的程式碼設定此屬性的值： <br/><br/>` cspParameters.ParentWindowHandle = form.Handle; ` | 認為這項變更的行為很不方便的應用程式可以選擇退出新行為。 同樣地，以舊版 .NET Framework 為目標，但在 .NET Framework 4.7 上執行的應用程式，可以選擇使用新的行為。 如需詳細資訊，請參閱[風險降低︰CspParameters.ParentWindowHandle 應該有 HWND](../../../docs/framework/migration-guide/mitigation-cspparameters-parentwindowhandle-expects-an-hwnd.md)。 | 次要 |
| 使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 序列化 | 從以 .NET Framework 4.7 為目標的應用程式開始，使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 序列化的控制項字元現在與 ECMAScript V6 和 V8 相容 | 這項變更符合 ECMAScript 標準且影響應該很小。 如果很大的話，可使用相容性參數來還原舊版的行為。 如需詳細資訊，請參閱[風險降低︰使用 DataContractJsonSerializer 控制字元的序列化](../../../docs/framework/migration-guide/mitigation-serialization-control-characters.md)  | Edge |

## <a name="a-nameasp--aspnet"></a><a name="asp" /> ASP.NET

| 功能  |變更  |影響 | 範圍 | 
---------|---------|---------|-----|
每一個工作階段的節流閥並行要求數目 | 在 .NET Framework 4.6.2 和先前版本中，ASP.NET 會使用相同的 <xref:System.Web.SessionState.HttpSessionState.SessionID%2A> 循序執行要求，且 ASP.NET 預設總是會透過 Cookie 發出 <xref:System.Web.SessionState.HttpSessionState.SessionID%2A>。 如果網頁花費很長的時間載入，按下瀏覽器的 <kbd>F5</kbd> 會使伺服器效能大幅下降。<br/><br/>從 .NET Framework 4.7 開始，會有一個計數器追蹤佇列要求，並在超過指定限制時終止要求。 預設值為 50。 如果達到限制，會在事件記錄檔記錄警告並在 IIS 記錄檔中記錄 HTTP 500 回應。|這項變更可以改善整體伺服器效能。<br/><br/>若要還原舊行為，您可以將下列設定加入您的 web.config 檔案以選擇退出新行為。<br/><br/>`<appSettings>`<br/>&nbsp;&nbsp;&nbsp;`<add key="aspnet:RequestQueueLimitPerSession" value="2147483647"/>`<br/>`</appSettings>` | Edge |

## <a name="a-namewcf--windows-communication-foundation"></a><a name="WCF" /> Windows Communication Foundation

| 功能  |變更  |影響 | 範圍 | 
---------|---------|---------|-----|
| WCF 訊息安全性 | 在 .NET Framework 4.7 或更新版本執行的應用程式能透過應用程式組態設定使用 WCF 訊息安全性中的 TLS 1.1 和 TLS 1.2。 這是選擇性功能。根據預設，支援 WCF 訊息安全性中的 TLS 1.1 和 TLS 1.2 會停用。 | WCF 訊息安全性的預設行為保持不變。 <br/><br/> 若要啟用支援 TLS 1.1 和 TLS 1.2，可在 `app.config` 的 [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md)區段或 `web.config` 檔案加入下列組態設定︰  <br/><br/>`<runtime>` <br/> &nbsp;&nbsp;&nbsp;`<AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;`<br/>&nbsp;&nbsp;&nbsp;`Switch.System.Net.DontEnableSchUseStrongCrypto=false" />`<br/>`</runtime>` | Edge |         

## <a name="a-namewpf--windows-presentation-foundation-wpf"></a><a name="WPF" /> Windows Presentation Foundation (WPF)  

| 功能 | 變更 | 影響 | 範圍 |
|---|---|---|---|
| <xref:System.Windows.Controls.Grid> 控制項的對 Star-columns 的空間配置 | 從以 .NET Framework 4.7 為目標的應用程式開始，WPF 取代了 <xref:System.Windows.Controls.Grid> 控制項用來配置 \*-columns.md) 空間的演算法 | 對於以 .NET Framework 為目標的應用程式，從 .NET Framework 4.7 開始，這項變更在數種情況下都會影響指派給 \*-columns 的實際寬度。 如果這項變更不恰當，可以在應用程式組態檔中加入項目，以繼續套用先前的演算法。 如需詳細資訊，請參閱[風險降低︰方格控制項對 Star-columns 的空間配置](../../../docs/framework/migration-guide/mitigation-grid-control.md)。 | 次要 |
| <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom%2A> | 在以 .NET Framework 4.6.2 和先前版本為目標的應用程式中，<xref:System.Windows.Media.ImageSourceConverter.ConvertFrom%2A> 方法的例外狀況處理程式碼中的錯誤會造成擲回 [NullReferenceException](assetId:///T:System.NullReferenceException]，而不是預期的例外狀況 (例如 [DirectoryNotFoundException](assetId:///T:System.IO.DirectoryNotFoundException) 或 [FileNotFoundException](assetId:///T:System.IO.FileNotFoundException)。<br/><br/>從以.NET Framework 4.7 為目標的應用程式開始，都會擲回正確的例外狀況。  | 以 .NET Framework 4.7 為目標且倚賴處理 [NullReferenceException](assetId:///T:System.NullReferenceException) 的應用程式，可以在 `app.config` 檔案的 [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段將下列設定加入至組態設定，以還原舊版的行為： <br/><br/>`<runtime>`<br/>&nbsp;&nbsp;&nbsp;`<AppContextSwitchOverrides value="Switch.System.Windows.Media.ImageSourceConverter.OverrideExceptionWithNullReferenceException=true"/>`<br/>`</runtime>`| Edge | 
| 選擇支援以 `WM_POINTER` 為基礎的觸控/手寫筆堆疊 | 從以.NET Framework 4.7 為目標的應用程式開始，WPF 新增支援選擇性以 `WM_POINTER 為基礎的觸控。  | 從 Windows 10 Creators Update 開始，這是可在 Windows 系統上使用的一項選擇性功能。 未明確地選擇支援以指標為基礎的觸控/手寫筆的 WPF 應用程式不會受到影響。 如需詳細資訊，請參閱[風險降低︰以指標為基礎的觸控及手寫筆支援](../Topic/Mitigation:%20Pointer-based%20Touch%20and%20Stylus%20Support.md)。 | Edge |
| [PrintQueue](assetId:///T:System.Printing.PrintQueue) 類別 | 從 .NET Framework 4.7 開始，使用 [PrintQueue](assetId:///T:System.Printing.PrintQueue) 的 WPF 列印 API 預設會呼叫 Windows 列印文件封裝 API，而不是現已遭到取代的 XPS 列印 API。<br/><br/>舊版 Windows 上的舊列印堆疊會繼續如往常一般運作。 | 使用者和開發人員都不應該會看到行為或 API 使用方式中有任何變更。 <br/><br/>若要在 Windows 10 Creators Update 中使用舊堆疊，可以將 `HKEY_CURRENT_USER\Software\Microsoft.NETFramework\Windows Presentation Foundation\Printing` 登錄機碼的 `UseXpsOMPrinting` `REG_DWORD`值設為 1。 | Edge | 
## <a name="see-also"></a>請參閱
[.NET Framework 4.7 中的應用程式相容性](Application%20Compatibility%20in%20the%20.NET%20Framework%204.7.md)


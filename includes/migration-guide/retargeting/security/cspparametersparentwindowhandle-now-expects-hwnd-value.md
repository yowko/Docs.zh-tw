---
ms.openlocfilehash: 72f907c117748fb19ca0663f24445a8c978afd32
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "68235606"
---
### <a name="cspparametersparentwindowhandle-now-expects-hwnd-value"></a>CspParameters.ParentWindowHandle 現在預期有 HWND 值

|   |   |
|---|---|
|詳細資料|.NET Framework 2.0 中引進的 <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> 值，可讓應用程式註冊父視窗控制代碼值，因而存取金鑰所需的任何 UI (如 PIN 提示或同意對話方塊) 在指定的視窗會開啟為強制回應子項。從以 .NET Framework 4.7 為目標的應用程式開始，Windows Forms 應用程式可以使用如下的程式碼設定 <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> 屬性：<pre><code class="lang-csharp">cspParameters.ParentWindowHandle = form.Handle;&#13;&#10;</code></pre>在舊版 .NET Framework 中，值必須為 <xref:System.IntPtr?displayProperty=name>，代表存放 [HWND](https://docs.microsoft.com/windows/desktop/WinProg/windows-data-types#HWND) 值之記憶體中的位置。 在 Windows 7 和舊版中，將屬性設為 form.Handle 不會有任何作用，但在 Windows 8 和更新的版本中，則會導致 &quot;<xref:System.Security.Cryptography.CryptographicException?displayProperty=name>：參數不正確。&quot;|
|建議|以 .NET Framework 4.7 或更新版本為目標的應用程式若要註冊父視窗關聯性，建議使用以下的簡化格式︰<pre><code class="lang-csharp">cspParameters.ParentWindowHandle = form.Handle;&#13;&#10;</code></pre>使用者如已發現要傳遞的正確值，是 <code>form.Handle</code> 值所在之記憶體位置的位址，則可以藉由將 AppContext 參數 <code>Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle</code> 設為 <code>true</code> 以選擇退出行為變更：<ol><li>以程式設計方式設定 AppContext 的相容性參數，如[這裡](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46)所述。</li><li>將下列程式行加入至 app.config 檔案的 <code>&lt;runtime&gt;</code> 區段：</li></ol><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>相反地，若使用者想在應用程式在舊版 .NET Framework 下載入時，選擇加入 .NET Framework 4.7 執行階段上的新行為，可以將 AppContext 參數設為 <code>false</code>。|
|影響範圍|Minor|
|版本|4.7|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.Security.Cryptography.CspParameters.ParentWindowHandle?displayProperty=nameWithType></li></ul>|

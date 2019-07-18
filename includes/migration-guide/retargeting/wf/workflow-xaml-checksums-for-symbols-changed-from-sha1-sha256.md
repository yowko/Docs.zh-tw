---
ms.openlocfilehash: 9c54572b8dcedaa103db8503cfc1155b4698c3ed
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803490"
---
### <a name="workflow-xaml-checksums-for-symbols-changed-from-sha1-to-sha256"></a>符號的工作流程 XAML 總和檢查碼從 SHA1 變更為 SHA256

|   |   |
|---|---|
|詳細資料|為了支援 Visual Studio 偵錯，工作流程執行階段會使用雜湊演算法為工作流程 XAML 檔案產生總和檢查碼。 在 .NET Framework 4.6.2 和更早版本中，工作流程總和檢查碼雜湊使用 MD5 演算法，它會在啟用 FIPS 的系統上造成問題。 從 .NET Framework 4.7 開始，預設的演算法已變更為 SHA1。 從 .NET Framework 4.8 開始，預設的演算法已變更為 SHA256。|
|建議|如果您的程式碼因為總和檢查碼失敗，而無法載入工作流程執行個體，或找不到適當的符號，請嘗試將 <code>AppContext</code> 參數 &quot;Switch.System.Activities.UseSHA1HashForDebuggerSymbols&quot; 設為 true。在程式碼中：<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Activities.UseSHA1HashForDebuggerSymbols&quot;, true);&#13;&#10;</code></pre>或者，在組態中：<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Activities.UseSHA1HashForDebuggerSymbols=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|範圍|次要|
|版本|4.8|
|類型|正在重定目標|


---
ms.openlocfilehash: f59c9f048bb3cd3f425e36b931302258fcf693f5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803518"
---
### <a name="workflow-xoml-file-checksums-changed-from-md5-to-sha256"></a>工作流程 XOML 檔案總和檢查碼已從 MD5 變更為 SHA256

|   |   |
|---|---|
|詳細資料|為了支援搭配 Visual Studio 偵錯 XOML 式的工作流程，建置包含 XOML 檔案的工作流程專案時，XOML 檔案內容的總和檢查碼會作為 <xref:System.Workflow.ComponentModel.Compiler.WorkflowMarkupSourceAttribute.MD5Digest?displayProperty=nameWithType> 值包含在所產生程式碼中。 在 .NET Framework 4.7.2 及更早版本中，這個總和檢查碼雜湊會使用 MD5 演算法，它會在啟用 FIPS 的系統上造成問題。 從 .NET Framework 4.8 開始，所使用的演算法是 SHA256。 為了與 WorkflowMarkupSourceAttribute.MD5Digest 相容，只會使用所產生總和檢查碼的前 16 個位元組。這可能會在偵錯時造成問題。 您可能需要重新建置您的專案。|
|建議|若重新建置您的專案沒有解決問題，請嘗試將 <code>AppContext</code> 切換 &quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot; 設為 True。在程式碼中：<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot;, true);&#13;&#10;</code></pre>或是在組態檔內 (這需要在您所使用 MSBuild.exe 的 MSBuild.exe.config 中)：<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|影響範圍|Minor|
|版本|4.8|
|類型|正在重定目標|

---
ms.openlocfilehash: 81b104d8e5a9ccc8e790c3b16e4837cfa0c0def5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803483"
---
### <a name="serialport-background-thread-exceptions"></a>SerialPort 背景執行緒例外狀況

|   |   |
|---|---|
|詳細資料|使用 <xref:System.IO.Ports.SerialPort> 資料流建立的背景執行緒與不會再於擲回 OS 的例外狀況時終止處理序。 <br/>在以 .NET Framework 4.7 和舊版為目標的應用程式中，當使用 <xref:System.IO.Ports.SerialPort> 資料流建立的背景執行緒上擲回作業系統例外狀況時，處理程序會終止。 <br/>在目標為 .NET Framework 4.7.1 或更新版本的應用程式中，背景執行緒會等候與作用中的序列連接埠相關且在某些情況下可能會損毀的 OS 事件，例如突然移除序列連接埠。|
|建議|若為以 .NET Framework 4.7.1 為目標的應用程式，如果不需要例外狀況處理，您可以透過將下列內容新增至 <code>app.config</code> 檔案的 <code>&lt;runtime&gt;</code> 區段以選擇退出例外狀況處理︰<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>若為以舊版 .NET Framework 為目標但卻在 .NET Framework 4.7.1 或更新版本上執行的應用程式，則可將下列內容新增至 <code>app.config</code> 檔案的 <code>&lt;runtime&gt;</code> 區段，以選擇加入例外狀況處理：<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|範圍|次要|
|版本|4.7.1|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.IO.Ports.SerialPort?displayProperty=nameWithType></li></ul>|

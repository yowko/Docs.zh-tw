---
ms.openlocfilehash: 318609c15d2e0b9a7ee59b38463735b33ef87974
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236179"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a>WCF PipeConnection.GetHashAlgorithm 現在會使用 SHA256

|   |   |
|---|---|
|詳細資料|從 .NET Framework 4.7.1 開始，Windows Communication Foundation 會使用 SHA256 雜湊來產生具名管道的隨機名稱。 在 .NET Framework 4.7 和舊版中，它已使用 SHA1 雜湊。|
|建議|如果在 .NET Framework 4.7.1 或更新版本上遇到這項變更的相容性問題，您可以在 app.config 檔案的 <code>&lt;runtime&gt;</code> 區段中新增下列程式行來退出變更：<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|範圍|次要|
|版本|4.7.1|
|類型|執行階段|

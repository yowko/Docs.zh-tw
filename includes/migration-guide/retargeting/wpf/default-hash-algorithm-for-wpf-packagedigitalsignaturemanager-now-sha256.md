---
ms.openlocfilehash: d3e0a61601f60a389b662f6f74934b6e6dc6e663
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614586"
---
### <a name="the-default-hash-algorithm-for-wpf-packagedigitalsignaturemanager-is-now-sha256"></a>WPF PackageDigitalSignatureManager 的預設雜湊演算法現在是 SHA256

#### <a name="details"></a>詳細資料

`System.IO.Packaging.PackageDigitalSignatureManager` 提供與 WPF 套件相關的數位簽章功能。  在 .NET Framework 4.7 和舊版中，用來簽署套件各部分的預設演算法 (<xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType>) 是 SHA1。  由於最新的 SHA1 安全性考量之故，這個預設值從 .NET Framework 4.7.1 開始已變更為 SHA256。  這項變更會影響所有套件簽署，包括 XPS 文件。

#### <a name="suggestion"></a>建議

開發人員若想要在目標設為低於 .NET Framework 4.7.1 的 Framework 版本時利用這項變更，或在目標設為 .NET Framework 4.7.1 或更高版本時使用先前的功能，可以適當地設定下列 AppContext 旗標。  true 值會導致使用 SHA1 作為預設演算法；false 值則導致使用 SHA256。<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.UseSha1AsDefaultHashAlgorithmForDigitalSignatures=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Edge        |
| 版本 | 4.7.1       |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType>

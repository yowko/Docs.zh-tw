---
ms.openlocfilehash: aadf5eb85c8736c29639d49bc8baf21545d2467c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606262"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a>.NET COM 成功封送處理事件上的 ByRef SafeArray 參數

#### <a name="details"></a>詳細資料

在 .NET Framework 4.7.2 和舊版中，COM 事件上的 ByRef [SafeArray](/windows/desktop/api/oaidl/ns-oaidl-safearray) 參數無法封送處理回機器碼。  現在，透過這項變更，系統可成功封送處理 [SafeArray](/windows/desktop/api/oaidl/ns-oaidl-safearray)。<ul><li>[ x ] Quirked</li></ul>

#### <a name="suggestion"></a>建議

如果正確封送處理 COM 事件上的 ByRef SafeArray 參數會導致執行中斷，您可以將下列組態參數新增至應用程式組態來停用此程式碼：<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |Minor|
|版本|4.8|
|類型|執行階段|

#### <a name="affected-apis"></a>受影響的 API

無法透過 API 分析偵測。

<!--

#### Affected APIs

Not detectable via API analysis.

-->

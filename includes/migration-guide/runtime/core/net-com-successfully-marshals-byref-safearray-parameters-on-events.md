---
ms.openlocfilehash: 9c72bc686e014a0bffdf272e3813358d1b29cc66
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2019
ms.locfileid: "65198869"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a>.NET COM 成功封送處理事件上的 ByRef SafeArray 參數

|   |   |
|---|---|
|詳細資料|在 .NET Framework 4.7.2 和舊版中，COM 事件上的 ByRef [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) 參數無法封送處理回機器碼。  透過這項變更，[SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) 現在會成功封送處理。<ul><li>[ x ] Quirked</li></ul>|
|建議|如果正確封送處理 COM 事件上的 ByRef SafeArray 參數會中斷執行，您可以將下列設定參數新增至應用程式設定來停用此程式碼：<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|範圍|次要|
|版本|4.8|
|類型|執行階段|

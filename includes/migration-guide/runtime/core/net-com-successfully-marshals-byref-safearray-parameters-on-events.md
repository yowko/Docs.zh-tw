---
ms.openlocfilehash: 2f4f92c8615b328caee2ad0b90028c76048026f4
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802577"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a>.NET COM 成功封送處理事件上的 ByRef SafeArray 參數

|   |   |
|---|---|
|詳細資料|在 .NET Framework 4.7.2 和舊版中，COM 事件上的 ByRef [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) 參數無法封送處理回機器碼。  現在，透過這項變更，系統可成功封送處理 [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray)。<ul><li>[ x ] Quirked</li></ul>|
|建議|如果正確封送處理 COM 事件上的 ByRef SafeArray 參數會導致執行中斷，您可以將下列組態參數新增至應用程式組態來停用此程式碼：<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|範圍|次要|
|版本|4.8|
|類型|執行階段|


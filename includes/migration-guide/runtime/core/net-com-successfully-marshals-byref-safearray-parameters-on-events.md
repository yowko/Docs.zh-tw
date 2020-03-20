---
ms.openlocfilehash: 6ff23bbe8c48235770d39cb7d35a1df7de6c5201
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "68440256"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a><span data-ttu-id="8babb-101">.NET COM 成功封送處理事件上的 ByRef SafeArray 參數</span><span class="sxs-lookup"><span data-stu-id="8babb-101">.NET COM successfully marshals ByRef SafeArray parameters on events</span></span>

|   |   |
|---|---|
|<span data-ttu-id="8babb-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8babb-102">Details</span></span>|<span data-ttu-id="8babb-103">在 .NET Framework 4.7.2 和舊版中，COM 事件上的 ByRef [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) 參數無法封送處理回機器碼。</span><span class="sxs-lookup"><span data-stu-id="8babb-103">In the .NET Framework 4.7.2 and earlier versions, a ByRef [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) parameter on a COM event would fail to marshal back to native code.</span></span>  <span data-ttu-id="8babb-104">現在，透過這項變更，系統可成功封送處理 [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray)。</span><span class="sxs-lookup"><span data-stu-id="8babb-104">With this change the [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) is now marshalled successfully.</span></span><ul><li><span data-ttu-id="8babb-105">[ x ] Quirked</span><span class="sxs-lookup"><span data-stu-id="8babb-105">[ x ] Quirked</span></span></li></ul>|
|<span data-ttu-id="8babb-106">建議</span><span class="sxs-lookup"><span data-stu-id="8babb-106">Suggestion</span></span>|<span data-ttu-id="8babb-107">如果正確封送處理 COM 事件上的 ByRef SafeArray 參數會導致執行中斷，您可以將下列組態參數新增至應用程式組態來停用此程式碼：</span><span class="sxs-lookup"><span data-stu-id="8babb-107">If properly marshalling ByRef SafeArray parameters on COM Events breaks execution, you can disable this code by adding the following configuration switch to your application config:</span></span><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="8babb-108">影響範圍</span><span class="sxs-lookup"><span data-stu-id="8babb-108">Scope</span></span>|<span data-ttu-id="8babb-109">Minor</span><span class="sxs-lookup"><span data-stu-id="8babb-109">Minor</span></span>|
|<span data-ttu-id="8babb-110">版本</span><span class="sxs-lookup"><span data-stu-id="8babb-110">Version</span></span>|<span data-ttu-id="8babb-111">4.8</span><span class="sxs-lookup"><span data-stu-id="8babb-111">4.8</span></span>|
|<span data-ttu-id="8babb-112">類型</span><span class="sxs-lookup"><span data-stu-id="8babb-112">Type</span></span>|<span data-ttu-id="8babb-113">執行階段</span><span class="sxs-lookup"><span data-stu-id="8babb-113">Runtime</span></span>|

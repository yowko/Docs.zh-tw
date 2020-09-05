---
ms.openlocfilehash: 1907c9b82c9685899d328f67da8001c0fa4fb697
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496853"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a><span data-ttu-id="e99e6-101">.NET COM 成功封送處理事件上的 ByRef SafeArray 參數</span><span class="sxs-lookup"><span data-stu-id="e99e6-101">.NET COM successfully marshals ByRef SafeArray parameters on events</span></span>

#### <a name="details"></a><span data-ttu-id="e99e6-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e99e6-102">Details</span></span>

<span data-ttu-id="e99e6-103">在 .NET Framework 4.7.2 和舊版中，COM 事件上的 ByRef [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) 參數無法封送處理回機器碼。</span><span class="sxs-lookup"><span data-stu-id="e99e6-103">In the .NET Framework 4.7.2 and earlier versions, a ByRef [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) parameter on a COM event would fail to marshal back to native code.</span></span>  <span data-ttu-id="e99e6-104">現在，透過這項變更，系統可成功封送處理 [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray)。</span><span class="sxs-lookup"><span data-stu-id="e99e6-104">With this change the [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) is now marshalled successfully.</span></span><ul><li><span data-ttu-id="e99e6-105">[ x ] Quirked</span><span class="sxs-lookup"><span data-stu-id="e99e6-105">[ x ] Quirked</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="e99e6-106">建議</span><span class="sxs-lookup"><span data-stu-id="e99e6-106">Suggestion</span></span>

<span data-ttu-id="e99e6-107">如果正確封送處理 COM 事件上的 ByRef SafeArray 參數會導致執行中斷，您可以將下列組態參數新增至應用程式組態來停用此程式碼：</span><span class="sxs-lookup"><span data-stu-id="e99e6-107">If properly marshalling ByRef SafeArray parameters on COM Events breaks execution, you can disable this code by adding the following configuration switch to your application config:</span></span><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="e99e6-108">名稱</span><span class="sxs-lookup"><span data-stu-id="e99e6-108">Name</span></span>    | <span data-ttu-id="e99e6-109">值</span><span class="sxs-lookup"><span data-stu-id="e99e6-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e99e6-110">範圍</span><span class="sxs-lookup"><span data-stu-id="e99e6-110">Scope</span></span>   |<span data-ttu-id="e99e6-111">Minor</span><span class="sxs-lookup"><span data-stu-id="e99e6-111">Minor</span></span>|
|<span data-ttu-id="e99e6-112">版本</span><span class="sxs-lookup"><span data-stu-id="e99e6-112">Version</span></span>|<span data-ttu-id="e99e6-113">4.8</span><span class="sxs-lookup"><span data-stu-id="e99e6-113">4.8</span></span>|
|<span data-ttu-id="e99e6-114">類型</span><span class="sxs-lookup"><span data-stu-id="e99e6-114">Type</span></span>|<span data-ttu-id="e99e6-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="e99e6-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="e99e6-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="e99e6-116">Affected APIs</span></span>

<span data-ttu-id="e99e6-117">無法透過 API 分析偵測。</span><span class="sxs-lookup"><span data-stu-id="e99e6-117">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->

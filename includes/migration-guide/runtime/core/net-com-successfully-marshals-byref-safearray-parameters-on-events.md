---
ms.openlocfilehash: 9c72bc686e014a0bffdf272e3813358d1b29cc66
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2019
ms.locfileid: "65198869"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a><span data-ttu-id="5bd03-101">.NET COM 成功封送處理事件上的 ByRef SafeArray 參數</span><span class="sxs-lookup"><span data-stu-id="5bd03-101">.NET COM successfully marshals ByRef SafeArray parameters on events</span></span>

|   |   |
|---|---|
|<span data-ttu-id="5bd03-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5bd03-102">Details</span></span>|<span data-ttu-id="5bd03-103">在 .NET Framework 4.7.2 和舊版中，COM 事件上的 ByRef [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) 參數無法封送處理回機器碼。</span><span class="sxs-lookup"><span data-stu-id="5bd03-103">In the .NET Framework 4.7.2 and earlier versions, a ByRef [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) parameter on a COM event would fail to marshal back to native code.</span></span>  <span data-ttu-id="5bd03-104">透過這項變更，[SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) 現在會成功封送處理。</span><span class="sxs-lookup"><span data-stu-id="5bd03-104">With this change the [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) is now marshaled successfully.</span></span><ul><li><span data-ttu-id="5bd03-105">[ x ] Quirked</span><span class="sxs-lookup"><span data-stu-id="5bd03-105">[ x ] Quirked</span></span></li></ul>|
|<span data-ttu-id="5bd03-106">建議</span><span class="sxs-lookup"><span data-stu-id="5bd03-106">Suggestion</span></span>|<span data-ttu-id="5bd03-107">如果正確封送處理 COM 事件上的 ByRef SafeArray 參數會中斷執行，您可以將下列設定參數新增至應用程式設定來停用此程式碼：</span><span class="sxs-lookup"><span data-stu-id="5bd03-107">If properly marshaling ByRef SafeArray parameters on COM Events breaks execution, you can disable this code by adding the following configuration switch to your application config:</span></span><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="5bd03-108">範圍</span><span class="sxs-lookup"><span data-stu-id="5bd03-108">Scope</span></span>|<span data-ttu-id="5bd03-109">次要</span><span class="sxs-lookup"><span data-stu-id="5bd03-109">Minor</span></span>|
|<span data-ttu-id="5bd03-110">版本</span><span class="sxs-lookup"><span data-stu-id="5bd03-110">Version</span></span>|<span data-ttu-id="5bd03-111">4.8</span><span class="sxs-lookup"><span data-stu-id="5bd03-111">4.8</span></span>|
|<span data-ttu-id="5bd03-112">類型</span><span class="sxs-lookup"><span data-stu-id="5bd03-112">Type</span></span>|<span data-ttu-id="5bd03-113">執行階段</span><span class="sxs-lookup"><span data-stu-id="5bd03-113">Runtime</span></span>|

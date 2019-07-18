---
ms.openlocfilehash: 2f4f92c8615b328caee2ad0b90028c76048026f4
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802577"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a><span data-ttu-id="c7ef3-101">.NET COM 成功封送處理事件上的 ByRef SafeArray 參數</span><span class="sxs-lookup"><span data-stu-id="c7ef3-101">.NET COM successfully marshals ByRef SafeArray parameters on events</span></span>

|   |   |
|---|---|
|<span data-ttu-id="c7ef3-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c7ef3-102">Details</span></span>|<span data-ttu-id="c7ef3-103">在 .NET Framework 4.7.2 和舊版中，COM 事件上的 ByRef [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) 參數無法封送處理回機器碼。</span><span class="sxs-lookup"><span data-stu-id="c7ef3-103">In the .NET Framework 4.7.2 and earlier versions, a ByRef [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) parameter on a COM event would fail to marshal back to native code.</span></span>  <span data-ttu-id="c7ef3-104">現在，透過這項變更，系統可成功封送處理 [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray)。</span><span class="sxs-lookup"><span data-stu-id="c7ef3-104">With this change the [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) is now marshalled successfully.</span></span><ul><li><span data-ttu-id="c7ef3-105">[ x ] Quirked</span><span class="sxs-lookup"><span data-stu-id="c7ef3-105">[ x ] Quirked</span></span></li></ul>|
|<span data-ttu-id="c7ef3-106">建議</span><span class="sxs-lookup"><span data-stu-id="c7ef3-106">Suggestion</span></span>|<span data-ttu-id="c7ef3-107">如果正確封送處理 COM 事件上的 ByRef SafeArray 參數會導致執行中斷，您可以將下列組態參數新增至應用程式組態來停用此程式碼：</span><span class="sxs-lookup"><span data-stu-id="c7ef3-107">If properly marshalling ByRef SafeArray parameters on COM Events breaks execution, you can disable this code by adding the following configuration switch to your application config:</span></span><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="c7ef3-108">範圍</span><span class="sxs-lookup"><span data-stu-id="c7ef3-108">Scope</span></span>|<span data-ttu-id="c7ef3-109">次要</span><span class="sxs-lookup"><span data-stu-id="c7ef3-109">Minor</span></span>|
|<span data-ttu-id="c7ef3-110">版本</span><span class="sxs-lookup"><span data-stu-id="c7ef3-110">Version</span></span>|<span data-ttu-id="c7ef3-111">4.8</span><span class="sxs-lookup"><span data-stu-id="c7ef3-111">4.8</span></span>|
|<span data-ttu-id="c7ef3-112">類型</span><span class="sxs-lookup"><span data-stu-id="c7ef3-112">Type</span></span>|<span data-ttu-id="c7ef3-113">執行階段</span><span class="sxs-lookup"><span data-stu-id="c7ef3-113">Runtime</span></span>|


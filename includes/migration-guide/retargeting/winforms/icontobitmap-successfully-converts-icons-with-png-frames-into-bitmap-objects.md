---
ms.openlocfilehash: 811b1a91169eeebfa056d9ecdb07d342d3b32d85
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615628"
---
### <a name="icontobitmap-successfully-converts-icons-with-png-frames-into-bitmap-objects"></a><span data-ttu-id="3baaa-101">Icon.ToBitmap 成功將具有 PNG 畫面格的圖示轉換成點陣圖物件</span><span class="sxs-lookup"><span data-stu-id="3baaa-101">Icon.ToBitmap successfully converts icons with PNG frames into Bitmap objects</span></span>

#### <a name="details"></a><span data-ttu-id="3baaa-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3baaa-102">Details</span></span>

<span data-ttu-id="3baaa-103">從以 .NET Framework 4.6 為目標的應用程式開始，<xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> 方法可將具有 PNG 框架的圖示成功轉換成點陣圖物件。</span><span class="sxs-lookup"><span data-stu-id="3baaa-103">Starting with the apps that target the .NET Framework 4.6, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method successfully converts icons with PNG frames into Bitmap objects.</span></span><p/><span data-ttu-id="3baaa-104">在以 .NET Framework 4.5.2 (含) 之前版本為目標的應用程式中，如果圖示物件具有 PNG 框架，則 <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> 方法會擲回 <xref:System.ArgumentOutOfRangeException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3baaa-104">In apps that target the .NET Framework 4.5.2 and earlier versions, the  <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method throws an <xref:System.ArgumentOutOfRangeException> exception if the Icon object has PNG frames.</span></span><p/><span data-ttu-id="3baaa-105">這項變更會影響重新撰寫之以 .NET Framework 4.6 為目標的應用程式，以及針對圖示物件具有 PNG 框架時所擲回的 <xref:System.ArgumentOutOfRangeException> 實作特殊處理的應用程式。</span><span class="sxs-lookup"><span data-stu-id="3baaa-105">This change affects apps that are recompiled to target the .NET Framework 4.6 and that implement special handling for the <xref:System.ArgumentOutOfRangeException> that is thrown when an Icon object has PNG frames.</span></span> <span data-ttu-id="3baaa-106">以 .NET Framework 4.6 執行時，轉換會成功，且不再擲回 <xref:System.ArgumentOutOfRangeException> ，因此不會再叫用例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="3baaa-106">When running under the .NET Framework 4.6, the conversion is successful, an <xref:System.ArgumentOutOfRangeException> is no longer thrown, and therefore the exception handler is no longer invoked.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3baaa-107">建議</span><span class="sxs-lookup"><span data-stu-id="3baaa-107">Suggestion</span></span>

<span data-ttu-id="3baaa-108">如果不需要這項行為，您可以在 app.config 檔案的 `<runtime>` 區段中新增下列項目，以保留舊版行為：</span><span class="sxs-lookup"><span data-stu-id="3baaa-108">If this behavior is undesirable, you can retain the previous behavior by adding the following element to the `<runtime>` section of your app.config file:</span></span>

<pre><code class="lang-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true&quot; /&gt;&#13;&#10;</code></pre>

<span data-ttu-id="3baaa-109">如果 app.config 檔案已經包含 `AppContextSwitchOverrides` 項目，則應以下列程式碼將新值與值屬性合併：</span><span class="sxs-lookup"><span data-stu-id="3baaa-109">If the app.config file already contains the `AppContextSwitchOverrides` element, the new value should be merged with the value attribute like this:</span></span>

<pre><code class="lang-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true;&lt;previous key&gt;=&lt;previous value&gt;&quot; /&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="3baaa-110">名稱</span><span class="sxs-lookup"><span data-stu-id="3baaa-110">Name</span></span>    | <span data-ttu-id="3baaa-111">值</span><span class="sxs-lookup"><span data-stu-id="3baaa-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3baaa-112">影響範圍</span><span class="sxs-lookup"><span data-stu-id="3baaa-112">Scope</span></span>   | <span data-ttu-id="3baaa-113">Minor</span><span class="sxs-lookup"><span data-stu-id="3baaa-113">Minor</span></span>       |
| <span data-ttu-id="3baaa-114">版本</span><span class="sxs-lookup"><span data-stu-id="3baaa-114">Version</span></span> | <span data-ttu-id="3baaa-115">4.6</span><span class="sxs-lookup"><span data-stu-id="3baaa-115">4.6</span></span>         |
| <span data-ttu-id="3baaa-116">類型</span><span class="sxs-lookup"><span data-stu-id="3baaa-116">Type</span></span>    | <span data-ttu-id="3baaa-117">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="3baaa-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="3baaa-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="3baaa-118">Affected APIs</span></span>

- <xref:System.Drawing.Icon.ToBitmap?displayProperty=nameWithType>

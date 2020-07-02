---
ms.openlocfilehash: f907cb1939e111c586d68243e6b8a8e291974e36
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615629"
---
### <a name="wpf-layout-rounding-of-margins-has-changed"></a><span data-ttu-id="56e75-101">邊界的 WPF 版面配置進位已變更</span><span class="sxs-lookup"><span data-stu-id="56e75-101">WPF layout rounding of margins has changed</span></span>

#### <a name="details"></a><span data-ttu-id="56e75-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="56e75-102">Details</span></span>

<span data-ttu-id="56e75-103">邊界的進位方式以及邊界內部的框線和背景皆有所變更。</span><span class="sxs-lookup"><span data-stu-id="56e75-103">The way in which margins are rounded and borders and the background inside of them has changed.</span></span> <span data-ttu-id="56e75-104">此變更的結果：</span><span class="sxs-lookup"><span data-stu-id="56e75-104">As a result of this change:</span></span>

- <span data-ttu-id="56e75-105">項目寬度或高度的增減最多不超過一個像素。</span><span class="sxs-lookup"><span data-stu-id="56e75-105">The width or height of elements may grow or shrink by at most one pixel.</span></span>
- <span data-ttu-id="56e75-106">物件的位置的位最多不超過一個像素。</span><span class="sxs-lookup"><span data-stu-id="56e75-106">The placement of an object can move by at most one pixel.</span></span>
- <span data-ttu-id="56e75-107">置中項目的垂直或水平位移最多不超過一個像素。</span><span class="sxs-lookup"><span data-stu-id="56e75-107">Centered elements can be vertically or horizontally off center by at most one pixel.</span></span>
<span data-ttu-id="56e75-108">預設只有以 .NET Framework 4.6 為目標的應用程式才會啟用此新版面配置。</span><span class="sxs-lookup"><span data-stu-id="56e75-108">By default, this new layout is enabled only for apps that target the .NET Framework 4.6.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="56e75-109">建議</span><span class="sxs-lookup"><span data-stu-id="56e75-109">Suggestion</span></span>

<span data-ttu-id="56e75-110">由於此修改會停用高 DPI 之 WPF 控制項右側或底端的裁剪功能，因此，應用程式若是以舊版 .NET Framework 為目標，但要在 .NET Framework 4.6 上執行，可將下行加入 app.config 檔案中的 `<runtime>` 區段來選擇使用此新行為：</span><span class="sxs-lookup"><span data-stu-id="56e75-110">Since this modification tends to eliminate clipping of the right or bottom of WPF controls at high DPIs, apps that target earlier versions of the .NET Framework but are running on the .NET Framework 4.6 can opt into this new behavior by adding the following line to the `<runtime>` section of the app.config file:</span></span>

<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false&quot; /&gt;&#39;&#13;&#10;</code></pre>

<span data-ttu-id="56e75-111">應用程式若是以 .NET Framework 4.6 為目標，但想使用先前的配置演算法來呈現 WPF 控制項，可將下行新增至 app.config 檔案中的 `<runtime>` 區段，以執行此作業：</span><span class="sxs-lookup"><span data-stu-id="56e75-111">Apps that target the .NET Framework 4.6 but want WPF controls to render using the previous layout algorithm can do so by adding the following line to the `<runtime>` section of the app.config file:</span></span>

<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true&quot; /&gt;&#39;.&#13;&#10;</code></pre>

| <span data-ttu-id="56e75-112">名稱</span><span class="sxs-lookup"><span data-stu-id="56e75-112">Name</span></span>    | <span data-ttu-id="56e75-113">值</span><span class="sxs-lookup"><span data-stu-id="56e75-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="56e75-114">影響範圍</span><span class="sxs-lookup"><span data-stu-id="56e75-114">Scope</span></span>   | <span data-ttu-id="56e75-115">Minor</span><span class="sxs-lookup"><span data-stu-id="56e75-115">Minor</span></span>       |
| <span data-ttu-id="56e75-116">版本</span><span class="sxs-lookup"><span data-stu-id="56e75-116">Version</span></span> | <span data-ttu-id="56e75-117">4.6</span><span class="sxs-lookup"><span data-stu-id="56e75-117">4.6</span></span>         |
| <span data-ttu-id="56e75-118">類型</span><span class="sxs-lookup"><span data-stu-id="56e75-118">Type</span></span>    | <span data-ttu-id="56e75-119">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="56e75-119">Retargeting</span></span> |

---
ms.openlocfilehash: 3d1dc8dec18212afd815aa3de7fc82c8a1f680dc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617799"
---
### <a name="hwndhost-now-correctly-resizes-child-hwnd-during-dpi-changes"></a><span data-ttu-id="83e7c-101">HwndHost 現在會在 DPI 變更期間正確調整子 HWND 的大小</span><span class="sxs-lookup"><span data-stu-id="83e7c-101">HwndHost now correctly resizes child-HWND during DPI changes</span></span>

#### <a name="details"></a><span data-ttu-id="83e7c-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="83e7c-102">Details</span></span>

<span data-ttu-id="83e7c-103">在 .NET Framework 4.7.2 和更早版本中，當 WPF 在個別監視器感知模式中執行時，裝載於 <xref:System.Windows.Interop.HwndHost> 內的控制項未在 DPI 變更後正確調整大小，例如將應用程式從某個監視器移至另一個監視器時。</span><span class="sxs-lookup"><span data-stu-id="83e7c-103">In .NET Framework 4.7.2 and earlier versions, when WPF was run in Per-Monitor Aware mode, controls hosted within <xref:System.Windows.Interop.HwndHost> were not sized correctly after DPI changes, such as when moving applications from one monitor to another.</span></span> <span data-ttu-id="83e7c-104">此修正可確保裝載的控制項適當調整大小。</span><span class="sxs-lookup"><span data-stu-id="83e7c-104">This fix ensures that hosted controls are sized appropriately.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="83e7c-105">建議</span><span class="sxs-lookup"><span data-stu-id="83e7c-105">Suggestion</span></span>

<span data-ttu-id="83e7c-106">為了讓應用程式受益於這些變更，應用程式必須於 .NET Framework 4.7.2 或更新版本執行，並且必須藉由將應用程式組態檔中 `<runtime>` 區段的 [AppContext 參數](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element)設為 `false` 來選擇使用此行為，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="83e7c-106">In order for the application to benefit from these changes, it must run on the .NET Framework 4.7.2 or later, and it must opt-in to this behavior by setting the following [AppContext Switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) in the `<runtime>` section of the app config file to `false`, as the following example shows.</span></span>

<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.DoNotUsePresentationDpiCapabilityTier2OrGreater=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="83e7c-107">名稱</span><span class="sxs-lookup"><span data-stu-id="83e7c-107">Name</span></span>    | <span data-ttu-id="83e7c-108">值</span><span class="sxs-lookup"><span data-stu-id="83e7c-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="83e7c-109">影響範圍</span><span class="sxs-lookup"><span data-stu-id="83e7c-109">Scope</span></span>   | <span data-ttu-id="83e7c-110">主要</span><span class="sxs-lookup"><span data-stu-id="83e7c-110">Major</span></span>       |
| <span data-ttu-id="83e7c-111">版本</span><span class="sxs-lookup"><span data-stu-id="83e7c-111">Version</span></span> | <span data-ttu-id="83e7c-112">4.8</span><span class="sxs-lookup"><span data-stu-id="83e7c-112">4.8</span></span>         |
| <span data-ttu-id="83e7c-113">類型</span><span class="sxs-lookup"><span data-stu-id="83e7c-113">Type</span></span>    | <span data-ttu-id="83e7c-114">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="83e7c-114">Retargeting</span></span> |

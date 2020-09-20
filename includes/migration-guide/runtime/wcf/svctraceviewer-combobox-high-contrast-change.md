---
ms.openlocfilehash: 4bc8db52efdfe483acb4f6b6e33c4fa7716e0b79
ms.sourcegitcommit: 261e0c98a111357692b3b63c596edf0cacf72991
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2020
ms.locfileid: "90770918"
---
### <a name="svctraceviewer-combobox-high-contrast-change"></a><span data-ttu-id="2b2a1-101">svcTraceViewer ComboBox 高對比變更</span><span class="sxs-lookup"><span data-stu-id="2b2a1-101">svcTraceViewer ComboBox high contrast change</span></span>

#### <a name="details"></a><span data-ttu-id="2b2a1-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2b2a1-102">Details</span></span>

<span data-ttu-id="2b2a1-103">在 [Microsoft 服務追蹤檢視器工具](~/docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)中，某些高對比佈景主題的 ComboBox 控制項未顯示正確色彩。</span><span class="sxs-lookup"><span data-stu-id="2b2a1-103">In the [Microsoft Service Trace Viewer tool](~/docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), ComboBox controls were not displayed in the correct color in certain high contrast themes.</span></span> <span data-ttu-id="2b2a1-104">此問題已在 .NET Framework 4.7.2 中修正。</span><span class="sxs-lookup"><span data-stu-id="2b2a1-104">The issue was fixed in .NET Framework 4.7.2.</span></span> <span data-ttu-id="2b2a1-105">不過，由於 .NET Framework SDK 的回溯相容性需求，因此預設為客戶看不到此項修正。</span><span class="sxs-lookup"><span data-stu-id="2b2a1-105">However, due to .NET Framework SDK backward compatibility requirements, the fix was not visible to customers by default.</span></span> <span data-ttu-id="2b2a1-106">.NET 4.8 將下列 [AppContext 組態參數](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)新增至 svcTraceViewer.exe.config 檔案，以呈現這項變更：</span><span class="sxs-lookup"><span data-stu-id="2b2a1-106">.NET 4.8 surfaces this change by adding the following [AppContext configuration switches](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to the svcTraceViewer.exe.config file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
```

#### <a name="suggestion"></a><span data-ttu-id="2b2a1-107">建議</span><span class="sxs-lookup"><span data-stu-id="2b2a1-107">Suggestion</span></span>

<span data-ttu-id="2b2a1-108">如果您不想要變更高對比行為，可以從 svcTraceViewer.exe.config 檔案中移除下列區段來停用它：</span><span class="sxs-lookup"><span data-stu-id="2b2a1-108">If you don't want to have the high contrast behavior change, you can disable it by removing the following section from the svcTraceViewer.exe.config file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
```

| <span data-ttu-id="2b2a1-109">Name</span><span class="sxs-lookup"><span data-stu-id="2b2a1-109">Name</span></span>    | <span data-ttu-id="2b2a1-110">值</span><span class="sxs-lookup"><span data-stu-id="2b2a1-110">Value</span></span>   |
|:--------|:--------|
| <span data-ttu-id="2b2a1-111">範圍</span><span class="sxs-lookup"><span data-stu-id="2b2a1-111">Scope</span></span>   | <span data-ttu-id="2b2a1-112">Edge</span><span class="sxs-lookup"><span data-stu-id="2b2a1-112">Edge</span></span>    |
| <span data-ttu-id="2b2a1-113">版本</span><span class="sxs-lookup"><span data-stu-id="2b2a1-113">Version</span></span> | <span data-ttu-id="2b2a1-114">4.8</span><span class="sxs-lookup"><span data-stu-id="2b2a1-114">4.8</span></span>     |
| <span data-ttu-id="2b2a1-115">類型</span><span class="sxs-lookup"><span data-stu-id="2b2a1-115">Type</span></span>    | <span data-ttu-id="2b2a1-116">執行階段</span><span class="sxs-lookup"><span data-stu-id="2b2a1-116">Runtime</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="2b2a1-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="2b2a1-117">Affected APIs</span></span>

<span data-ttu-id="2b2a1-118">無法透過 API 分析偵測。</span><span class="sxs-lookup"><span data-stu-id="2b2a1-118">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->

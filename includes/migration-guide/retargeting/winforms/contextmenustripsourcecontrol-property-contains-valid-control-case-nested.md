---
ms.openlocfilehash: 97299ddb9bee89c792ddb3d2b9c37516180996f7
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614400"
---
### <a name="contextmenustripsourcecontrol-property-contains-a-valid-control-in-the-case-of-nested-toolstripmenuitems"></a><span data-ttu-id="12b9d-101">在巢狀 ToolStripMenuItems 的情況下，ContextMenuStrip.SourceControl 屬性包含有效的控制項</span><span class="sxs-lookup"><span data-stu-id="12b9d-101">ContextMenuStrip.SourceControl property contains a valid control in the case of nested ToolStripMenuItems</span></span>

#### <a name="details"></a><span data-ttu-id="12b9d-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="12b9d-102">Details</span></span>

<span data-ttu-id="12b9d-103">在 .NET Framework 4.7.1 和舊版本中，當使用者從巢狀 <xref:System.Windows.Forms.ToolStripMenuItem> 控制項開啟功能表時，<xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> 屬性會誤傳回 null。</span><span class="sxs-lookup"><span data-stu-id="12b9d-103">In the .NET Framework 4.7.1 and previous versions, the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> property incorrectly returns null when the user opens the menu from nested <xref:System.Windows.Forms.ToolStripMenuItem> controls.</span></span> <span data-ttu-id="12b9d-104">在 .NET Framework 4.7.2 和更新版本中，一律會將 <xref:System.Windows.Forms.ContextMenuStrip.SourceControl> 屬性設定為實際的來源控制項。</span><span class="sxs-lookup"><span data-stu-id="12b9d-104">In the .NET Framework 4.7.2 and later, <xref:System.Windows.Forms.ContextMenuStrip.SourceControl> property is always set to the actual source control.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="12b9d-105">建議</span><span class="sxs-lookup"><span data-stu-id="12b9d-105">Suggestion</span></span>

<span data-ttu-id="12b9d-106">**如何加入宣告或退出這些變更**為了讓應用程式受益于這些變更，它必須在 .NET Framework 4.7.2 或更新版本上執行。</span><span class="sxs-lookup"><span data-stu-id="12b9d-106">**How to opt in or out of these changes** In order for an application to benefit from these changes, it must run on the .NET Framework 4.7.2 or later.</span></span> <span data-ttu-id="12b9d-107">應用程式可以用下列任一種方式受益於這些變更：</span><span class="sxs-lookup"><span data-stu-id="12b9d-107">The application can benefit from these changes in either of the following ways:</span></span>

- <span data-ttu-id="12b9d-108">以 .NET Framework 4.7.2 為目標。</span><span class="sxs-lookup"><span data-stu-id="12b9d-108">It targets the .NET Framework 4.7.2.</span></span> <span data-ttu-id="12b9d-109">在以 .NET Framework 4.7.2 或更新版本為目標的 Windows Forms 應用程式上，預設會啟用這項變更。</span><span class="sxs-lookup"><span data-stu-id="12b9d-109">This change is enabled by default on Windows Forms applications that target the .NET Framework 4.7.2 or later.</span></span>
- <span data-ttu-id="12b9d-110">以 .NET Framework 4.7.1 或舊版為目標，並選擇不使用舊版協助工具行為；方法為在 app.config 檔的 `<runtime>` 區段中新增下列 [AppContext 參數](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element)，並將其設定為 `false`，如下範例所示。</span><span class="sxs-lookup"><span data-stu-id="12b9d-110">It targets the .NET Framework 4.7.1 or an earlier version and opts out of the legacy accessibility behaviors by adding the following [AppContext Switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) to the `<runtime>` section of the app.config file and setting it to `false`, as the following example shows.</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue=false"/>
</runtime>
```

<span data-ttu-id="12b9d-111">如果應用程式是以 .NET Framework 4.7.2 或更新版本為目標，而您想要保留舊版的行為，則可以明確將此 AppContext 參數設為 `true`，選擇使用舊版的來源控制項。</span><span class="sxs-lookup"><span data-stu-id="12b9d-111">Applications that target the .NET Framework 4.7.2 or later, and want to preserve the legacy behavior can opt in to the use of the legacy source control value by explicitly setting this AppContext switch to `true`.</span></span>

| <span data-ttu-id="12b9d-112">名稱</span><span class="sxs-lookup"><span data-stu-id="12b9d-112">Name</span></span>    | <span data-ttu-id="12b9d-113">值</span><span class="sxs-lookup"><span data-stu-id="12b9d-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="12b9d-114">影響範圍</span><span class="sxs-lookup"><span data-stu-id="12b9d-114">Scope</span></span>   | <span data-ttu-id="12b9d-115">Edge</span><span class="sxs-lookup"><span data-stu-id="12b9d-115">Edge</span></span>        |
| <span data-ttu-id="12b9d-116">版本</span><span class="sxs-lookup"><span data-stu-id="12b9d-116">Version</span></span> | <span data-ttu-id="12b9d-117">4.7.2</span><span class="sxs-lookup"><span data-stu-id="12b9d-117">4.7.2</span></span>       |
| <span data-ttu-id="12b9d-118">類型</span><span class="sxs-lookup"><span data-stu-id="12b9d-118">Type</span></span>    | <span data-ttu-id="12b9d-119">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="12b9d-119">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="12b9d-120">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="12b9d-120">Affected APIs</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

---
ms.openlocfilehash: 5529b8379c5cb9f1bc525e0c2340f6b885e35822
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606707"
---
### <a name="contextmenustripsourcecontrol-property-contains-a-valid-control-in-the-case-of-nested-toolstripmenuitems"></a><span data-ttu-id="e96b7-101">在巢狀 ToolStripMenuItems 的情況下，ContextMenuStrip.SourceControl 屬性包含有效的控制項</span><span class="sxs-lookup"><span data-stu-id="e96b7-101">ContextMenuStrip.SourceControl property contains a valid control in the case of nested ToolStripMenuItems</span></span>

#### <a name="details"></a><span data-ttu-id="e96b7-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e96b7-102">Details</span></span>

<span data-ttu-id="e96b7-103">在 .NET Framework 4.7.1 和舊版本中，當使用者從巢狀 <xref:System.Windows.Forms.ToolStripMenuItem> 控制項開啟功能表時，<xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> 屬性會誤傳回 null。</span><span class="sxs-lookup"><span data-stu-id="e96b7-103">In the .NET Framework 4.7.1 and previous versions, the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> property incorrectly returns null when the user opens the menu from nested <xref:System.Windows.Forms.ToolStripMenuItem> controls.</span></span> <span data-ttu-id="e96b7-104">在 .NET Framework 4.7.2 和更新版本中，一律會將 <xref:System.Windows.Forms.ContextMenuStrip.SourceControl> 屬性設定為實際的來源控制項。</span><span class="sxs-lookup"><span data-stu-id="e96b7-104">In the .NET Framework 4.7.2 and later, <xref:System.Windows.Forms.ContextMenuStrip.SourceControl> property is always set to the actual source control.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e96b7-105">建議</span><span class="sxs-lookup"><span data-stu-id="e96b7-105">Suggestion</span></span>

<span data-ttu-id="e96b7-106">**如何加入宣告或退出這些變更** 為了讓應用程式受益于這些變更，它必須在 .NET Framework 4.7.2 或更新版本上執行。</span><span class="sxs-lookup"><span data-stu-id="e96b7-106">**How to opt in or out of these changes** In order for an application to benefit from these changes, it must run on the .NET Framework 4.7.2 or later.</span></span> <span data-ttu-id="e96b7-107">應用程式可以用下列任一種方式受益於這些變更：</span><span class="sxs-lookup"><span data-stu-id="e96b7-107">The application can benefit from these changes in either of the following ways:</span></span>

- <span data-ttu-id="e96b7-108">以 .NET Framework 4.7.2 為目標。</span><span class="sxs-lookup"><span data-stu-id="e96b7-108">It targets the .NET Framework 4.7.2.</span></span> <span data-ttu-id="e96b7-109">在以 .NET Framework 4.7.2 或更新版本為目標的 Windows Forms 應用程式上，預設會啟用這項變更。</span><span class="sxs-lookup"><span data-stu-id="e96b7-109">This change is enabled by default on Windows Forms applications that target the .NET Framework 4.7.2 or later.</span></span>
- <span data-ttu-id="e96b7-110">以 .NET Framework 4.7.1 或舊版為目標，並選擇不使用舊版協助工具行為；方法為在 app.config 檔的 `<runtime>` 區段中新增下列 [AppContext 參數](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)，並將其設定為 `false`，如下範例所示。</span><span class="sxs-lookup"><span data-stu-id="e96b7-110">It targets the .NET Framework 4.7.1 or an earlier version and opts out of the legacy accessibility behaviors by adding the following [AppContext Switch](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to the `<runtime>` section of the app.config file and setting it to `false`, as the following example shows.</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue=false"/>
</runtime>
```

<span data-ttu-id="e96b7-111">如果應用程式是以 .NET Framework 4.7.2 或更新版本為目標，而您想要保留舊版的行為，則可以明確將此 AppContext 參數設為 `true`，選擇使用舊版的來源控制項。</span><span class="sxs-lookup"><span data-stu-id="e96b7-111">Applications that target the .NET Framework 4.7.2 or later, and want to preserve the legacy behavior can opt in to the use of the legacy source control value by explicitly setting this AppContext switch to `true`.</span></span>

| <span data-ttu-id="e96b7-112">名稱</span><span class="sxs-lookup"><span data-stu-id="e96b7-112">Name</span></span>    | <span data-ttu-id="e96b7-113">值</span><span class="sxs-lookup"><span data-stu-id="e96b7-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e96b7-114">範圍</span><span class="sxs-lookup"><span data-stu-id="e96b7-114">Scope</span></span>   | <span data-ttu-id="e96b7-115">Edge</span><span class="sxs-lookup"><span data-stu-id="e96b7-115">Edge</span></span>        |
| <span data-ttu-id="e96b7-116">版本</span><span class="sxs-lookup"><span data-stu-id="e96b7-116">Version</span></span> | <span data-ttu-id="e96b7-117">4.7.2</span><span class="sxs-lookup"><span data-stu-id="e96b7-117">4.7.2</span></span>       |
| <span data-ttu-id="e96b7-118">類型</span><span class="sxs-lookup"><span data-stu-id="e96b7-118">Type</span></span>    | <span data-ttu-id="e96b7-119">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="e96b7-119">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="e96b7-120">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="e96b7-120">Affected APIs</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

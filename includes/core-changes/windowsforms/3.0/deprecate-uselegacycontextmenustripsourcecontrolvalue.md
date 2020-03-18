---
ms.openlocfilehash: 5aca2b8b3ca6572194692888eae3c5614245b481
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937109"
---
### <a name="uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a><span data-ttu-id="be389-101">不支援使用傳統內容功能表，提供資源控制值相容性開關</span><span class="sxs-lookup"><span data-stu-id="be389-101">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>

<span data-ttu-id="be389-102">.NET 框架 4.7.2 中引入的`Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue`相容性開關在 .NET Core 3.0 上的 Windows 表單中不受支援。</span><span class="sxs-lookup"><span data-stu-id="be389-102">The `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch, which was introduced in .NET Framework 4.7.2, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="be389-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="be389-103">Change description</span></span>

<span data-ttu-id="be389-104">從 .NET 框架 4.7.2`Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue`開始，相容性開關允許開發人員退出宣告<xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>屬性的新行為，該行為現在返回對原始程式碼管理的引用。</span><span class="sxs-lookup"><span data-stu-id="be389-104">Starting with the .NET Framework 4.7.2, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch allows the developer to opt out of the new behavior of the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> property, which now returns a reference to the source control.</span></span> <span data-ttu-id="be389-105">屬性的先前行為是返回`null`。</span><span class="sxs-lookup"><span data-stu-id="be389-105">The previous behavior of the property was to return `null`.</span></span> <span data-ttu-id="be389-106">有關詳細資訊，請參閱[\<應用上下文切換覆蓋>元素](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)。</span><span class="sxs-lookup"><span data-stu-id="be389-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="be389-107">在 .NET 內核`Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue`中，不支援交換器。</span><span class="sxs-lookup"><span data-stu-id="be389-107">In .NET Core, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="be389-108">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="be389-108">Version introduced</span></span>

<span data-ttu-id="be389-109">3.0 預覽 9</span><span class="sxs-lookup"><span data-stu-id="be389-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="be389-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="be389-110">Recommended action</span></span>

<span data-ttu-id="be389-111">卸下開關。</span><span class="sxs-lookup"><span data-stu-id="be389-111">Remove the switch.</span></span> <span data-ttu-id="be389-112">不支援該開關，並且沒有可用的替代功能。</span><span class="sxs-lookup"><span data-stu-id="be389-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="be389-113">類別</span><span class="sxs-lookup"><span data-stu-id="be389-113">Category</span></span>

<span data-ttu-id="be389-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="be389-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="be389-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="be389-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->

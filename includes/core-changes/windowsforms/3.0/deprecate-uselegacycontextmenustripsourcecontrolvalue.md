---
ms.openlocfilehash: 5aca2b8b3ca6572194692888eae3c5614245b481
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937109"
---
### <a name="uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a><span data-ttu-id="a311e-101">不支援 UseLegacyCoNtextMenuStripSourceControlValue 相容性切換</span><span class="sxs-lookup"><span data-stu-id="a311e-101">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>

<span data-ttu-id="a311e-102">在 .NET Framework 4.7.2 中引進的 `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` 相容性參數，在 .NET Core 3.0 的 Windows Forms 中不受支援。</span><span class="sxs-lookup"><span data-stu-id="a311e-102">The `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch, which was introduced in .NET Framework 4.7.2, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a311e-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="a311e-103">Change description</span></span>

<span data-ttu-id="a311e-104">從 .NET Framework 4.7.2 開始，`Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` 相容性參數可讓開發人員選擇不使用 <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> 屬性的新行為，這現在會傳回原始檔控制的參考。</span><span class="sxs-lookup"><span data-stu-id="a311e-104">Starting with the .NET Framework 4.7.2, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch allows the developer to opt out of the new behavior of the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> property, which now returns a reference to the source control.</span></span> <span data-ttu-id="a311e-105">先前的屬性行為是傳回 `null`。</span><span class="sxs-lookup"><span data-stu-id="a311e-105">The previous behavior of the property was to return `null`.</span></span> <span data-ttu-id="a311e-106">如需詳細資訊，請參閱[\<AppCoNtextSwitchOverrides > 元素](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)。</span><span class="sxs-lookup"><span data-stu-id="a311e-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="a311e-107">在 .NET Core 中，不支援 `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` 參數。</span><span class="sxs-lookup"><span data-stu-id="a311e-107">In .NET Core, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a311e-108">引進的版本</span><span class="sxs-lookup"><span data-stu-id="a311e-108">Version introduced</span></span>

<span data-ttu-id="a311e-109">3.0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="a311e-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a311e-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="a311e-110">Recommended action</span></span>

<span data-ttu-id="a311e-111">移除參數。</span><span class="sxs-lookup"><span data-stu-id="a311e-111">Remove the switch.</span></span> <span data-ttu-id="a311e-112">不支援此參數，而且沒有可用的替代功能。</span><span class="sxs-lookup"><span data-stu-id="a311e-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="a311e-113">分類</span><span class="sxs-lookup"><span data-stu-id="a311e-113">Category</span></span>

<span data-ttu-id="a311e-114">Windows 表單</span><span class="sxs-lookup"><span data-stu-id="a311e-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a311e-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="a311e-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->

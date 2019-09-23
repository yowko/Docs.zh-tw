---
ms.openlocfilehash: 5c1dc42a451d2c6a82e2c2429115db023c610334
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181848"
---
### <a name="switchsystemwindowsformsuselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a><span data-ttu-id="578df-101">不支援 UseLegacyCoNtextMenuStripSourceControlValue 相容性參數</span><span class="sxs-lookup"><span data-stu-id="578df-101">Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>

<span data-ttu-id="578df-102">.Net `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` Core 3.0 的 Windows Forms 不支援在 .NET Framework 4.7.2 中引進的相容性參數。</span><span class="sxs-lookup"><span data-stu-id="578df-102">The `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch, which was introduced in .NET Framework 4.7.2, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="578df-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="578df-103">Change description</span></span>

<span data-ttu-id="578df-104">從 .NET Framework 4.7.2 開始， `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue`相容性參數可讓開發人員選擇不使用<xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>屬性的新行為，這現在會傳回原始檔控制的參考。</span><span class="sxs-lookup"><span data-stu-id="578df-104">Starting with the .NET Framework 4.7.2, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch allows the developer to opt out of the new behavior of the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> property, which now returns a reference to the source control.</span></span> <span data-ttu-id="578df-105">屬性的先前行為是`null`傳回。</span><span class="sxs-lookup"><span data-stu-id="578df-105">The previous behavior of the property was to return `null`.</span></span> <span data-ttu-id="578df-106">如需詳細資訊，請參閱[ \<AppCoNtextSwitchOverrides > 元素](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)。</span><span class="sxs-lookup"><span data-stu-id="578df-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="578df-107">在 .net Core 中， `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue`不支援參數。</span><span class="sxs-lookup"><span data-stu-id="578df-107">In .NET Core, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="578df-108">引進的版本</span><span class="sxs-lookup"><span data-stu-id="578df-108">Version introduced</span></span>

<span data-ttu-id="578df-109">3.0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="578df-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="578df-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="578df-110">Recommended action</span></span>

<span data-ttu-id="578df-111">移除參數。</span><span class="sxs-lookup"><span data-stu-id="578df-111">Remove the switch.</span></span> <span data-ttu-id="578df-112">不支援此參數，而且沒有可用的替代功能。</span><span class="sxs-lookup"><span data-stu-id="578df-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="578df-113">分類</span><span class="sxs-lookup"><span data-stu-id="578df-113">Category</span></span>

<span data-ttu-id="578df-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="578df-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="578df-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="578df-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->

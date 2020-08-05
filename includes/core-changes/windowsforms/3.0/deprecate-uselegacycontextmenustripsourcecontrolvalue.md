---
ms.openlocfilehash: df6169289fb96df5f7daf8bd58ccaeebc33ad87c
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556145"
---
### <a name="uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a><span data-ttu-id="f9340-101">不支援 UseLegacyCoNtextMenuStripSourceControlValue 相容性切換</span><span class="sxs-lookup"><span data-stu-id="f9340-101">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>

<span data-ttu-id="f9340-102">`Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue`.Net Core 或 .net 5.0 和更新版本的 Windows Forms 不支援 .NET Framework 4.7.2 中引進的相容性參數。</span><span class="sxs-lookup"><span data-stu-id="f9340-102">The `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch, which was introduced in .NET Framework 4.7.2, is not supported in Windows Forms on .NET Core or .NET 5.0 and later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f9340-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="f9340-103">Change description</span></span>

<span data-ttu-id="f9340-104">從 .NET Framework 4.7.2 開始， `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` 相容性參數可讓開發人員選擇不使用屬性的新行為 <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> ，這現在會傳回原始檔控制的參考。</span><span class="sxs-lookup"><span data-stu-id="f9340-104">Starting with .NET Framework 4.7.2, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch allows the developer to opt out of the new behavior of the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> property, which now returns a reference to the source control.</span></span> <span data-ttu-id="f9340-105">屬性的先前行為是傳回 `null` 。</span><span class="sxs-lookup"><span data-stu-id="f9340-105">The previous behavior of the property was to return `null`.</span></span> <span data-ttu-id="f9340-106">如需詳細資訊，請參閱[ \<AppContextSwitchOverrides> 元素](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)。</span><span class="sxs-lookup"><span data-stu-id="f9340-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="f9340-107">在 .NET Core 和 .NET 5.0 和更新版本中， `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` 不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="f9340-107">In .NET Core and .NET 5.0 and later, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f9340-108">引進的版本</span><span class="sxs-lookup"><span data-stu-id="f9340-108">Version introduced</span></span>

<span data-ttu-id="f9340-109">3.0</span><span class="sxs-lookup"><span data-stu-id="f9340-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f9340-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="f9340-110">Recommended action</span></span>

<span data-ttu-id="f9340-111">移除參數。</span><span class="sxs-lookup"><span data-stu-id="f9340-111">Remove the switch.</span></span> <span data-ttu-id="f9340-112">不支援此參數，而且沒有可用的替代功能。</span><span class="sxs-lookup"><span data-stu-id="f9340-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="f9340-113">類別</span><span class="sxs-lookup"><span data-stu-id="f9340-113">Category</span></span>

<span data-ttu-id="f9340-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f9340-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f9340-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="f9340-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->

---
ms.openlocfilehash: 0be59258df10aa13920551f011d68bc8efe20b93
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888104"
---
### <a name="duplicated-apis-removed-from-windows-forms"></a><span data-ttu-id="10cc5-101">從 Windows 表單中移除的重複 API</span><span class="sxs-lookup"><span data-stu-id="10cc5-101">Duplicated APIs removed from Windows Forms</span></span>

<span data-ttu-id="10cc5-102">在 .NET Core<xref:System.Windows.Forms?displayProperty=fullName>3.0 預覽 4 中啟動的命名空間中意外複製了許多 API,已在 .NET Core 3.0 RC1 中刪除。</span><span class="sxs-lookup"><span data-stu-id="10cc5-102">A number of APIs accidentally duplicated in the <xref:System.Windows.Forms?displayProperty=fullName> namespace starting in .NET Core 3.0 Preview 4 have been removed in .NET Core 3.0 RC1.</span></span>

#### <a name="change-description"></a><span data-ttu-id="10cc5-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="10cc5-103">Change description</span></span>

<span data-ttu-id="10cc5-104">.NET Core 3.0 預覽 4<xref:System.Windows.Forms?displayProperty=fullName><xref:System.ComponentModel.Design?displayProperty=fullName>無意中複製了 命名空間中已經存在的命名空間中的許多類型。</span><span class="sxs-lookup"><span data-stu-id="10cc5-104">.NET Core 3.0 Preview 4 inadvertently duplicated a number of types in the <xref:System.Windows.Forms?displayProperty=fullName> namespace that already existed in the <xref:System.ComponentModel.Design?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="10cc5-105">從 .NET Core 3.0 RC1 開始,這些重複的類型不再可用。</span><span class="sxs-lookup"><span data-stu-id="10cc5-105">Starting with .NET Core 3.0 RC1, these duplicated types are no longer available.</span></span> <span data-ttu-id="10cc5-106">下表列的原始型態與重複型態:</span><span class="sxs-lookup"><span data-stu-id="10cc5-106">The following table shows lists the original type and its duplicated type:</span></span>

> [!div class="mx-tdCol2BreakAll"]
> |<span data-ttu-id="10cc5-107">原始類型</span><span class="sxs-lookup"><span data-stu-id="10cc5-107">Original type</span></span>|<span data-ttu-id="10cc5-108">重複類型</span><span class="sxs-lookup"><span data-stu-id="10cc5-108">Duplicated type</span></span>|
> |---|---|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventArgs?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventArgs`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventHandler?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventHandler`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedType?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedType`|
> |<xref:System.ComponentModel.Design.DesignerActionUIService?displayProperty=fullName>|`System.Windows.Forms.DesignerActionUIService`|
> |<xref:System.ComponentModel.Design.DesignerCommandSet?displayProperty=fullName>|`System.Windows.Forms.DesignerCommandSet`|

#### <a name="version-introduced"></a><span data-ttu-id="10cc5-109">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="10cc5-109">Version introduced</span></span>

<span data-ttu-id="10cc5-110">3.0 RC1</span><span class="sxs-lookup"><span data-stu-id="10cc5-110">3.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="10cc5-111">建議的動作</span><span class="sxs-lookup"><span data-stu-id="10cc5-111">Recommended action</span></span>

<span data-ttu-id="10cc5-112">更新代碼以引用原始類型,如表**的"原始類型**"列所示。</span><span class="sxs-lookup"><span data-stu-id="10cc5-112">Update the code to reference the original type, as shown in the **Original type** column of the table.</span></span>

#### <a name="category"></a><span data-ttu-id="10cc5-113">類別</span><span class="sxs-lookup"><span data-stu-id="10cc5-113">Category</span></span>

<span data-ttu-id="10cc5-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="10cc5-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="10cc5-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="10cc5-115">Affected APIs</span></span>

- <span data-ttu-id="10cc5-116">無。</span><span class="sxs-lookup"><span data-stu-id="10cc5-116">None.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis.

-->

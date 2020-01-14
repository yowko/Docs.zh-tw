---
ms.openlocfilehash: e609b8006846cd202a6a7eeec2529cf1fbb09e7c
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937084"
---
### <a name="duplicated-apis-removed-from-windows-forms"></a><span data-ttu-id="120fa-101">已從 Windows Forms 移除重複的 Api</span><span class="sxs-lookup"><span data-stu-id="120fa-101">Duplicated APIs removed from Windows Forms</span></span>

<span data-ttu-id="120fa-102">從 .NET Core 3.0 Preview 4 開始，在 <xref:System.Windows.Forms?displayProperty=fullName> 命名空間中不小心重複的一些 Api，已在 .NET Core 3.0 RC1 中移除。</span><span class="sxs-lookup"><span data-stu-id="120fa-102">A number of APIs accidentally duplicated in the <xref:System.Windows.Forms?displayProperty=fullName> namespace starting in .NET Core 3.0 Preview 4 have been removed in .NET Core 3.0 RC1.</span></span>

#### <a name="change-description"></a><span data-ttu-id="120fa-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="120fa-103">Change description</span></span>

<span data-ttu-id="120fa-104">.NET Core 3.0 Preview 4 不小心複製 <xref:System.ComponentModel.Design?displayProperty=fullName> 命名空間中已存在的 <xref:System.Windows.Forms?displayProperty=fullName> 命名空間中的數種類型。</span><span class="sxs-lookup"><span data-stu-id="120fa-104">.NET Core 3.0 Preview 4 inadvertently duplicated a number of types in the <xref:System.Windows.Forms?displayProperty=fullName> namespace that already existed in the <xref:System.ComponentModel.Design?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="120fa-105">從 .NET Core 3.0 RC1 開始，這些重複的類型已無法再使用。</span><span class="sxs-lookup"><span data-stu-id="120fa-105">Starting with .NET Core 3.0 RC1, these duplicated types are no longer available.</span></span> <span data-ttu-id="120fa-106">下表顯示原始類型和其重複類型的清單：</span><span class="sxs-lookup"><span data-stu-id="120fa-106">The following table shows lists the original type and its duplicated type:</span></span>

> [!div class="mx-tdCol2BreakAll"]
> |<span data-ttu-id="120fa-107">原始類型</span><span class="sxs-lookup"><span data-stu-id="120fa-107">Original type</span></span>|<span data-ttu-id="120fa-108">重複的類型</span><span class="sxs-lookup"><span data-stu-id="120fa-108">Duplicated type</span></span>|
> |---|---|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventArgs?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventArgs`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventHandler?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventHandler`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedType?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedType`|
> |<xref:System.ComponentModel.Design.DesignerActionUIService?displayProperty=fullName>|`System.Windows.Forms.DesignerActionUIService`|
> |<xref:System.ComponentModel.Design.DesignerCommandSet?displayProperty=fullName>|`System.Windows.Forms.DesignerCommandSet`|

#### <a name="version-introduced"></a><span data-ttu-id="120fa-109">引進的版本</span><span class="sxs-lookup"><span data-stu-id="120fa-109">Version introduced</span></span>

<span data-ttu-id="120fa-110">3.0 RC1</span><span class="sxs-lookup"><span data-stu-id="120fa-110">3.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="120fa-111">建議的動作</span><span class="sxs-lookup"><span data-stu-id="120fa-111">Recommended action</span></span>

<span data-ttu-id="120fa-112">更新程式碼以參考原始類型，如資料表的**原始類型**資料行所示。</span><span class="sxs-lookup"><span data-stu-id="120fa-112">Update the code to reference the original type, as shown in the **Original type** column of the table.</span></span>

#### <a name="category"></a><span data-ttu-id="120fa-113">分類</span><span class="sxs-lookup"><span data-stu-id="120fa-113">Category</span></span>

<span data-ttu-id="120fa-114">Windows 表單</span><span class="sxs-lookup"><span data-stu-id="120fa-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="120fa-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="120fa-115">Affected APIs</span></span>

- <span data-ttu-id="120fa-116">無法透過 API 分析來偵測。</span><span class="sxs-lookup"><span data-stu-id="120fa-116">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis.

-->

---
ms.openlocfilehash: e609b8006846cd202a6a7eeec2529cf1fbb09e7c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937084"
---
### <a name="duplicated-apis-removed-from-windows-forms"></a><span data-ttu-id="73202-101">從 Windows 表單中刪除的重複 API</span><span class="sxs-lookup"><span data-stu-id="73202-101">Duplicated APIs removed from Windows Forms</span></span>

<span data-ttu-id="73202-102">在 .NET Core 3.0<xref:System.Windows.Forms?displayProperty=fullName>預覽 4 中啟動的命名空間中意外複製了許多 API，已在 .NET Core 3.0 RC1 中刪除。</span><span class="sxs-lookup"><span data-stu-id="73202-102">A number of APIs accidentally duplicated in the <xref:System.Windows.Forms?displayProperty=fullName> namespace starting in .NET Core 3.0 Preview 4 have been removed in .NET Core 3.0 RC1.</span></span>

#### <a name="change-description"></a><span data-ttu-id="73202-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="73202-103">Change description</span></span>

<span data-ttu-id="73202-104">.NET Core 3.0 預覽 4 無意中複製了<xref:System.Windows.Forms?displayProperty=fullName><xref:System.ComponentModel.Design?displayProperty=fullName>命名空間中已經存在的命名空間中的許多類型。</span><span class="sxs-lookup"><span data-stu-id="73202-104">.NET Core 3.0 Preview 4 inadvertently duplicated a number of types in the <xref:System.Windows.Forms?displayProperty=fullName> namespace that already existed in the <xref:System.ComponentModel.Design?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="73202-105">從 .NET Core 3.0 RC1 開始，這些重複的類型不再可用。</span><span class="sxs-lookup"><span data-stu-id="73202-105">Starting with .NET Core 3.0 RC1, these duplicated types are no longer available.</span></span> <span data-ttu-id="73202-106">下表列出了原始類型及其重複類型：</span><span class="sxs-lookup"><span data-stu-id="73202-106">The following table shows lists the original type and its duplicated type:</span></span>

> [!div class="mx-tdCol2BreakAll"]
> |<span data-ttu-id="73202-107">原始類型</span><span class="sxs-lookup"><span data-stu-id="73202-107">Original type</span></span>|<span data-ttu-id="73202-108">重複類型</span><span class="sxs-lookup"><span data-stu-id="73202-108">Duplicated type</span></span>|
> |---|---|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventArgs?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventArgs`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventHandler?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventHandler`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedType?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedType`|
> |<xref:System.ComponentModel.Design.DesignerActionUIService?displayProperty=fullName>|`System.Windows.Forms.DesignerActionUIService`|
> |<xref:System.ComponentModel.Design.DesignerCommandSet?displayProperty=fullName>|`System.Windows.Forms.DesignerCommandSet`|

#### <a name="version-introduced"></a><span data-ttu-id="73202-109">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="73202-109">Version introduced</span></span>

<span data-ttu-id="73202-110">3.0 RC1</span><span class="sxs-lookup"><span data-stu-id="73202-110">3.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="73202-111">建議的動作</span><span class="sxs-lookup"><span data-stu-id="73202-111">Recommended action</span></span>

<span data-ttu-id="73202-112">更新代碼以引用原始類型，如表**的"原始類型**"列所示。</span><span class="sxs-lookup"><span data-stu-id="73202-112">Update the code to reference the original type, as shown in the **Original type** column of the table.</span></span>

#### <a name="category"></a><span data-ttu-id="73202-113">類別</span><span class="sxs-lookup"><span data-stu-id="73202-113">Category</span></span>

<span data-ttu-id="73202-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="73202-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="73202-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="73202-115">Affected APIs</span></span>

- <span data-ttu-id="73202-116">無法通過 API 分析檢測。</span><span class="sxs-lookup"><span data-stu-id="73202-116">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis.

-->

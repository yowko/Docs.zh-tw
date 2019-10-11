---
ms.openlocfilehash: 75ba041a93b71377928591967e1554742e1d17e1
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237311"
---
### <a name="types-in-microsoftvisualbasicmyservices-namespace-not-available"></a><span data-ttu-id="9eaf3-101">MyServices 命名空間中的類型無法使用</span><span class="sxs-lookup"><span data-stu-id="9eaf3-101">Types in Microsoft.VisualBasic.MyServices namespace not available</span></span>

<span data-ttu-id="9eaf3-102">@No__t 0 命名空間中的類型無法使用。</span><span class="sxs-lookup"><span data-stu-id="9eaf3-102">The types in the <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace are not available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9eaf3-103">引進的版本</span><span class="sxs-lookup"><span data-stu-id="9eaf3-103">Version introduced</span></span>

<span data-ttu-id="9eaf3-104">.NET Core 3.0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="9eaf3-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="9eaf3-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="9eaf3-105">Change description</span></span>

<span data-ttu-id="9eaf3-106">在某些 .NET Core 3.0 Preview 版本中，可以使用 <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> 命名空間中的類型。</span><span class="sxs-lookup"><span data-stu-id="9eaf3-106">The types in the <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace were available in some .NET Core 3.0 Preview releases.</span></span> <span data-ttu-id="9eaf3-107">從 .NET Core 3.0 Preview 9 開始就不再提供這些功能。</span><span class="sxs-lookup"><span data-stu-id="9eaf3-107">They are no longer available starting with .NET Core 3.0 Preview 9.</span></span>

<span data-ttu-id="9eaf3-108">已移除類型，以避免不必要的元件相依性或後續版本中的重大變更。</span><span class="sxs-lookup"><span data-stu-id="9eaf3-108">The types were removed to avoid unnecessary assembly dependencies or breaking changes in subsequent releases.</span></span>
 
#### <a name="recommended-action"></a><span data-ttu-id="9eaf3-109">建議的動作</span><span class="sxs-lookup"><span data-stu-id="9eaf3-109">Recommended action</span></span>

<span data-ttu-id="9eaf3-110">如果您的程式碼相依于**MyServices**類型及其成員，則 .net 類別庫中會有對應的類型和成員。</span><span class="sxs-lookup"><span data-stu-id="9eaf3-110">If your code depends on the use of **Microsoft.VisualBasic.MyServices** types and their members, there are corresponding types and members in the .NET class library.</span></span> <span data-ttu-id="9eaf3-111">以下是**MyServices**類型對應到其對等 .net 類別庫類型的對應：</span><span class="sxs-lookup"><span data-stu-id="9eaf3-111">The following is a mapping of  **Microsoft.VisualBasic.MyServices** types to their equivalent .NET class library types:</span></span>

|<span data-ttu-id="9eaf3-112">MyServices 類型</span><span class="sxs-lookup"><span data-stu-id="9eaf3-112">Microsoft.VisualBasic.MyServices type</span></span>|<span data-ttu-id="9eaf3-113">.NET 類別庫類型</span><span class="sxs-lookup"><span data-stu-id="9eaf3-113">.NET class library type</span></span>|
|--|--|
|<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>|<span data-ttu-id="9eaf3-114">適用于 WPF 應用程式的 <xref:System.Windows.Clipboard?displayProperty=nameWithType>，適用于 Windows Forms 應用程式 <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9eaf3-114"><xref:System.Windows.Clipboard?displayProperty=nameWithType> for WPF applications, <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> for Windows Forms applications</span></span>| 
|<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy>|<span data-ttu-id="9eaf3-115">@No__t-0 命名空間中的類型</span><span class="sxs-lookup"><span data-stu-id="9eaf3-115">Types in the <xref:System.IO> namespace</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>|<span data-ttu-id="9eaf3-116">@No__t-0 命名空間中的登錄相關類型</span><span class="sxs-lookup"><span data-stu-id="9eaf3-116">Registry-related types in the <xref:Microsoft.Win32> namespace</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy>|<xref:System.Environment.GetFolderPath%2A?displayProperty=nameWithType>|

#### <a name="category"></a><span data-ttu-id="9eaf3-117">Category</span><span class="sxs-lookup"><span data-stu-id="9eaf3-117">Category</span></span>

<span data-ttu-id="9eaf3-118">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9eaf3-118">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9eaf3-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="9eaf3-119">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.MyServices`

-- >


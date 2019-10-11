---
ms.openlocfilehash: 294c077b837899bd714deb2afd1bdff2b3185f38
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237306"
---
### <a name="types-in-microsoftvisualbasicapplicationservices-namespace-not-available"></a><span data-ttu-id="b1426-101">Microsoft.visualbasic.applicationservices.cantstartsingleinstanceexception 命名空間中的類型無法使用</span><span class="sxs-lookup"><span data-stu-id="b1426-101">Types in Microsoft.VisualBasic.ApplicationServices namespace not available</span></span>

<span data-ttu-id="b1426-102">@No__t 0 命名空間中的類型無法使用。</span><span class="sxs-lookup"><span data-stu-id="b1426-102">The types in the <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName> namespace are not available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b1426-103">引進的版本</span><span class="sxs-lookup"><span data-stu-id="b1426-103">Version introduced</span></span>

<span data-ttu-id="b1426-104">.NET Core 3.0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="b1426-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="b1426-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="b1426-105">Change description</span></span>

<span data-ttu-id="b1426-106">在某些 .NET Core 3.0 Preview 版本中，可以使用 <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName> 命名空間中的類型。</span><span class="sxs-lookup"><span data-stu-id="b1426-106">The types in the <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName> namespace were available in some .NET Core 3.0 Preview releases.</span></span> <span data-ttu-id="b1426-107">從 .NET Core 3.0 Preview 9 開始就不再提供這些功能。</span><span class="sxs-lookup"><span data-stu-id="b1426-107">They are no longer available starting with .NET Core 3.0 Preview 9.</span></span>

<span data-ttu-id="b1426-108">已移除類型，以避免不必要的元件相依性或後續版本中的重大變更。</span><span class="sxs-lookup"><span data-stu-id="b1426-108">The types were removed to avoid unnecessary assembly dependencies or breaking changes in subsequent releases.</span></span>
 
#### <a name="recommended-action"></a><span data-ttu-id="b1426-109">建議的動作</span><span class="sxs-lookup"><span data-stu-id="b1426-109">Recommended action</span></span>

<span data-ttu-id="b1426-110">如果您的程式碼相依于使用 @no__t 0 型別及其成員，您可以在 .NET 類別庫中使用對應的型別或成員。</span><span class="sxs-lookup"><span data-stu-id="b1426-110">If your code depends on the use of <xref:Microsoft.VisualBasic.ApplicationServices> types and their members, you may be able to use a corresponding type or member in the .NET class library.</span></span> <span data-ttu-id="b1426-111">例如，某些 <xref:System.Environment?displayProperty=nameWithType> 和 @no__t 1 成員對 @no__t 2 類別的屬性提供對等的功能。</span><span class="sxs-lookup"><span data-stu-id="b1426-111">For example, some <xref:System.Environment?displayProperty=nameWithType> and <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType> members provide equivalent functionality to the properties of the <xref:Microsoft.VisualBasic.ApplicationServices.User?displayProperty=nameWithType> class.</span></span>

#### <a name="category"></a><span data-ttu-id="b1426-112">Category</span><span class="sxs-lookup"><span data-stu-id="b1426-112">Category</span></span>

<span data-ttu-id="b1426-113">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b1426-113">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b1426-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="b1426-114">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.ApplicationServices`

-- >


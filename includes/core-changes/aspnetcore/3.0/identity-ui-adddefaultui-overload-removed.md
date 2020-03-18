---
ms.openlocfilehash: 806722ea9aec1c828786525e3155b7f624159ac1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522691"
---
### <a name="identity-adddefaultui-method-overload-removed"></a><span data-ttu-id="dd1bf-101">標識：刪除添加 DefaultUI 方法重載</span><span class="sxs-lookup"><span data-stu-id="dd1bf-101">Identity: AddDefaultUI method overload removed</span></span>

<span data-ttu-id="dd1bf-102">從 ASP.NET Core 3.0<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType>開始，該方法重載不再存在。</span><span class="sxs-lookup"><span data-stu-id="dd1bf-102">Starting with ASP.NET Core 3.0, the <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType> method overload no longer exists.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="dd1bf-103">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="dd1bf-103">Version introduced</span></span>

<span data-ttu-id="dd1bf-104">3.0</span><span class="sxs-lookup"><span data-stu-id="dd1bf-104">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="dd1bf-105">更改原因</span><span class="sxs-lookup"><span data-stu-id="dd1bf-105">Reason for change</span></span>

<span data-ttu-id="dd1bf-106">此更改是採用靜態 Web 資產功能的結果。</span><span class="sxs-lookup"><span data-stu-id="dd1bf-106">This change was a result of adoption of the static web assets feature.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="dd1bf-107">建議的動作</span><span class="sxs-lookup"><span data-stu-id="dd1bf-107">Recommended action</span></span>

<span data-ttu-id="dd1bf-108">調用<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType>而不是重載。</span><span class="sxs-lookup"><span data-stu-id="dd1bf-108">Call <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> instead of the overload.</span></span> <span data-ttu-id="dd1bf-109">如果使用 Bootstrap 3，請向專案檔案中`<PropertyGroup>`的元素添加以下行：</span><span class="sxs-lookup"><span data-stu-id="dd1bf-109">If you're using Bootstrap 3, also add the following line to a `<PropertyGroup>` element in your project file:</span></span>

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a><span data-ttu-id="dd1bf-110">類別</span><span class="sxs-lookup"><span data-stu-id="dd1bf-110">Category</span></span>

<span data-ttu-id="dd1bf-111">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="dd1bf-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="dd1bf-112">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="dd1bf-112">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->

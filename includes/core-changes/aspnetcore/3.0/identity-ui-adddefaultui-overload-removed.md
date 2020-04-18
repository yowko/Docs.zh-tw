---
ms.openlocfilehash: 474f039cf00cb48761bfe7b7c4a0a9c6300cd820
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2020
ms.locfileid: "81637193"
---
### <a name="identity-adddefaultui-method-overload-removed"></a><span data-ttu-id="bb941-101">識別:移除新增 DefaultUI 方法重載</span><span class="sxs-lookup"><span data-stu-id="bb941-101">Identity: AddDefaultUI method overload removed</span></span>

<span data-ttu-id="bb941-102">從ASP.NET核心3.0開始,[標識產生器UI擴展.AddDefaultUI(身份生成器、UIFramework)](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.identity.identitybuilderuiextensions.adddefaultui?view=aspnetcore-2.2#Microsoft_AspNetCore_Identity_IdentityBuilderUIExtensions_AddDefaultUI_Microsoft_AspNetCore_Identity_IdentityBuilder_Microsoft_AspNetCore_Identity_UI_UIFramework_)方法重載不再存在。</span><span class="sxs-lookup"><span data-stu-id="bb941-102">Starting with ASP.NET Core 3.0, the [IdentityBuilderUIExtensions.AddDefaultUI(IdentityBuilder,UIFramework)](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.identity.identitybuilderuiextensions.adddefaultui?view=aspnetcore-2.2#Microsoft_AspNetCore_Identity_IdentityBuilderUIExtensions_AddDefaultUI_Microsoft_AspNetCore_Identity_IdentityBuilder_Microsoft_AspNetCore_Identity_UI_UIFramework_) method overload no longer exists.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="bb941-103">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="bb941-103">Version introduced</span></span>

<span data-ttu-id="bb941-104">3.0</span><span class="sxs-lookup"><span data-stu-id="bb941-104">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="bb941-105">變更原因</span><span class="sxs-lookup"><span data-stu-id="bb941-105">Reason for change</span></span>

<span data-ttu-id="bb941-106">此更改是採用靜態 Web 資產功能的結果。</span><span class="sxs-lookup"><span data-stu-id="bb941-106">This change was a result of adoption of the static web assets feature.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="bb941-107">建議的動作</span><span class="sxs-lookup"><span data-stu-id="bb941-107">Recommended action</span></span>

<span data-ttu-id="bb941-108">調用<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType>而不是需要兩個參數的重載。</span><span class="sxs-lookup"><span data-stu-id="bb941-108">Call <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> instead of the overload that takes two arguments.</span></span> <span data-ttu-id="bb941-109">如果使用 Bootstrap 3,請向專案`<PropertyGroup>`檔中 的元素新增以下行:</span><span class="sxs-lookup"><span data-stu-id="bb941-109">If you're using Bootstrap 3, also add the following line to a `<PropertyGroup>` element in your project file:</span></span>

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a><span data-ttu-id="bb941-110">類別</span><span class="sxs-lookup"><span data-stu-id="bb941-110">Category</span></span>

<span data-ttu-id="bb941-111">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="bb941-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="bb941-112">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="bb941-112">Affected APIs</span></span>

[<span data-ttu-id="bb941-113">識別產生器 UI 延伸.新增預設 UI(識別產生器,UIFramework)</span><span class="sxs-lookup"><span data-stu-id="bb941-113">IdentityBuilderUIExtensions.AddDefaultUI(IdentityBuilder,UIFramework)</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.identity.identitybuilderuiextensions.adddefaultui?view=aspnetcore-2.2#Microsoft_AspNetCore_Identity_IdentityBuilderUIExtensions_AddDefaultUI_Microsoft_AspNetCore_Identity_IdentityBuilder_Microsoft_AspNetCore_Identity_UI_UIFramework_)

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->

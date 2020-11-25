---
ms.openlocfilehash: e77312605ee367c159171e305d8f69429f9ac58b
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032369"
---
### <a name="identity-adddefaultui-method-overload-removed"></a><span data-ttu-id="908ed-101">Identity： AddDefaultUI 方法多載已移除</span><span class="sxs-lookup"><span data-stu-id="908ed-101">Identity: AddDefaultUI method overload removed</span></span>

<span data-ttu-id="908ed-102">從 ASP.NET Core 3.0 開始， [IdentityBuilderUIExtensions. AddDefaultUI (IdentityBuilder、UIFramework) ](/dotnet/api/microsoft.aspnetcore.identity.identitybuilderuiextensions.adddefaultui?view=aspnetcore-2.2#Microsoft_AspNetCore_Identity_IdentityBuilderUIExtensions_AddDefaultUI_Microsoft_AspNetCore_Identity_IdentityBuilder_Microsoft_AspNetCore_Identity_UI_UIFramework_) 方法多載已不存在。</span><span class="sxs-lookup"><span data-stu-id="908ed-102">Starting with ASP.NET Core 3.0, the [IdentityBuilderUIExtensions.AddDefaultUI(IdentityBuilder,UIFramework)](/dotnet/api/microsoft.aspnetcore.identity.identitybuilderuiextensions.adddefaultui?view=aspnetcore-2.2#Microsoft_AspNetCore_Identity_IdentityBuilderUIExtensions_AddDefaultUI_Microsoft_AspNetCore_Identity_IdentityBuilder_Microsoft_AspNetCore_Identity_UI_UIFramework_) method overload no longer exists.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="908ed-103">引進的版本</span><span class="sxs-lookup"><span data-stu-id="908ed-103">Version introduced</span></span>

<span data-ttu-id="908ed-104">3.0</span><span class="sxs-lookup"><span data-stu-id="908ed-104">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="908ed-105">變更的原因</span><span class="sxs-lookup"><span data-stu-id="908ed-105">Reason for change</span></span>

<span data-ttu-id="908ed-106">這項變更是採用靜態 web 資產功能的結果。</span><span class="sxs-lookup"><span data-stu-id="908ed-106">This change was a result of adoption of the static web assets feature.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="908ed-107">建議的動作</span><span class="sxs-lookup"><span data-stu-id="908ed-107">Recommended action</span></span>

<span data-ttu-id="908ed-108">呼叫 <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> ，而不是採用兩個引數的多載。</span><span class="sxs-lookup"><span data-stu-id="908ed-108">Call <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> instead of the overload that takes two arguments.</span></span> <span data-ttu-id="908ed-109">如果您使用的是啟動程式3，也請將下列這一行新增至 `<PropertyGroup>` 專案檔中的元素：</span><span class="sxs-lookup"><span data-stu-id="908ed-109">If you're using Bootstrap 3, also add the following line to a `<PropertyGroup>` element in your project file:</span></span>

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a><span data-ttu-id="908ed-110">類別</span><span class="sxs-lookup"><span data-stu-id="908ed-110">Category</span></span>

<span data-ttu-id="908ed-111">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="908ed-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="908ed-112">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="908ed-112">Affected APIs</span></span>

[<span data-ttu-id="908ed-113">IdentityBuilderUIExtensions. AddDefaultUI (IdentityBuilder，UIFramework) </span><span class="sxs-lookup"><span data-stu-id="908ed-113">IdentityBuilderUIExtensions.AddDefaultUI(IdentityBuilder,UIFramework)</span></span>](/dotnet/api/microsoft.aspnetcore.identity.identitybuilderuiextensions.adddefaultui?view=aspnetcore-2.2#Microsoft_AspNetCore_Identity_IdentityBuilderUIExtensions_AddDefaultUI_Microsoft_AspNetCore_Identity_IdentityBuilder_Microsoft_AspNetCore_Identity_UI_UIFramework_)

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->

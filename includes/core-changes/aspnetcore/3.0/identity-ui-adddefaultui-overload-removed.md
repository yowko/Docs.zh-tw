---
ms.openlocfilehash: 806722ea9aec1c828786525e3155b7f624159ac1
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522691"
---
### <a name="identity-adddefaultui-method-overload-removed"></a><span data-ttu-id="e1376-101">識別： AddDefaultUI 方法多載已移除</span><span class="sxs-lookup"><span data-stu-id="e1376-101">Identity: AddDefaultUI method overload removed</span></span>

<span data-ttu-id="e1376-102">從 ASP.NET Core 3.0 開始，<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType> 方法多載已不存在。</span><span class="sxs-lookup"><span data-stu-id="e1376-102">Starting with ASP.NET Core 3.0, the <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType> method overload no longer exists.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e1376-103">引進的版本</span><span class="sxs-lookup"><span data-stu-id="e1376-103">Version introduced</span></span>

<span data-ttu-id="e1376-104">3.0</span><span class="sxs-lookup"><span data-stu-id="e1376-104">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e1376-105">變更的原因</span><span class="sxs-lookup"><span data-stu-id="e1376-105">Reason for change</span></span>

<span data-ttu-id="e1376-106">這項變更是採用靜態 web 資產功能的結果。</span><span class="sxs-lookup"><span data-stu-id="e1376-106">This change was a result of adoption of the static web assets feature.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e1376-107">建議的動作</span><span class="sxs-lookup"><span data-stu-id="e1376-107">Recommended action</span></span>

<span data-ttu-id="e1376-108">呼叫 <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType>，而不是多載。</span><span class="sxs-lookup"><span data-stu-id="e1376-108">Call <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> instead of the overload.</span></span> <span data-ttu-id="e1376-109">如果您使用的是啟動程式3，也請將下行新增至專案檔中的 `<PropertyGroup>` 元素：</span><span class="sxs-lookup"><span data-stu-id="e1376-109">If you're using Bootstrap 3, also add the following line to a `<PropertyGroup>` element in your project file:</span></span>

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a><span data-ttu-id="e1376-110">Category</span><span class="sxs-lookup"><span data-stu-id="e1376-110">Category</span></span>

<span data-ttu-id="e1376-111">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e1376-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e1376-112">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="e1376-112">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->

---
ms.openlocfilehash: c5e4b5619394f99a419fe48aee190ad741ea8c0d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "73041655"
---
### <a name="identity-ui-uses-static-web-assets-feature"></a><span data-ttu-id="4db28-101">標識：UI 使用靜態 Web 資產功能</span><span class="sxs-lookup"><span data-stu-id="4db28-101">Identity: UI uses static web assets feature</span></span>

<span data-ttu-id="4db28-102">ASP.NET Core 3.0 引入了靜態 Web 資產功能，而標識 UI 已採用此功能。</span><span class="sxs-lookup"><span data-stu-id="4db28-102">ASP.NET Core 3.0 introduced a static web assets feature, and Identity UI has adopted it.</span></span>

#### <a name="change-description"></a><span data-ttu-id="4db28-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="4db28-103">Change description</span></span>

<span data-ttu-id="4db28-104">由於標識 UI 採用了靜態 Web 資產功能：</span><span class="sxs-lookup"><span data-stu-id="4db28-104">As a result of Identity UI adopting the static web assets feature:</span></span>

- <span data-ttu-id="4db28-105">框架選擇通過使用專案檔案中的屬性`IdentityUIFrameworkVersion`來完成。</span><span class="sxs-lookup"><span data-stu-id="4db28-105">Framework selection is accomplished by using the `IdentityUIFrameworkVersion` property in your project file.</span></span>
- <span data-ttu-id="4db28-106">引導 4 是標識 UI 的預設 UI 框架。</span><span class="sxs-lookup"><span data-stu-id="4db28-106">Bootstrap 4 is the default UI framework for Identity UI.</span></span> <span data-ttu-id="4db28-107">引導 3 已達到生命週期結束，應考慮遷移到受支援的版本。</span><span class="sxs-lookup"><span data-stu-id="4db28-107">Bootstrap 3 has reached end of life, and you should consider migrating to a supported version.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4db28-108">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="4db28-108">Version introduced</span></span>

<span data-ttu-id="4db28-109">3.0</span><span class="sxs-lookup"><span data-stu-id="4db28-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="4db28-110">舊的行為</span><span class="sxs-lookup"><span data-stu-id="4db28-110">Old behavior</span></span>

<span data-ttu-id="4db28-111">標識 UI 的預設 UI 框架為**引導 3**。</span><span class="sxs-lookup"><span data-stu-id="4db28-111">The default UI framework for Identity UI was **Bootstrap 3**.</span></span> <span data-ttu-id="4db28-112">可以使用 參數對 中的`AddDefaultUI``Startup.ConfigureServices`方法調用配置 UI 框架。</span><span class="sxs-lookup"><span data-stu-id="4db28-112">The UI framework could be configured using a parameter to the `AddDefaultUI` method call in `Startup.ConfigureServices`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="4db28-113">新的行為</span><span class="sxs-lookup"><span data-stu-id="4db28-113">New behavior</span></span>

<span data-ttu-id="4db28-114">標識 UI 的預設 UI 框架是**引導 4**。</span><span class="sxs-lookup"><span data-stu-id="4db28-114">The default UI framework for Identity UI is **Bootstrap 4**.</span></span> <span data-ttu-id="4db28-115">必須在專案檔案中而不是`AddDefaultUI`方法調用中配置 UI 框架。</span><span class="sxs-lookup"><span data-stu-id="4db28-115">The UI framework must be configured in your project file, instead of in the `AddDefaultUI` method call.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="4db28-116">更改原因</span><span class="sxs-lookup"><span data-stu-id="4db28-116">Reason for change</span></span>

<span data-ttu-id="4db28-117">採用靜態 Web 資產功能要求 UI 框架配置遷移到 MSBuild。</span><span class="sxs-lookup"><span data-stu-id="4db28-117">Adoption of the static web assets feature required that the UI framework configuration move to MSBuild.</span></span> <span data-ttu-id="4db28-118">要嵌入哪個框架的決定是生成時間決策，而不是運行時決策。</span><span class="sxs-lookup"><span data-stu-id="4db28-118">The decision on which framework to embed is a build-time decision, not a runtime decision.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4db28-119">建議的動作</span><span class="sxs-lookup"><span data-stu-id="4db28-119">Recommended action</span></span>

<span data-ttu-id="4db28-120">查看網站 UI 以確保新的 Bootstrap 4 元件相容。</span><span class="sxs-lookup"><span data-stu-id="4db28-120">Review your site UI to ensure the new Bootstrap 4 components are compatible.</span></span> <span data-ttu-id="4db28-121">如有必要，`IdentityUIFrameworkVersion`請使用 MSBuild 屬性還原到引導 3。</span><span class="sxs-lookup"><span data-stu-id="4db28-121">If necessary, use the `IdentityUIFrameworkVersion` MSBuild property to revert to Bootstrap 3.</span></span> <span data-ttu-id="4db28-122">將屬性添加到專案檔案中`<PropertyGroup>`的元素：</span><span class="sxs-lookup"><span data-stu-id="4db28-122">Add the property to a `<PropertyGroup>` element in your project file:</span></span>

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a><span data-ttu-id="4db28-123">類別</span><span class="sxs-lookup"><span data-stu-id="4db28-123">Category</span></span>

<span data-ttu-id="4db28-124">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4db28-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4db28-125">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="4db28-125">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->

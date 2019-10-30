---
ms.openlocfilehash: c5e4b5619394f99a419fe48aee190ad741ea8c0d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2019
ms.locfileid: "73041655"
---
### <a name="identity-ui-uses-static-web-assets-feature"></a><span data-ttu-id="b425d-101">身分識別： UI 使用靜態 web 資產功能</span><span class="sxs-lookup"><span data-stu-id="b425d-101">Identity: UI uses static web assets feature</span></span>

<span data-ttu-id="b425d-102">ASP.NET Core 3.0 引進了靜態 web 資產功能，且身分識別 UI 已採用它。</span><span class="sxs-lookup"><span data-stu-id="b425d-102">ASP.NET Core 3.0 introduced a static web assets feature, and Identity UI has adopted it.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b425d-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="b425d-103">Change description</span></span>

<span data-ttu-id="b425d-104">由於身分識別使用者介面採用靜態 web 資產功能：</span><span class="sxs-lookup"><span data-stu-id="b425d-104">As a result of Identity UI adopting the static web assets feature:</span></span>

- <span data-ttu-id="b425d-105">您可以使用專案檔中的 `IdentityUIFrameworkVersion` 屬性來完成架構選擇。</span><span class="sxs-lookup"><span data-stu-id="b425d-105">Framework selection is accomplished by using the `IdentityUIFrameworkVersion` property in your project file.</span></span>
- <span data-ttu-id="b425d-106">啟動程式4是身分識別 UI 的預設 UI 架構。</span><span class="sxs-lookup"><span data-stu-id="b425d-106">Bootstrap 4 is the default UI framework for Identity UI.</span></span> <span data-ttu-id="b425d-107">啟動程式3已達到生命週期的結尾，您應該考慮遷移至支援的版本。</span><span class="sxs-lookup"><span data-stu-id="b425d-107">Bootstrap 3 has reached end of life, and you should consider migrating to a supported version.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b425d-108">引進的版本</span><span class="sxs-lookup"><span data-stu-id="b425d-108">Version introduced</span></span>

<span data-ttu-id="b425d-109">3.0</span><span class="sxs-lookup"><span data-stu-id="b425d-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="b425d-110">舊的行為</span><span class="sxs-lookup"><span data-stu-id="b425d-110">Old behavior</span></span>

<span data-ttu-id="b425d-111">身分識別 UI 的預設 UI 架構是**啟動程式 3**。</span><span class="sxs-lookup"><span data-stu-id="b425d-111">The default UI framework for Identity UI was **Bootstrap 3**.</span></span> <span data-ttu-id="b425d-112">您可以使用 `Startup.ConfigureServices`中 `AddDefaultUI` 方法呼叫的參數來設定 UI 架構。</span><span class="sxs-lookup"><span data-stu-id="b425d-112">The UI framework could be configured using a parameter to the `AddDefaultUI` method call in `Startup.ConfigureServices`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="b425d-113">新的行為</span><span class="sxs-lookup"><span data-stu-id="b425d-113">New behavior</span></span>

<span data-ttu-id="b425d-114">身分識別 UI 的預設 UI 架構是**啟動程式 4**。</span><span class="sxs-lookup"><span data-stu-id="b425d-114">The default UI framework for Identity UI is **Bootstrap 4**.</span></span> <span data-ttu-id="b425d-115">UI 架構必須在專案檔中設定，而不是在 `AddDefaultUI` 方法呼叫中。</span><span class="sxs-lookup"><span data-stu-id="b425d-115">The UI framework must be configured in your project file, instead of in the `AddDefaultUI` method call.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b425d-116">變更的原因</span><span class="sxs-lookup"><span data-stu-id="b425d-116">Reason for change</span></span>

<span data-ttu-id="b425d-117">採用靜態 web 資產功能時，UI 架構設定必須移至 MSBuild。</span><span class="sxs-lookup"><span data-stu-id="b425d-117">Adoption of the static web assets feature required that the UI framework configuration move to MSBuild.</span></span> <span data-ttu-id="b425d-118">決定要內嵌的架構是組建時間決策，而不是執行時間決策。</span><span class="sxs-lookup"><span data-stu-id="b425d-118">The decision on which framework to embed is a build-time decision, not a runtime decision.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b425d-119">建議的動作</span><span class="sxs-lookup"><span data-stu-id="b425d-119">Recommended action</span></span>

<span data-ttu-id="b425d-120">請檢查您的網站 UI，以確保新的啟動程式4元件相容。</span><span class="sxs-lookup"><span data-stu-id="b425d-120">Review your site UI to ensure the new Bootstrap 4 components are compatible.</span></span> <span data-ttu-id="b425d-121">如有必要，請使用 `IdentityUIFrameworkVersion` MSBuild 屬性來還原為啟動程式3。</span><span class="sxs-lookup"><span data-stu-id="b425d-121">If necessary, use the `IdentityUIFrameworkVersion` MSBuild property to revert to Bootstrap 3.</span></span> <span data-ttu-id="b425d-122">將屬性新增至專案檔中的 `<PropertyGroup>` 元素：</span><span class="sxs-lookup"><span data-stu-id="b425d-122">Add the property to a `<PropertyGroup>` element in your project file:</span></span>

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a><span data-ttu-id="b425d-123">Category</span><span class="sxs-lookup"><span data-stu-id="b425d-123">Category</span></span>

<span data-ttu-id="b425d-124">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b425d-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b425d-125">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="b425d-125">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->

---
ms.openlocfilehash: edff55d540f08e8a9fd4d0687aaf6bd963ee3a84
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539454"
---
### <a name="blazor-rendertreeframe-readonly-public-fields-have-become-properties"></a><span data-ttu-id="69596-101">Blazor： RenderTreeFrame readonly public fields 已成為屬性</span><span class="sxs-lookup"><span data-stu-id="69596-101">Blazor: RenderTreeFrame readonly public fields have become properties</span></span>

<span data-ttu-id="69596-102">在 ASP.NET Core 3.0 和3.1 中， <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame> 結構會公開各種 `readonly public` 欄位，包括 <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.FrameType> 、 <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.Sequence> 和其他欄位。</span><span class="sxs-lookup"><span data-stu-id="69596-102">In ASP.NET Core 3.0 and 3.1, the <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame> struct exposed various `readonly public` fields, including <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.FrameType>, <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.Sequence>, and others.</span></span> <span data-ttu-id="69596-103">在 ASP.NET Core 5.0 RC1 和更新版本中，所有的 `readonly public` 欄位都會變更為 `readonly public` 屬性。</span><span class="sxs-lookup"><span data-stu-id="69596-103">In ASP.NET Core 5.0 RC1 and later versions, all the `readonly public` fields changed to `readonly public` properties.</span></span>

<span data-ttu-id="69596-104">這種變更不會影響許多開發人員，因為：</span><span class="sxs-lookup"><span data-stu-id="69596-104">This change won't affect many developers because:</span></span>

* <span data-ttu-id="69596-105">只要使用檔案 `.razor` (或甚至是手動呼叫) 來定義其元件的任何應用程式或程式庫，都 <xref:Microsoft.AspNetCore.Components.Rendering.RenderTreeBuilder> 不會直接參考此類型。</span><span class="sxs-lookup"><span data-stu-id="69596-105">Any app or library that simply uses `.razor` files (or even manual <xref:Microsoft.AspNetCore.Components.Rendering.RenderTreeBuilder> calls) to define its components wouldn't be referencing this type directly.</span></span>
* <span data-ttu-id="69596-106">`RenderTreeFrame`型別本身被視為是一種執行的詳細資料，而不是用於架構之外。</span><span class="sxs-lookup"><span data-stu-id="69596-106">The `RenderTreeFrame` type itself is regarded as an implementation detail, not intended for use outside of the framework.</span></span> <span data-ttu-id="69596-107">如果直接使用型別，ASP.NET Core 3.0 和更新版本包含的分析器會發出編譯器警告。</span><span class="sxs-lookup"><span data-stu-id="69596-107">ASP.NET Core 3.0 and later includes an analyzer that issues compiler warnings if the type is being used directly.</span></span>
* <span data-ttu-id="69596-108">即使您直接參考 `RenderTreeFrame` ，這項變更仍是二進位檔，但不會中斷來源。</span><span class="sxs-lookup"><span data-stu-id="69596-108">Even if you reference `RenderTreeFrame` directly, this change is binary-breaking but not source-breaking.</span></span> <span data-ttu-id="69596-109">也就是說，您現有的原始程式碼會編譯並正常運作。</span><span class="sxs-lookup"><span data-stu-id="69596-109">That is, your existing source code will compile and behave properly.</span></span> <span data-ttu-id="69596-110">您只會在針對 .NET Core 3.x framework 進行編譯，然後針對 .NET 5.0 RC1 和更新版本的架構執行這些二進位檔時，才會遇到問題。</span><span class="sxs-lookup"><span data-stu-id="69596-110">You'll only encounter an issue if compiling against a .NET Core 3.x framework and then running those binaries against the .NET 5.0 RC1 and later framework.</span></span>

<span data-ttu-id="69596-111">如需相關討論，請參閱 GitHub issue [dotnet/aspnetcore # 25727](https://github.com/dotnet/aspnetcore/issues/25727)。</span><span class="sxs-lookup"><span data-stu-id="69596-111">For discussion, see GitHub issue [dotnet/aspnetcore#25727](https://github.com/dotnet/aspnetcore/issues/25727).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="69596-112">引進的版本</span><span class="sxs-lookup"><span data-stu-id="69596-112">Version introduced</span></span>

<span data-ttu-id="69596-113">5.0 RC1</span><span class="sxs-lookup"><span data-stu-id="69596-113">5.0 RC1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="69596-114">舊的行為</span><span class="sxs-lookup"><span data-stu-id="69596-114">Old behavior</span></span>

<span data-ttu-id="69596-115">上的 Public 成員 `RenderTreeFrame` 定義為欄位。</span><span class="sxs-lookup"><span data-stu-id="69596-115">Public members on `RenderTreeFrame` are defined as fields.</span></span> <span data-ttu-id="69596-116">例如，`renderTreeFrame.Sequence` 與 `renderTreeFrame.ElementName`。</span><span class="sxs-lookup"><span data-stu-id="69596-116">For example, `renderTreeFrame.Sequence` and `renderTreeFrame.ElementName`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="69596-117">新的行為</span><span class="sxs-lookup"><span data-stu-id="69596-117">New behavior</span></span>

<span data-ttu-id="69596-118">上的 Public 成員 `RenderTreeFrame` 定義為與之前相同名稱的屬性。</span><span class="sxs-lookup"><span data-stu-id="69596-118">Public members on `RenderTreeFrame` are defined as properties with the same names as before.</span></span> <span data-ttu-id="69596-119">例如，`renderTreeFrame.Sequence` 與 `renderTreeFrame.ElementName`。</span><span class="sxs-lookup"><span data-stu-id="69596-119">For example, `renderTreeFrame.Sequence` and `renderTreeFrame.ElementName`.</span></span>

<span data-ttu-id="69596-120">如果在此變更之後，舊的先行編譯器代碼尚未重新編譯，可能會擲回類似 *system.missingfieldexception：找不到欄位： ' RenderTree. RenderTreeFrame. FrameType '* 的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="69596-120">If older precompiled code hasn't been recompiled since this change, it may throw an exception similar to *MissingFieldException: Field not found: 'Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.FrameType'*.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="69596-121">變更的原因</span><span class="sxs-lookup"><span data-stu-id="69596-121">Reason for change</span></span>

<span data-ttu-id="69596-122">需要進行這項變更，才能在 ASP.NET Core 5.0 的 Blazor 元件轉譯中執行高影響力效能改進。</span><span class="sxs-lookup"><span data-stu-id="69596-122">This change was necessary to implement high-impact performance improvements in Blazor component rendering in ASP.NET Core 5.0.</span></span> <span data-ttu-id="69596-123">系統會維護相同等級的安全性和封裝。</span><span class="sxs-lookup"><span data-stu-id="69596-123">The same levels of safety and encapsulation are maintained.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="69596-124">建議的動作</span><span class="sxs-lookup"><span data-stu-id="69596-124">Recommended action</span></span>

<span data-ttu-id="69596-125">大部分的 Blazor 開發人員都不會受到這項變更的影響。</span><span class="sxs-lookup"><span data-stu-id="69596-125">Most Blazor developers are unaffected by this change.</span></span> <span data-ttu-id="69596-126">變更可能會影響媒體櫃和套件作者，但只有在罕見的情況下才會影響。</span><span class="sxs-lookup"><span data-stu-id="69596-126">The change is more likely to affect library and package authors, but only in rare cases.</span></span> <span data-ttu-id="69596-127">具體而言，如果您要開發：</span><span class="sxs-lookup"><span data-stu-id="69596-127">Specifically, if you're developing:</span></span>

* <span data-ttu-id="69596-128">應用程式和使用 ASP.NET Core 3.x 或升級至 5.0 RC1 或更新版本，您不需要變更自己的程式碼。</span><span class="sxs-lookup"><span data-stu-id="69596-128">An app and using ASP.NET Core 3.x or upgrading to 5.0 RC1 or later, you don't need to change your own code.</span></span> <span data-ttu-id="69596-129">但是，如果您相依于升級為帳戶以進行這項變更的程式庫，則您需要更新為該程式庫的較新版本。</span><span class="sxs-lookup"><span data-stu-id="69596-129">However, if you depend on a library that upgraded to account for this change, then you need to update to a newer version of that library.</span></span>
* <span data-ttu-id="69596-130">程式庫，而且只想要支援 ASP.NET Core 5.0 RC1 或更新版本，不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="69596-130">A library and want to support only ASP.NET Core 5.0 RC1 or later, no action is needed.</span></span> <span data-ttu-id="69596-131">請確定您的專案檔宣告 `<TargetFramework>` 的值為 `net5.0` 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="69596-131">Just ensure that your project file declares a `<TargetFramework>` value of `net5.0` or a later version.</span></span>
* <span data-ttu-id="69596-132">程式庫，而且想要同時支援 ASP.NET Core 3.x *和* 5.0，以判斷您的程式碼是否會讀取任何 `RenderTreeFrame` 成員。</span><span class="sxs-lookup"><span data-stu-id="69596-132">A library and want to support both ASP.NET Core 3.x *and* 5.0, determine whether your code reads any `RenderTreeFrame` members.</span></span> <span data-ttu-id="69596-133">例如，評估 `someRenderTreeFrame.FrameType` 。</span><span class="sxs-lookup"><span data-stu-id="69596-133">For example, evaluating `someRenderTreeFrame.FrameType`.</span></span>
  * <span data-ttu-id="69596-134">大部分的程式庫都不會讀取 `RenderTreeFrame` 成員，包括包含元件的程式庫 `.razor` 。</span><span class="sxs-lookup"><span data-stu-id="69596-134">Most libraries won't read `RenderTreeFrame` members, including libraries that contain `.razor` components.</span></span> <span data-ttu-id="69596-135">在此情況下，不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="69596-135">In this case, no action is needed.</span></span>
  * <span data-ttu-id="69596-136">但是，如果您的程式庫這樣做，則您需要多目標以支援 `netstandard2.1` 和 `net5.0` 。</span><span class="sxs-lookup"><span data-stu-id="69596-136">However, if your library does that, you'll need to multi-target to support both `netstandard2.1` and `net5.0`.</span></span> <span data-ttu-id="69596-137">將下列變更套用至您的專案檔：</span><span class="sxs-lookup"><span data-stu-id="69596-137">Apply the following changes in your project file:</span></span>
    * <span data-ttu-id="69596-138">以取代現有的 `<TargetFramework>` 元素 `<TargetFrameworks>netstandard2.0;net5.0</TargetFrameworks>` 。</span><span class="sxs-lookup"><span data-stu-id="69596-138">Replace the existing `<TargetFramework>` element with `<TargetFrameworks>netstandard2.0;net5.0</TargetFrameworks>`.</span></span>
    * <span data-ttu-id="69596-139">`Microsoft.AspNetCore.Components`針對您想要支援的兩個版本，請使用條件式套件參考來進行考慮。</span><span class="sxs-lookup"><span data-stu-id="69596-139">Use a conditional `Microsoft.AspNetCore.Components` package reference to account for both versions you wish to support.</span></span> <span data-ttu-id="69596-140">例如：</span><span class="sxs-lookup"><span data-stu-id="69596-140">For example:</span></span>

        ```xml
        <PackageReference Include="Microsoft.AspNetCore.Components" Version="3.0.0" Condition="'$(TargetFramework)' == 'netstandard2.0'" />
        <PackageReference Include="Microsoft.AspNetCore.Components" Version="5.0.0-rc.1.*" Condition="'$(TargetFramework)' != 'netstandard2.0'" />
        ```

<span data-ttu-id="69596-141">如需進一步的說明，請參閱此 [差異顯示 @jsakamoto 已升級連結 `Toolbelt.Blazor.HeadElement` 庫的方式](https://github.com/jsakamoto/Toolbelt.Blazor.HeadElement/commit/090df430ba725f9420d412753db8104e8c32bf51)。</span><span class="sxs-lookup"><span data-stu-id="69596-141">For further clarification, see this [diff showing how @jsakamoto already upgraded the `Toolbelt.Blazor.HeadElement` library](https://github.com/jsakamoto/Toolbelt.Blazor.HeadElement/commit/090df430ba725f9420d412753db8104e8c32bf51).</span></span>

#### <a name="category"></a><span data-ttu-id="69596-142">類別</span><span class="sxs-lookup"><span data-stu-id="69596-142">Category</span></span>

<span data-ttu-id="69596-143">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="69596-143">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="69596-144">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="69596-144">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame`

-->

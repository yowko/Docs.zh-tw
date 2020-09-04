---
title: 修剪獨立的應用程式
description: 瞭解如何修剪獨立的應用程式，以縮減其大小。 .NET Core 會將執行時間與獨立發行的應用程式組合，而且通常會包含更多執行時間，因此是必要的。
author: jamshedd
ms.author: jamshedd
ms.date: 04/03/2020
ms.openlocfilehash: 9c2994c98a2ebe6f45b056256c2bda28db017fbf
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465477"
---
# <a name="trim-self-contained-deployments-and-executables"></a><span data-ttu-id="7056c-104">修剪獨立式部署及可執行檔</span><span class="sxs-lookup"><span data-stu-id="7056c-104">Trim self-contained deployments and executables</span></span>

<span data-ttu-id="7056c-105">從 .NET 開始， [framework 相依的部署模型](index.md#publish-framework-dependent) 是最成功的部署模型。</span><span class="sxs-lookup"><span data-stu-id="7056c-105">The [framework-dependent deployment model](index.md#publish-framework-dependent) has been the most successful deployment model since the inception of .NET.</span></span> <span data-ttu-id="7056c-106">在此案例中，應用程式開發人員只會將應用程式和協力廠商元件組合在一起，並預期在用戶端電腦上可以使用 .NET 執行時間和架構程式庫。</span><span class="sxs-lookup"><span data-stu-id="7056c-106">In this scenario, the application developer bundles only the application and third-party assemblies with the expectation that the .NET runtime and framework libraries will be available in the client machine.</span></span> <span data-ttu-id="7056c-107">此部署模型也會繼續成為 .NET Core 中的主應用程式，但在某些情況下，framework 相依的模型不是最佳的。</span><span class="sxs-lookup"><span data-stu-id="7056c-107">This deployment model continues to be the dominant one in .NET Core as well but there are some scenarios where the framework-dependent model is not optimal.</span></span> <span data-ttu-id="7056c-108">替代方式是發佈獨立式 [應用程式](index.md#publish-self-contained)，其中 .net Core 執行時間和架構會與應用程式和協力廠商元件一起配套。</span><span class="sxs-lookup"><span data-stu-id="7056c-108">The alternative is to publish a [self-contained application](index.md#publish-self-contained), where the .NET Core runtime and framework are bundled together with the application and third-party assemblies.</span></span>

<span data-ttu-id="7056c-109">Trim 獨立部署模型是獨立部署模型的特製化版本，已優化以減少部署大小。</span><span class="sxs-lookup"><span data-stu-id="7056c-109">The trim-self-contained deployment model is a specialized version of the self-contained deployment model that is optimized to reduce deployment size.</span></span> <span data-ttu-id="7056c-110">將部署大小降至最低是某些用戶端案例的重要需求，例如 Blazor 應用程式。</span><span class="sxs-lookup"><span data-stu-id="7056c-110">Minimizing deployment size is a critical requirement for some client-side scenarios like Blazor applications.</span></span> <span data-ttu-id="7056c-111">視應用程式的複雜度而定，只會參考架構元件的子集，而每個元件內的程式碼子集都需要執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="7056c-111">Depending on the complexity of the application, only a subset of the framework assemblies are referenced, and a subset of the code within each assembly is required to run the application.</span></span> <span data-ttu-id="7056c-112">未使用的程式庫部分是不必要的，而且可以從封裝的應用程式中修剪。</span><span class="sxs-lookup"><span data-stu-id="7056c-112">The unused parts of the libraries are unnecessary and can be trimmed from the packaged application.</span></span>

<span data-ttu-id="7056c-113">但是，應用程式的組建時間分析可能會在執行時間造成失敗，因為無法可靠地分析各種有問題的程式碼模式 (主要是以反映使用) 為中心。</span><span class="sxs-lookup"><span data-stu-id="7056c-113">However, there is a risk that the build time analysis of the application can cause failures at runtime, due to not being able to reliably analyze various problematic code patterns (largely centered on reflection use).</span></span> <span data-ttu-id="7056c-114">因為無法保證可靠性，所以會以預覽功能的形式提供此部署模型。</span><span class="sxs-lookup"><span data-stu-id="7056c-114">Because reliability can't be guaranteed, this deployment model is offered as a preview feature.</span></span>

<span data-ttu-id="7056c-115">組建時間分析引擎會為程式碼模式的開發人員提供警告，以偵測需要哪些其他程式碼。</span><span class="sxs-lookup"><span data-stu-id="7056c-115">The build time analysis engine provides warnings to the developer of code patterns that are problematic to detect which other code is required.</span></span> <span data-ttu-id="7056c-116">您可以使用屬性來標注程式碼，以告訴修剪器要包含的其他內容。</span><span class="sxs-lookup"><span data-stu-id="7056c-116">Code can be annotated with attributes to tell the trimmer what else to include.</span></span> <span data-ttu-id="7056c-117">您可以使用 [來源](https://github.com/dotnet/roslyn/blob/master/docs/features/source-generators.md)產生器，將許多反映模式取代為組建階段程式碼。</span><span class="sxs-lookup"><span data-stu-id="7056c-117">Many reflection patterns can be replaced with build-time code generation using [Source Generators](https://github.com/dotnet/roslyn/blob/master/docs/features/source-generators.md).</span></span>

<span data-ttu-id="7056c-118">應用程式的修剪模式是使用設定進行設定 `TrimMode` 。</span><span class="sxs-lookup"><span data-stu-id="7056c-118">The trim mode for the applications is configured with the `TrimMode` setting.</span></span> <span data-ttu-id="7056c-119">預設值為 `copyused` ，並將參考的元件與應用程式配套。</span><span class="sxs-lookup"><span data-stu-id="7056c-119">The default value is `copyused` and bundles referenced assemblies with the application.</span></span> <span data-ttu-id="7056c-120">此 `link` 值會與 Blazor WebAssembly 應用程式搭配使用，並在元件中修剪未使用的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7056c-120">The `link` value is used with Blazor WebAssembly applications and trims unused code within assemblies.</span></span> <span data-ttu-id="7056c-121">Trim 分析警告會提供無法進行完整相依性分析的程式碼模式相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7056c-121">Trim analysis warnings give information on code patterns where a full dependency analysis was not possible.</span></span> <span data-ttu-id="7056c-122">預設會隱藏這些警告，並可將旗標設為來開啟這些警告 `SuppressTrimAnalysisWarnings` `false` 。</span><span class="sxs-lookup"><span data-stu-id="7056c-122">These warnings are suppressed by default and can be turned on by setting the flag `SuppressTrimAnalysisWarnings` to `false`.</span></span> <span data-ttu-id="7056c-123">如需可用之修剪選項的詳細資訊，請參閱 [修剪選項](trimming-options.md)。</span><span class="sxs-lookup"><span data-stu-id="7056c-123">For more information about the trim options available, see [Trimming options](trimming-options.md).</span></span>

> [!NOTE]
> <span data-ttu-id="7056c-124">修剪是 .NET Core 3.1、5.0 中的實驗性功能， _僅_ 適用于獨立發行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="7056c-124">Trimming is an experimental feature in .NET Core 3.1, 5.0 and is _only_ available to applications that are published self-contained.</span></span>

## <a name="prevent-assemblies-from-being-trimmed"></a><span data-ttu-id="7056c-125">防止元件遭到修剪</span><span class="sxs-lookup"><span data-stu-id="7056c-125">Prevent assemblies from being trimmed</span></span>

<span data-ttu-id="7056c-126">有些情況下，修剪功能將無法偵測到參考。</span><span class="sxs-lookup"><span data-stu-id="7056c-126">There are scenarios in which the trimming functionality will fail to detect references.</span></span> <span data-ttu-id="7056c-127">例如，當您的應用程式或應用程式所參考的程式庫在執行時間元件上使用反映時，不會直接參考該元件。</span><span class="sxs-lookup"><span data-stu-id="7056c-127">For example, when reflection is used on a runtime assembly, either by your application or a library that is referenced by your application, the assembly isn't directly referenced.</span></span> <span data-ttu-id="7056c-128">修剪不知道這些間接參考，而會將程式庫從已發行的資料夾中排除。</span><span class="sxs-lookup"><span data-stu-id="7056c-128">Trimming is unaware of these indirect references and would exclude the library from the published folder.</span></span>

<span data-ttu-id="7056c-129">當程式碼透過反映間接參考元件時，您可以防止元件使用設定進行修剪 `<TrimmerRootAssembly>` 。</span><span class="sxs-lookup"><span data-stu-id="7056c-129">When the code is indirectly referencing an assembly through reflection, you can prevent the assembly from being trimmed with the `<TrimmerRootAssembly>` setting.</span></span> <span data-ttu-id="7056c-130">下列範例示範如何防止元件稱為「元件」進行 `System.Security` 修剪：</span><span class="sxs-lookup"><span data-stu-id="7056c-130">The following example shows how to prevent an assembly called `System.Security` assembly from being trimmed:</span></span>

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="trim-your-app---cli"></a><span data-ttu-id="7056c-131">修剪您的應用程式-CLI</span><span class="sxs-lookup"><span data-stu-id="7056c-131">Trim your app - CLI</span></span>

<span data-ttu-id="7056c-132">使用 [dotnet publish](../tools/dotnet-publish.md) 命令修剪您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="7056c-132">Trim your application using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span> <span data-ttu-id="7056c-133">當您發佈應用程式時，請設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="7056c-133">When you publish your app, set the following properties:</span></span>

- <span data-ttu-id="7056c-134">發佈為特定執行時間的獨立應用程式： `-r win-x64`</span><span class="sxs-lookup"><span data-stu-id="7056c-134">Publish as a self-contained app for a specific runtime: `-r win-x64`</span></span>
- <span data-ttu-id="7056c-135">啟用修剪： `/p:PublishTrimmed=true`</span><span class="sxs-lookup"><span data-stu-id="7056c-135">Enable trimming: `/p:PublishTrimmed=true`</span></span>

<span data-ttu-id="7056c-136">下列範例會將適用于 Windows 的應用程式發佈為獨立的應用程式，並修剪輸出。</span><span class="sxs-lookup"><span data-stu-id="7056c-136">The following example publishes an app for Windows as self-contained and trims the output.</span></span>

```xml
<PropertyGroup>
    <RuntimeIdentifier>win-x64</RuntimeIdentifier>
    <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

<span data-ttu-id="7056c-137">下列範例會在積極的修剪模式中發佈應用程式，而元件中未使用的程式碼將會被修剪，並啟用修剪器警告。</span><span class="sxs-lookup"><span data-stu-id="7056c-137">The following example publishes an app in the aggressive trim mode where unused code within assemblies will be trimmed and trimmer warnings enabled.</span></span>

```xml
<PropertyGroup>
    <RuntimeIdentifier>win-x64</RuntimeIdentifier>
    <PublishTrimmed>true</PublishTrimmed>
    <TrimMode>link</TrimMode>
    <SuppressTrimAnalysisWarnings>false</SuppressTrimAnalysisWarnings>
</PropertyGroup>
```

<span data-ttu-id="7056c-138">如需詳細資訊，請參閱 [使用 .NET Core CLI 發佈 .Net Core 應用程式](deploy-with-cli.md)。</span><span class="sxs-lookup"><span data-stu-id="7056c-138">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="trim-your-app---visual-studio"></a><span data-ttu-id="7056c-139">修剪您的應用程式-Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7056c-139">Trim your app - Visual Studio</span></span>

<span data-ttu-id="7056c-140">Visual Studio 會建立可重複使用的發行設定檔，以控制您的應用程式發佈方式。</span><span class="sxs-lookup"><span data-stu-id="7056c-140">Visual Studio creates reusable publishing profiles that control how your application is published.</span></span>

01. <span data-ttu-id="7056c-141">在 [ **方案總管** ] 窗格中，以滑鼠右鍵按一下您要發行的專案。</span><span class="sxs-lookup"><span data-stu-id="7056c-141">On the **Solution Explorer** pane, right-click on the project you want to publish.</span></span> <span data-ttu-id="7056c-142">選取 [ **發佈 ...**]。</span><span class="sxs-lookup"><span data-stu-id="7056c-142">Select **Publish...**.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-solution-explorer.png" alt-text="使用醒目提示 [發佈] 選項的右鍵功能表方案總管。":::

    <span data-ttu-id="7056c-144">如果您還沒有發行設定檔，請遵循指示來建立一個設定檔，並選擇 [ **資料夾** 目標] 類型。</span><span class="sxs-lookup"><span data-stu-id="7056c-144">If you don't already have a publishing profile, follow the instructions to create one and choose the **Folder** target-type.</span></span>

01. <span data-ttu-id="7056c-145">選擇 [編輯]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7056c-145">Choose **Edit**.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-edit-settings.png" alt-text="Visual studio 以編輯按鈕發行設定檔。":::

01. <span data-ttu-id="7056c-147">在 [ **設定檔設定** ] 對話方塊中，設定下列選項：</span><span class="sxs-lookup"><span data-stu-id="7056c-147">In the **Profile settings** dialog, set the following options:</span></span>

    - <span data-ttu-id="7056c-148">設定**獨立**的**部署模式**。</span><span class="sxs-lookup"><span data-stu-id="7056c-148">Set **Deployment mode** to **Self-contained**.</span></span>
    - <span data-ttu-id="7056c-149">將 **目標運行** 時間設定為您想要發佈的目標平臺。</span><span class="sxs-lookup"><span data-stu-id="7056c-149">Set **Target runtime** to the platform you want to publish to.</span></span>
    - <span data-ttu-id="7056c-150">**在 [預覽]) 中選取 [修剪未使用的元件 (**]。</span><span class="sxs-lookup"><span data-stu-id="7056c-150">Select **Trim unused assemblies (in preview)**.</span></span>

    <span data-ttu-id="7056c-151">選擇 [ **儲存** ] 以儲存設定，並返回 [ **發佈** ] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7056c-151">Choose **Save** to save the settings and return to the **Publish** dialog.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-properties.png" alt-text="醒目提示具有部署模式、目標執行時間和修剪未使用元件選項的 [設定檔設定] 對話方塊。":::

01. <span data-ttu-id="7056c-153">選擇 [ **發行** ] 以發行已修剪的應用程式。</span><span class="sxs-lookup"><span data-stu-id="7056c-153">Choose **Publish** to publish your app trimmed.</span></span>

<span data-ttu-id="7056c-154">如需詳細資訊，請參閱 [使用 Visual Studio 發佈 .Net Core 應用程式](deploy-with-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="7056c-154">For more information, see [Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>

## <a name="trim-your-app---visual-studio-for-mac"></a><span data-ttu-id="7056c-155">修剪您的應用程式-Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="7056c-155">Trim your app - Visual Studio for Mac</span></span>

<span data-ttu-id="7056c-156">Visual Studio for Mac 不會提供在發佈期間修剪應用程式的選項。</span><span class="sxs-lookup"><span data-stu-id="7056c-156">Visual Studio for Mac doesn't provide options to trim your app during publish.</span></span> <span data-ttu-id="7056c-157">您必須遵循 [ [修剪您的應用程式-CLI](#trim-your-app---cli) ] 區段中的指示，手動發佈。</span><span class="sxs-lookup"><span data-stu-id="7056c-157">You'll need to publish manually by following the instructions from the [Trim your app - CLI](#trim-your-app---cli) section.</span></span> <span data-ttu-id="7056c-158">如需詳細資訊，請參閱 [使用 .NET Core CLI 發佈 .Net Core 應用程式](deploy-with-cli.md)。</span><span class="sxs-lookup"><span data-stu-id="7056c-158">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7056c-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7056c-159">See also</span></span>

- <span data-ttu-id="7056c-160">[.Net Core 應用程式部署](index.md)。</span><span class="sxs-lookup"><span data-stu-id="7056c-160">[.NET Core application deployment](index.md).</span></span>
- <span data-ttu-id="7056c-161">[使用 .NET Core CLI 發佈 .Net Core 應用程式](deploy-with-cli.md)。</span><span class="sxs-lookup"><span data-stu-id="7056c-161">[Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>
- <span data-ttu-id="7056c-162">[使用 Visual Studio 發佈 .Net Core 應用程式](deploy-with-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="7056c-162">[Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>
- <span data-ttu-id="7056c-163">[dotnet publish 命令](../tools/dotnet-publish.md)。</span><span class="sxs-lookup"><span data-stu-id="7056c-163">[dotnet publish command](../tools/dotnet-publish.md).</span></span>

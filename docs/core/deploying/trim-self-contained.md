---
title: 修剪自包含應用程式
description: 瞭解如何修剪自包含應用以減小其大小。 .NET Core 將運行時與自包含發佈的應用捆綁在一起,並且通常包含更多運行時,因此有必要這樣做。
author: jamshedd
ms.author: jamshedd
ms.date: 04/03/2020
ms.openlocfilehash: bb8ac88c5e16b7fd20a7670e4ad76dbe4b44da1b
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242896"
---
# <a name="trim-self-contained-deployments-and-executables"></a><span data-ttu-id="0f880-104">修剪獨立式部署及可執行檔</span><span class="sxs-lookup"><span data-stu-id="0f880-104">Trim self-contained deployments and executables</span></span>

<span data-ttu-id="0f880-105">發佈應用程式自包含時,.NET Core 運行時與應用程式捆綁在一起。</span><span class="sxs-lookup"><span data-stu-id="0f880-105">When publishing an application self-contained, the .NET Core runtime is bundled together with the application.</span></span> <span data-ttu-id="0f880-106">這種捆綁為打包的應用程式增加了大量內容。</span><span class="sxs-lookup"><span data-stu-id="0f880-106">This bundling adds a significant amount of content to your packaged application.</span></span> <span data-ttu-id="0f880-107">在部署應用程式時,大小通常是一個重要因素。</span><span class="sxs-lookup"><span data-stu-id="0f880-107">When it comes to deploying your application, size is often an important factor.</span></span> <span data-ttu-id="0f880-108">保持包應用程式的大小盡可能小通常是應用程式開發人員的目標。</span><span class="sxs-lookup"><span data-stu-id="0f880-108">Keeping the size of the package application as small as possible is typically a goal for application developers.</span></span>

<span data-ttu-id="0f880-109">根據應用程式的複雜性,運行應用程式只需要運行時的子集。</span><span class="sxs-lookup"><span data-stu-id="0f880-109">Depending on the complexity of the application, only a subset of the runtime is required to run the application.</span></span> <span data-ttu-id="0f880-110">這些未使用的運行時部分是不必要的,可以從打包的應用程式修剪。</span><span class="sxs-lookup"><span data-stu-id="0f880-110">These unused parts of the runtime are unnecessary and can be trimmed from the packaged application.</span></span>

<span data-ttu-id="0f880-111">修剪功能的工作原理是檢查應用程式二進位檔,以發現和生成所需運行時程式集的圖形。</span><span class="sxs-lookup"><span data-stu-id="0f880-111">The trimming feature works by examining the application binaries to discover and build a graph of the required runtime assemblies.</span></span> <span data-ttu-id="0f880-112">排除未引用的剩餘運行時程式集。</span><span class="sxs-lookup"><span data-stu-id="0f880-112">The remaining runtime assemblies that aren't referenced are excluded.</span></span>

> [!NOTE]
> <span data-ttu-id="0f880-113">修剪是 .NET Core 3.1 中的實驗功能,_僅適用於_自包含發布的應用程式。</span><span class="sxs-lookup"><span data-stu-id="0f880-113">Trimming is an experimental feature in .NET Core 3.1 and is _only_ available to applications that are published self-contained.</span></span>

## <a name="prevent-assemblies-from-being-trimmed"></a><span data-ttu-id="0f880-114">防止修剪裝配體</span><span class="sxs-lookup"><span data-stu-id="0f880-114">Prevent assemblies from being trimmed</span></span>

<span data-ttu-id="0f880-115">在某些情況下,修剪功能將無法檢測引用。</span><span class="sxs-lookup"><span data-stu-id="0f880-115">There are scenarios in which the trimming functionality will fail to detect references.</span></span> <span data-ttu-id="0f880-116">例如,當應用程式或應用程式引用的庫在運行時程式集上使用反射時,不會直接引用該程式集。</span><span class="sxs-lookup"><span data-stu-id="0f880-116">For example, when reflection is used on a runtime assembly, either by your application or a library that is referenced by your application, the assembly isn't directly referenced.</span></span> <span data-ttu-id="0f880-117">修剪不知道這些間接引用,並且會將庫從已發佈的資料夾中排除。</span><span class="sxs-lookup"><span data-stu-id="0f880-117">Trimming is unaware of these indirect references and would exclude the library from the published folder.</span></span>

<span data-ttu-id="0f880-118">當代碼通過反射間接引用程式集時,可以防止使用`<TrimmerRootAssembly>`設置修剪程式集。</span><span class="sxs-lookup"><span data-stu-id="0f880-118">When the code is indirectly referencing an assembly through reflection, you can prevent the assembly from being trimmed with the `<TrimmerRootAssembly>` setting.</span></span> <span data-ttu-id="0f880-119">下面的範例簡報如何防止修剪`System.Security`稱為 程式集的程式集:</span><span class="sxs-lookup"><span data-stu-id="0f880-119">The following example shows how to prevent an assembly called `System.Security` assembly from being trimmed:</span></span>

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="trim-your-app---cli"></a><span data-ttu-id="0f880-120">修剪你的應用程式 - CLI</span><span class="sxs-lookup"><span data-stu-id="0f880-120">Trim your app - CLI</span></span>

<span data-ttu-id="0f880-121">使用[dotnet 發佈](../tools/dotnet-publish.md)命令修剪應用程式。</span><span class="sxs-lookup"><span data-stu-id="0f880-121">Trim your application using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span> <span data-ttu-id="0f880-122">發佈應用時,請設置以下三個設置:</span><span class="sxs-lookup"><span data-stu-id="0f880-122">When you publish your app, set the following three settings:</span></span>

- <span data-ttu-id="0f880-123">以自包含身份發佈:`--self-contained true`</span><span class="sxs-lookup"><span data-stu-id="0f880-123">Publish as self-contained: `--self-contained true`</span></span>
- <span data-ttu-id="0f880-124">關閉單檔:`-p:PublishSingleFile=false`</span><span class="sxs-lookup"><span data-stu-id="0f880-124">Disable single-file publishing: `-p:PublishSingleFile=false`</span></span>
- <span data-ttu-id="0f880-125">開啟修剪:`p:PublishTrimmed=true`</span><span class="sxs-lookup"><span data-stu-id="0f880-125">Enable trimming: `p:PublishTrimmed=true`</span></span>

<span data-ttu-id="0f880-126">下面的範例將 Windows 10 的應用發佈為自包含並修剪輸出。</span><span class="sxs-lookup"><span data-stu-id="0f880-126">The following example publishes an app for Windows 10 as self-contained and trims the output.</span></span>

```dotnetcli
dotnet publish -c Release -r win10-x64 --self-contained true -p:PublishSingleFile=false -p:PublishTrimmed=true
```

<span data-ttu-id="0f880-127">有關詳細資訊,請參閱發佈[.NET 核心應用 ,以及 .NET 核心 CLI](deploy-with-cli.md)。</span><span class="sxs-lookup"><span data-stu-id="0f880-127">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="trim-your-app---visual-studio"></a><span data-ttu-id="0f880-128">修剪你的應用程式 - 視覺工作室</span><span class="sxs-lookup"><span data-stu-id="0f880-128">Trim your app - Visual Studio</span></span>

<span data-ttu-id="0f880-129">Visual Studio 創建可重用的發佈配置檔,以控制應用程式的發佈方式。</span><span class="sxs-lookup"><span data-stu-id="0f880-129">Visual Studio creates reusable publishing profiles that control how your application is published.</span></span>

01. <span data-ttu-id="0f880-130">在 **「解決方案資源管理員」** 窗格中,右鍵單擊要發布的專案。</span><span class="sxs-lookup"><span data-stu-id="0f880-130">On the **Solution Explorer** pane, right-click on the project you want to publish.</span></span> <span data-ttu-id="0f880-131">選擇 **"發佈..."**</span><span class="sxs-lookup"><span data-stu-id="0f880-131">Select **Publish...**.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-solution-explorer.png" alt-text="解決方案資源管理器,右鍵單擊功能表突出顯示發佈選項。":::

    <span data-ttu-id="0f880-133">如果還沒有發佈設定檔,請按照說明創建一個設定檔,然後選擇 **「資料夾**目標類型」。</span><span class="sxs-lookup"><span data-stu-id="0f880-133">If you don't already have a publishing profile, follow the instructions to create one and choose the **Folder** target-type.</span></span>

01. <span data-ttu-id="0f880-134">選擇 [編輯]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0f880-134">Choose **Edit**.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-edit-settings.png" alt-text="可視化工作室發佈配置檔與編輯按鈕。":::

01. <span data-ttu-id="0f880-136">在 **「設定檔設定」對話框**中,設定以下選項:</span><span class="sxs-lookup"><span data-stu-id="0f880-136">In the **Profile settings** dialog, set the following options:</span></span>

    - <span data-ttu-id="0f880-137">將**部署模式**設定為**自包含**。</span><span class="sxs-lookup"><span data-stu-id="0f880-137">Set **Deployment mode** to **Self-contained**.</span></span>
    - <span data-ttu-id="0f880-138">將**目標運行時**設置為要發佈到的平臺。</span><span class="sxs-lookup"><span data-stu-id="0f880-138">Set **Target runtime** to the platform you want to publish to.</span></span>
    - <span data-ttu-id="0f880-139">選擇 **「修剪未使用的裝配體(在預覽中)**</span><span class="sxs-lookup"><span data-stu-id="0f880-139">Select **Trim unused assemblies (in preview)**.</span></span>

    <span data-ttu-id="0f880-140">選擇 **「儲存**」以儲存設定並傳回到 **「發布」** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0f880-140">Choose **Save** to save the settings and return to the **Publish** dialog.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-properties.png" alt-text="設定檔設定對話框,突出顯示了部署模式、目標運行時和修剪未使用的程式集選項。":::

01. <span data-ttu-id="0f880-142">選擇 **「發布」** 以發佈已修剪的應用。</span><span class="sxs-lookup"><span data-stu-id="0f880-142">Choose **Publish** to publish your app trimmed.</span></span>

<span data-ttu-id="0f880-143">有關詳細資訊,請參閱發佈[.NET 核心應用與可視化工作室](deploy-with-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="0f880-143">For more information, see [Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>

## <a name="trim-your-app---visual-studio-for-mac"></a><span data-ttu-id="0f880-144">修剪你的應用程式 - Mac 的視覺化工作室</span><span class="sxs-lookup"><span data-stu-id="0f880-144">Trim your app - Visual Studio for Mac</span></span>

<span data-ttu-id="0f880-145">適用於 Mac 的可視化工作室不提供在發表期間修剪應用的選項。</span><span class="sxs-lookup"><span data-stu-id="0f880-145">Visual Studio for Mac doesn't provide options to trim your app during publish.</span></span> <span data-ttu-id="0f880-146">您需要按照[「修剪應用 - CLI」](#trim-your-app---cli)部分的說明手動發佈。</span><span class="sxs-lookup"><span data-stu-id="0f880-146">You'll need to publish manually by following the instructions from the [Trim your app - CLI](#trim-your-app---cli) section.</span></span> <span data-ttu-id="0f880-147">有關詳細資訊,請參閱發佈[.NET 核心應用 ,以及 .NET 核心 CLI](deploy-with-cli.md)。</span><span class="sxs-lookup"><span data-stu-id="0f880-147">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0f880-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f880-148">See also</span></span>

- <span data-ttu-id="0f880-149">[.NET 核心應用程式部署](index.md)。</span><span class="sxs-lookup"><span data-stu-id="0f880-149">[.NET Core application deployment](index.md).</span></span>
- <span data-ttu-id="0f880-150">[使用 .NET 核心 CLI 發佈 .NET 核心應用程式](deploy-with-cli.md)。</span><span class="sxs-lookup"><span data-stu-id="0f880-150">[Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>
- <span data-ttu-id="0f880-151">[發布 .NET 核心應用程式與視覺化工作室](deploy-with-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="0f880-151">[Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>
- <span data-ttu-id="0f880-152">[點網發佈命令](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="0f880-152">[dotnet publish command](../tools/dotnet-publish.md).</span></span>

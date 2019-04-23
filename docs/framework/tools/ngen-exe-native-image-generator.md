---
title: Ngen.exe (原生映像產生器)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Native Image Generator
- images [.NET Framework], native
- side-by-side execution, native images
- assemblies [.NET Framework], native image
- Ngen.exe
- native image generation
- native image cache
- publisher policy applied for native images
- invalid images
- BypassNGenAttribute
- System.Runtime.BypassNGenAttribute
ms.assetid: 44bf97aa-a9a4-4eba-9a0d-cfaa6fc53a66
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e425394df0d04ffbb4cde41c83a9efe3c5b4abe0
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/11/2019
ms.locfileid: "59481258"
---
# <a name="ngenexe-native-image-generator"></a><span data-ttu-id="4b8fc-102">Ngen.exe (原生映像產生器)</span><span class="sxs-lookup"><span data-stu-id="4b8fc-102">Ngen.exe (Native Image Generator)</span></span>

<span data-ttu-id="4b8fc-103">原生映像產生器 (Ngen.exe) 是一種可以增進 Managed 應用程式效能的工具。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-103">The Native Image Generator (Ngen.exe) is a tool that improves the performance of managed applications.</span></span> <span data-ttu-id="4b8fc-104">Ngen.exe 會建立原生映像，也就是包含已編譯之處理器特定機器碼的檔案，然後將原生映像安裝到本機電腦上的原生映像快取中。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-104">Ngen.exe creates native images, which are files containing compiled processor-specific machine code, and installs them into the native image cache on the local computer.</span></span> <span data-ttu-id="4b8fc-105">執行階段就可以從快取中使用原生映像，而不是使用 Just-In-Time (JIT) 編譯器來編譯原始組件。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-105">The runtime can use native images from the cache instead of using the just-in-time (JIT) compiler to compile the original assembly.</span></span>

<span data-ttu-id="4b8fc-106">Ngen.exe 在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 中的變更：</span><span class="sxs-lookup"><span data-stu-id="4b8fc-106">Changes to Ngen.exe in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]:</span></span>

- <span data-ttu-id="4b8fc-107">Ngen.exe 現在會以完全信任的方式編譯組件，而且不再評估程式碼存取安全性 (CAS) 原則。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-107">Ngen.exe now compiles assemblies with full trust, and code access security (CAS) policy is no longer evaluated.</span></span>

- <span data-ttu-id="4b8fc-108">以 Ngen.exe 產生的原生映像已無法載入以部分信任執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-108">Native images that are generated with Ngen.exe can no longer be loaded into applications that are running in partial trust.</span></span>

<span data-ttu-id="4b8fc-109">Ngen.exe 在 .NET Framework 2.0 版中的變更：</span><span class="sxs-lookup"><span data-stu-id="4b8fc-109">Changes to Ngen.exe in the .NET Framework version 2.0:</span></span>

- <span data-ttu-id="4b8fc-110">安裝組件時也會安裝其相依性，因而簡化 Ngen.exe 的語法。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-110">Installing an assembly also installs its dependencies, simplifying the syntax of Ngen.exe.</span></span>

- <span data-ttu-id="4b8fc-111">現在可以在應用程式定義域之間共用原生映像。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-111">Native images can now be shared across application domains.</span></span>

- <span data-ttu-id="4b8fc-112">`update` 這個新動作可以重新建立已經失效的映像。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-112">A new action, `update`, re-creates images that have been invalidated.</span></span>

- <span data-ttu-id="4b8fc-113">可以先延後動作，再讓於電腦上使用閒置時間的服務執行該動作，以產生及安裝映像。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-113">Actions can be deferred for execution by a service that uses idle time on the computer to generate and install images.</span></span>

- <span data-ttu-id="4b8fc-114">已經排除影像失效的某些原因。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-114">Some causes of image invalidation have been eliminated.</span></span>

<span data-ttu-id="4b8fc-115">在 Windows 8 上，請參閱[原生映像工作](#native-image-task)。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-115">On Windows 8, see [Native Image Task](#native-image-task).</span></span>

<span data-ttu-id="4b8fc-116">如需使用 Ngen.exe 和原生映像服務的詳細資訊，請參閱[原生映像服務](#native-image-service)。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-116">For additional information on using Ngen.exe and the native image service, see [Native Image Service](#native-image-service).</span></span>

> [!NOTE]
> <span data-ttu-id="4b8fc-117">您可以在[原生映像產生器 (Ngen.exe) 舊版語法](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms165073(v=vs.100))中找到 .NET Framework 1.0 和 1.1 版的 Ngen.exe 語法。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-117">Ngen.exe syntax for versions 1.0 and 1.1 of the .NET Framework can be found in [Native Image Generator (Ngen.exe) Legacy Syntax](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms165073(v=vs.100)).</span></span>

<span data-ttu-id="4b8fc-118">此工具會自動與 Visual Studio 一起安裝。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-118">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="4b8fc-119">若要執行這項工具，請使用 [Visual Studio 開發人員命令提示字元] (或 Windows 7 中的 [Visual Studio 命令提示字元])。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-119">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="4b8fc-120">如需詳細資訊，請參閱[命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-120">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="4b8fc-121">在命令提示字元下輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="4b8fc-121">At the command prompt, type the following:</span></span>

## <a name="syntax"></a><span data-ttu-id="4b8fc-122">語法</span><span class="sxs-lookup"><span data-stu-id="4b8fc-122">Syntax</span></span>

```
ngen action [options]
```

```
ngen /? | /help
```

## <a name="actions"></a><span data-ttu-id="4b8fc-123">動作</span><span class="sxs-lookup"><span data-stu-id="4b8fc-123">Actions</span></span>

<span data-ttu-id="4b8fc-124">下表顯示每個 `action` 的語法。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-124">The following table shows the syntax of each `action`.</span></span> <span data-ttu-id="4b8fc-125">如需 `action` 個別部分的描述，請參閱[引數](#ArgumentTable)、[優先權層級](#PriorityTable)、[情節](#ScenarioTable)，以及[組態](#ConfigTable)表格。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-125">For descriptions of the individual parts of an `action`, see the [Arguments](#ArgumentTable), [Priority Levels](#PriorityTable), [Scenarios](#ScenarioTable), and [Config](#ConfigTable) tables.</span></span> <span data-ttu-id="4b8fc-126">[選項](#OptionTable)表格則描述 `options` 和說明參數。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-126">The [Options](#OptionTable) table describes the `options` and the help switches.</span></span>

|<span data-ttu-id="4b8fc-127">動作</span><span class="sxs-lookup"><span data-stu-id="4b8fc-127">Action</span></span>|<span data-ttu-id="4b8fc-128">說明</span><span class="sxs-lookup"><span data-stu-id="4b8fc-128">Description</span></span>|
|------------|-----------------|
|`install` <span data-ttu-id="4b8fc-129">[`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`] [`/queue`[`:`{`1`&#124;`2`&#124;`3`}]]</span><span class="sxs-lookup"><span data-stu-id="4b8fc-129">[`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`] [`/queue`[`:`{`1`&#124;`2`&#124;`3`}]]</span></span>|<span data-ttu-id="4b8fc-130">產生組件的原生映像及其相依性，並在原生映像快取中安裝映像。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-130">Generate native images for an assembly and its dependencies and install the images in the native image cache.</span></span><br /><br /> <span data-ttu-id="4b8fc-131">如果已指定 `/queue`，原生映像服務的動作就會排入佇列。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-131">If `/queue` is specified, the action is queued for the native image service.</span></span> <span data-ttu-id="4b8fc-132">預設優先權為 3。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-132">The default priority is 3.</span></span> <span data-ttu-id="4b8fc-133">請參閱[優先權層級](#PriorityTable)表格。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-133">See the [Priority Levels](#PriorityTable) table.</span></span>|
|`uninstall` <span data-ttu-id="4b8fc-134">[`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`]</span><span class="sxs-lookup"><span data-stu-id="4b8fc-134">[`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`]</span></span>|<span data-ttu-id="4b8fc-135">從原生映像快取中刪除組件的原生映像和其相依性。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-135">Delete the native images of an assembly and its dependencies from the native image cache.</span></span><br /><br /> <span data-ttu-id="4b8fc-136">若要解除安裝單一映像和其相依性，請使用安裝影像時所用的相同命令列引數。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-136">To uninstall a single image and its dependencies, use the same command-line arguments that were used to install the image.</span></span> <span data-ttu-id="4b8fc-137">**注意：** 從 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 開始，不再支援 `uninstall` \* 動作。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-137">**Note:**  Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the action `uninstall` \* is no longer supported.</span></span>|
|`update` <span data-ttu-id="4b8fc-138">[`/queue`]</span><span class="sxs-lookup"><span data-stu-id="4b8fc-138">[`/queue`]</span></span>|<span data-ttu-id="4b8fc-139">更新已經變成無效的原生映像。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-139">Update native images that have become invalid.</span></span><br /><br /> <span data-ttu-id="4b8fc-140">如果已指定 `/queue`，原生映像服務的更新動作就會排入佇列。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-140">If `/queue` is specified, the updates are queued for the native image service.</span></span> <span data-ttu-id="4b8fc-141">更新動作一律會排在優先權 3，因此會在電腦為閒置時才執行。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-141">Updates are always scheduled at priority 3, so they run when the computer is idle.</span></span>|
|`display` <span data-ttu-id="4b8fc-142">[`assemblyName` &#124; `assemblyPath`]</span><span class="sxs-lookup"><span data-stu-id="4b8fc-142">[`assemblyName` &#124; `assemblyPath`]</span></span>|<span data-ttu-id="4b8fc-143">顯示組件的原生映像狀態和其相依性。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-143">Display the state of the native images for an assembly and its dependencies.</span></span><br /><br /> <span data-ttu-id="4b8fc-144">如果沒有提供任何引數，將顯示原生映像快取中的每個項目。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-144">If no argument is supplied, everything in the native image cache is displayed.</span></span>|
|`executeQueuedItems` <span data-ttu-id="4b8fc-145">[<code>1&#124;2&#124;3</code>]</span><span class="sxs-lookup"><span data-stu-id="4b8fc-145">[<code>1&#124;2&#124;3</code>]</span></span><br /><br /> <span data-ttu-id="4b8fc-146">-或-</span><span class="sxs-lookup"><span data-stu-id="4b8fc-146">-or-</span></span><br /><br /> `eqi` <span data-ttu-id="4b8fc-147">[1&#124;2&#124;3]</span><span class="sxs-lookup"><span data-stu-id="4b8fc-147">[1&#124;2&#124;3]</span></span>|<span data-ttu-id="4b8fc-148">執行排入佇列的編譯工作。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-148">Execute queued compilation jobs.</span></span><br /><br /> <span data-ttu-id="4b8fc-149">如果已指定優先權，就會執行具有較大或相同優先權的編譯工作。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-149">If a priority is specified, compilation jobs with greater or equal priority are executed.</span></span> <span data-ttu-id="4b8fc-150">如果沒有指定優先權，將會執行所有排入佇列的編譯工作。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-150">If no priority is specified, all queued compilation jobs are executed.</span></span>|
|`queue` <span data-ttu-id="4b8fc-151">{`pause` &#124; `continue` &#124; `status`}</span><span class="sxs-lookup"><span data-stu-id="4b8fc-151">{`pause` &#124; `continue` &#124; `status`}</span></span>|<span data-ttu-id="4b8fc-152">暫停原生映像服務，讓暫停的服務可繼續執行，或查詢服務的狀態。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-152">Pause the native image service, allow the paused service to continue, or query the status of the service.</span></span>|

<a name="ArgumentTable"></a>

## <a name="arguments"></a><span data-ttu-id="4b8fc-153">引數</span><span class="sxs-lookup"><span data-stu-id="4b8fc-153">Arguments</span></span>

|<span data-ttu-id="4b8fc-154">引數</span><span class="sxs-lookup"><span data-stu-id="4b8fc-154">Argument</span></span>|<span data-ttu-id="4b8fc-155">說明</span><span class="sxs-lookup"><span data-stu-id="4b8fc-155">Description</span></span>|
|--------------|-----------------|
|`assemblyName`|<span data-ttu-id="4b8fc-156">組件的完整顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-156">The full display name of the assembly.</span></span> <span data-ttu-id="4b8fc-157">例如，`"myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5"`。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-157">For example, `"myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5"`.</span></span> <span data-ttu-id="4b8fc-158">**注意：** 您可以提供組件的部分名稱 (例如 `myAssembly`) 以進行 `display` 和 `uninstall` 動作。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-158">**Note:**  You can supply a partial assembly name, such as `myAssembly`, for the `display` and `uninstall` actions.</span></span> <br /><br /> <span data-ttu-id="4b8fc-159">每一個 Ngen.exe 命令列只能指定一個組件。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-159">Only one assembly can be specified per Ngen.exe command line.</span></span>|
|`assemblyPath`|<span data-ttu-id="4b8fc-160">組件的明確路徑。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-160">The explicit path of the assembly.</span></span> <span data-ttu-id="4b8fc-161">您可以指定完整或相對路徑。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-161">You can specify a full or relative path.</span></span><br /><br /> <span data-ttu-id="4b8fc-162">如果指定檔案名稱但沒有指定路徑，則組件必須位於目前的目錄中。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-162">If you specify a file name without a path, the assembly must be located in the current directory.</span></span><br /><br /> <span data-ttu-id="4b8fc-163">每一個 Ngen.exe 命令列只能指定一個組件。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-163">Only one assembly can be specified per Ngen.exe command line.</span></span>|

<a name="PriorityTable"></a>

## <a name="priority-levels"></a><span data-ttu-id="4b8fc-164">優先權層級</span><span class="sxs-lookup"><span data-stu-id="4b8fc-164">Priority Levels</span></span>

|<span data-ttu-id="4b8fc-165">優先權</span><span class="sxs-lookup"><span data-stu-id="4b8fc-165">Priority</span></span>|<span data-ttu-id="4b8fc-166">說明</span><span class="sxs-lookup"><span data-stu-id="4b8fc-166">Description</span></span>|
|--------------|-----------------|
|`1`|<span data-ttu-id="4b8fc-167">立即產生並安裝原生映像，不等待閒置時間。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-167">Native images are generated and installed immediately, without waiting for idle time.</span></span>|
|`2`|<span data-ttu-id="4b8fc-168">產生並安裝原生映像，不等待閒置時間，但在完成所有優先權為 1 的操作 (及其相依性) 之後。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-168">Native images are generated and installed without waiting for idle time, but after all priority 1 actions (and their dependencies) have completed.</span></span>|
|`3`|<span data-ttu-id="4b8fc-169">當原生映像服務偵測到電腦閒置時安裝原生映像。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-169">Native images are installed when the native image service detects that the computer is idle.</span></span> <span data-ttu-id="4b8fc-170">請參閱[原生映像服務](#native-image-service)。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-170">See [Native Image Service](#native-image-service).</span></span>|

<a name="ScenarioTable"></a>

## <a name="scenarios"></a><span data-ttu-id="4b8fc-171">案例</span><span class="sxs-lookup"><span data-stu-id="4b8fc-171">Scenarios</span></span>

|<span data-ttu-id="4b8fc-172">情節</span><span class="sxs-lookup"><span data-stu-id="4b8fc-172">Scenario</span></span>|<span data-ttu-id="4b8fc-173">說明</span><span class="sxs-lookup"><span data-stu-id="4b8fc-173">Description</span></span>|
|--------------|-----------------|
|`/Debug`|<span data-ttu-id="4b8fc-174">產生可以在偵錯工具下使用的原生映像。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-174">Generate native images that can be used under a debugger.</span></span>|
|`/Profile`|<span data-ttu-id="4b8fc-175">產生可以在分析工具下使用的原生映像。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-175">Generate native images that can be used under a profiler.</span></span>|
|`/NoDependencies`|<span data-ttu-id="4b8fc-176">產生指定的情節選項所需的最小數量原生映像。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-176">Generate the minimum number of native images required by the specified scenario options.</span></span>|

<a name="ConfigTable"></a>

## <a name="config"></a><span data-ttu-id="4b8fc-177">組態</span><span class="sxs-lookup"><span data-stu-id="4b8fc-177">Config</span></span>

|<span data-ttu-id="4b8fc-178">組態</span><span class="sxs-lookup"><span data-stu-id="4b8fc-178">Configuration</span></span>|<span data-ttu-id="4b8fc-179">說明</span><span class="sxs-lookup"><span data-stu-id="4b8fc-179">Description</span></span>|
|-------------------|-----------------|
|`/ExeConfig:` `exePath`|<span data-ttu-id="4b8fc-180">使用指定之可執行組件的組態。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-180">Use the configuration of the specified executable assembly.</span></span><br /><br /> <span data-ttu-id="4b8fc-181">Ngen.exe 繫結至相依性時，必須做出與載入器一樣的決定。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-181">Ngen.exe needs to make the same decisions as the loader when binding to dependencies.</span></span> <span data-ttu-id="4b8fc-182">在執行階段載入共用元件時，如果使用 <xref:System.Reflection.Assembly.Load%2A> 方法，應用程式的組態檔就會判斷為共用元件載入的相依性，例如，載入的相依性版本。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-182">When a shared component is loaded at run time, using the <xref:System.Reflection.Assembly.Load%2A> method, the application's configuration file determines the dependencies that are loaded for the shared component — for example, the version of a dependency that is loaded.</span></span> <span data-ttu-id="4b8fc-183">`/ExeConfig` 參數會對 Ngen.exe 提供在執行階段時載入的相依性指引。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-183">The `/ExeConfig` switch gives Ngen.exe guidance on which dependencies would be loaded at run time.</span></span>|
|`/AppBase:` `directoryPath`|<span data-ttu-id="4b8fc-184">在尋找相依性時，使用指定的目錄做為應用程式基底。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-184">When locating dependencies, use the specified directory as the application base.</span></span>|

<a name="OptionTable"></a>

## <a name="options"></a><span data-ttu-id="4b8fc-185">選項</span><span class="sxs-lookup"><span data-stu-id="4b8fc-185">Options</span></span>

|<span data-ttu-id="4b8fc-186">選項</span><span class="sxs-lookup"><span data-stu-id="4b8fc-186">Option</span></span>|<span data-ttu-id="4b8fc-187">說明</span><span class="sxs-lookup"><span data-stu-id="4b8fc-187">Description</span></span>|
|------------|-----------------|
|`/nologo`|<span data-ttu-id="4b8fc-188">隱藏 Microsoft 程式啟始資訊的顯示。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-188">Suppress the Microsoft startup banner display.</span></span>|
|`/silent`|<span data-ttu-id="4b8fc-189">隱藏成功訊息的顯示。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-189">Suppress the display of success messages.</span></span>|
|`/verbose`|<span data-ttu-id="4b8fc-190">顯示用來偵錯的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-190">Display detailed information for debugging.</span></span> <span data-ttu-id="4b8fc-191">**注意：** 由於作業系統限制的關係，這個選項在 Windows 98 和 Windows Millennium Edition 上不會顯示那麼多詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-191">**Note:**  Due to operating system limitations, this option does not display as much additional information on Windows 98 and Windows Millennium Edition.</span></span>|
|`/help`<span data-ttu-id="4b8fc-192">,</span><span class="sxs-lookup"><span data-stu-id="4b8fc-192">,</span></span> `/?`|<span data-ttu-id="4b8fc-193">顯示目前版本的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-193">Display command syntax and options for the current release.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4b8fc-194">備註</span><span class="sxs-lookup"><span data-stu-id="4b8fc-194">Remarks</span></span>

<span data-ttu-id="4b8fc-195">若要執行 Ngen.exe，您必須具有系統管理員權限。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-195">To run Ngen.exe, you must have administrative privileges.</span></span>

> [!CAUTION]
> <span data-ttu-id="4b8fc-196">請勿在不受完全信任的組件上執行 Ngen.exe。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-196">Do not run Ngen.exe on assemblies that are not fully trusted.</span></span> <span data-ttu-id="4b8fc-197">從 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 開始，Ngen.exe 都以完全信任的方式來編譯組件，而且不再評估程式碼存取安全性 (CAS) 原則。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-197">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Ngen.exe compiles assemblies with full trust, and code access security (CAS) policy is no longer evaluated.</span></span>

<span data-ttu-id="4b8fc-198">從 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 開始，以 Ngen.exe 產生的原生映像，不再載入至以部分信任執行的應用程式中。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-198">Starting with the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], the native images that are generated with Ngen.exe can no longer be loaded into applications that are running in partial trust.</span></span> <span data-ttu-id="4b8fc-199">而是會改為叫用 Just-In-Time (JIT) 編譯器。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-199">Instead, the just-in-time (JIT) compiler is invoked.</span></span>

<span data-ttu-id="4b8fc-200">Ngen.exe 會產生 `install` 動作的 `assemblyname` 引數所指定組件的原生映像和其所有相依性。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-200">Ngen.exe generates native images for the assembly specified by the `assemblyname` argument to the `install` action and all its dependencies.</span></span> <span data-ttu-id="4b8fc-201">相依性是由組件資訊清單中的參考所決定。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-201">Dependencies are determined from references in the assembly manifest.</span></span> <span data-ttu-id="4b8fc-202">唯一需要個別安裝相依性的狀況，是在應用程式使用反映將它載入時 (例如，藉由呼叫 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> 方法)。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-202">The only scenario in which you need to install a dependency separately is when the application loads it using reflection, for example by calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4b8fc-203">請勿對原生映像使用 <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-203">Do not use the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method with native images.</span></span> <span data-ttu-id="4b8fc-204">使用這個方法載入的映像無法供執行內容中的其他組件使用。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-204">An image loaded with this method cannot be used by other assemblies in the execution context.</span></span>

<span data-ttu-id="4b8fc-205">Ngen.exe 會維護相依性的計數。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-205">Ngen.exe maintains a count on dependencies.</span></span> <span data-ttu-id="4b8fc-206">例如，假設 `MyAssembly.exe` 和 `YourAssembly.exe` 兩者都安裝在原生映像快取中，且兩者都有 `OurDependency.dll` 的參考。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-206">For example, suppose `MyAssembly.exe` and `YourAssembly.exe` are both installed in the native image cache, and both have references to `OurDependency.dll`.</span></span> <span data-ttu-id="4b8fc-207">如果 `MyAssembly.exe` 已解除安裝，則 `OurDependency.dll` 不會解除安裝。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-207">If `MyAssembly.exe` is uninstalled, `OurDependency.dll` is not uninstalled.</span></span> <span data-ttu-id="4b8fc-208">只有在 `YourAssembly.exe` 也解除安裝時，才會將它移除。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-208">It is only removed when `YourAssembly.exe` is also uninstalled.</span></span>

<span data-ttu-id="4b8fc-209">如果正在全域組件快取中產生組件的原生映像，請指定它的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-209">If you are generating a native image for an assembly in the global assembly cache, specify its display name.</span></span> <span data-ttu-id="4b8fc-210">請參閱 <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-210">See <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="4b8fc-211">Ngen.exe 產生的原生映像可以在應用程式定義域之間共用。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-211">The native images that Ngen.exe generates can be shared across application domains.</span></span> <span data-ttu-id="4b8fc-212">這表示您可以在需要跨應用程式定義域共用組件的應用程式案例中使用 Ngen.exe。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-212">This means you can use Ngen.exe in application scenarios that require assemblies to be shared across application domains.</span></span> <span data-ttu-id="4b8fc-213">若要指定定義域中立性：</span><span class="sxs-lookup"><span data-stu-id="4b8fc-213">To specify domain neutrality:</span></span>

- <span data-ttu-id="4b8fc-214">將 <xref:System.LoaderOptimizationAttribute> 屬性套用至應用程式。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-214">Apply the <xref:System.LoaderOptimizationAttribute> attribute to your application.</span></span>

- <span data-ttu-id="4b8fc-215">當您建立新應用程式定義域的安裝資訊時，請設定 <xref:System.AppDomainSetup.LoaderOptimization%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-215">Set the <xref:System.AppDomainSetup.LoaderOptimization%2A?displayProperty=nameWithType> property when you create setup information for a new application domain.</span></span>

<span data-ttu-id="4b8fc-216">將相同的組件載入多個應用程式定義域時，一律使用定義域中性程式碼。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-216">Always use domain-neutral code when loading the same assembly into multiple application domains.</span></span> <span data-ttu-id="4b8fc-217">如果原生映像在載入共用定義域之後載入未共用的應用程式定義域，就會無法使用。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-217">If a native image is loaded into a nonshared application domain after having been loaded into a shared domain, it cannot be used.</span></span>

> [!NOTE]
> <span data-ttu-id="4b8fc-218">無法卸載定義域中性程式碼，特別是在存取靜態成員時，效能可能會稍微變慢。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-218">Domain-neutral code cannot be unloaded, and performance may be slightly slower, particularly when accessing static members.</span></span>

<span data-ttu-id="4b8fc-219">在＜備註＞一節中：</span><span class="sxs-lookup"><span data-stu-id="4b8fc-219">In this Remarks section:</span></span>

- [<span data-ttu-id="4b8fc-220">產生不同情節的映像</span><span class="sxs-lookup"><span data-stu-id="4b8fc-220">Generating images for different scenarios</span></span>](#Scenarios)

- [<span data-ttu-id="4b8fc-221">判斷使用原生映像的時機</span><span class="sxs-lookup"><span data-stu-id="4b8fc-221">Determining when to Use native images</span></span>](#WhenToUse)

  - [<span data-ttu-id="4b8fc-222">改進記憶體使用</span><span class="sxs-lookup"><span data-stu-id="4b8fc-222">Improved memory use</span></span>](#Memory)

  - [<span data-ttu-id="4b8fc-223">應用程式啟動較快</span><span class="sxs-lookup"><span data-stu-id="4b8fc-223">Faster application startup</span></span>](#Startup)

  - [<span data-ttu-id="4b8fc-224">使用方式考量摘要</span><span class="sxs-lookup"><span data-stu-id="4b8fc-224">Summary of usage considerations</span></span>](#UsageSummary)

- [<span data-ttu-id="4b8fc-225">組件基底位址的重要性</span><span class="sxs-lookup"><span data-stu-id="4b8fc-225">Importance of assembly base addresses</span></span>](#BaseAddresses)

- [<span data-ttu-id="4b8fc-226">硬式繫結</span><span class="sxs-lookup"><span data-stu-id="4b8fc-226">Hard binding</span></span>](#HardBinding)

  - [<span data-ttu-id="4b8fc-227">指定相依性的繫結提示</span><span class="sxs-lookup"><span data-stu-id="4b8fc-227">Specifying a binding hint for a dependency</span></span>](#DependencyHint)

  - [<span data-ttu-id="4b8fc-228">指定組件的預設繫結提示</span><span class="sxs-lookup"><span data-stu-id="4b8fc-228">Specifying a default binding hint for an assembly</span></span>](#AssemblyHint)

- [<span data-ttu-id="4b8fc-229">延後處理</span><span class="sxs-lookup"><span data-stu-id="4b8fc-229">Deferred processing</span></span>](#Deferred)

- [<span data-ttu-id="4b8fc-230">原生映像和 JIT 編譯</span><span class="sxs-lookup"><span data-stu-id="4b8fc-230">Native images and JIT compilation</span></span>](#JITCompilation)

  - [<span data-ttu-id="4b8fc-231">無效的映像</span><span class="sxs-lookup"><span data-stu-id="4b8fc-231">Invalid images</span></span>](#InvalidImages)

- [<span data-ttu-id="4b8fc-232">疑難排解</span><span class="sxs-lookup"><span data-stu-id="4b8fc-232">Troubleshooting</span></span>](#Troubleshooting)

  - [<span data-ttu-id="4b8fc-233">組件繫結記錄檔檢視器</span><span class="sxs-lookup"><span data-stu-id="4b8fc-233">Assembly Binding Log Viewer</span></span>](#Fusion)

  - [<span data-ttu-id="4b8fc-234">JITCompilationStart Managed 偵錯助理</span><span class="sxs-lookup"><span data-stu-id="4b8fc-234">The JITCompilationStart managed debugging assistant</span></span>](#MDA)

  - [<span data-ttu-id="4b8fc-235">選擇不產生原生映像</span><span class="sxs-lookup"><span data-stu-id="4b8fc-235">Opting out of native image generation</span></span>](#OptOut)

<a name="Scenarios"></a>

## <a name="generating-images-for-----different-scenarios"></a><span data-ttu-id="4b8fc-236">產生不同情節的映像</span><span class="sxs-lookup"><span data-stu-id="4b8fc-236">Generating images for     different scenarios</span></span>

<span data-ttu-id="4b8fc-237">當您產生組件的原生映像後，執行階段會在每次執行組件時自動嘗試找出並且使用這個原生映像。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-237">After you have generated a native image for an assembly, the runtime automatically attempts to locate and use this native   image each time it runs the assembly.</span></span> <span data-ttu-id="4b8fc-238">視使用情節而定，可以產生多個映像。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-238">Multiple images can be generated, depending on usage scenarios.</span></span>

<span data-ttu-id="4b8fc-239">例如，如果您是在偵錯或分析情節中執行組件，則執行階段會尋找以 `/Debug` 或 `/Profile` 選項產生的原生映像。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-239">For example, if you run an assembly in a debugging or profiling scenario, the runtime looks for a native image that was generated with the `/Debug` or `/Profile` options.</span></span> <span data-ttu-id="4b8fc-240">如果執行階段找不到符合的原生映像，就會還原成標準 JIT 編譯。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-240">If it is unable to find a matching native image, the runtime reverts to standard JIT compilation.</span></span> <span data-ttu-id="4b8fc-241">偵錯原生映像的唯一方法是以 `/Debug` 選項建立原生映像。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-241">The only way to debug native images is to create a native image with the `/Debug` option.</span></span>

<span data-ttu-id="4b8fc-242">`uninstall` 動作也會辨識情節，因此您可以解除安裝所有情節或只解除安裝選取的情節。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-242">The `uninstall` action also recognize scenarios, so you can uninstall all scenarios or only selected scenarios.</span></span>

<a name="WhenToUse"></a>

## <a name="determining-when-to-use-native-images"></a><span data-ttu-id="4b8fc-243">判斷使用原生映像的時機</span><span class="sxs-lookup"><span data-stu-id="4b8fc-243">Determining when to Use native images</span></span>

<span data-ttu-id="4b8fc-244">原生映像可提供兩個區域的效能改進：改進記憶體使用和減少啟動時間。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-244">Native images can provide performance improvements in two areas: improved memory use and reduced startup time.</span></span>

> [!NOTE]
> <span data-ttu-id="4b8fc-245">原生映像的效能取決於下列數個讓分析更加困難的因素：程式碼和資料存取模式、跨模組界限中產生多少個呼叫以及其他應用程式已載入多少個相依性等等。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-245">Performance of native images depends on a number of factors that make analysis difficult, such as code and data access patterns, how many calls are made across module boundaries, and how many dependencies have already been loaded by other applications.</span></span> <span data-ttu-id="4b8fc-246">判斷原生映像是否對您的應用程式帶來好處的唯一方法是在主要部署情節中，仔細地度量效能。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-246">The only way to determine whether native images benefit your application is by careful performance measurements in your key deployment scenarios.</span></span>

<a name="Memory"></a>

### <a name="improved-memory-use"></a><span data-ttu-id="4b8fc-247">改進記憶體使用</span><span class="sxs-lookup"><span data-stu-id="4b8fc-247">Improved memory use</span></span>

<span data-ttu-id="4b8fc-248">在處理序之間共用程式碼時，原生映像可以顯著地改進記憶體使用。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-248">Native images can significantly improve memory use when code is shared between processes.</span></span> <span data-ttu-id="4b8fc-249">原生映像是 Windows PE 檔案，因此多個處理序可以共用 .dll 檔案的單一複本；相反地，JIT 編譯器產生的機器碼則會存放在專用記憶體中，並且無法共用。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-249">Native images are Windows PE files, so a single copy of a .dll file can be shared by multiple processes; by contrast, native code produced by the JIT compiler is stored in private memory and cannot be shared.</span></span>

<span data-ttu-id="4b8fc-250">在終端機服務下執行的應用程式也可以從共用字碼頁獲益。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-250">Applications that are run under terminal services can also benefit from shared code pages.</span></span>

<span data-ttu-id="4b8fc-251">此外，不載入 JIT 編譯器可為每個應用程式執行個體節省固定量的記憶體。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-251">In addition, not loading the JIT compiler saves a fixed amount of memory for each application instance.</span></span>

<a name="Startup"></a>

### <a name="faster-application-startup"></a><span data-ttu-id="4b8fc-252">應用程式啟動較快</span><span class="sxs-lookup"><span data-stu-id="4b8fc-252">Faster application startup</span></span>

<span data-ttu-id="4b8fc-253">以 Ngen.exe 先行編譯組件可以改進某些應用程式的啟動時間。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-253">Precompiling assemblies with Ngen.exe can improve the startup time for some applications.</span></span> <span data-ttu-id="4b8fc-254">一般來說，在應用程式共用元件組件時就會獲益，這是因為啟動第一個應用程式之後，就已對後續的應用程式載入共用的元件。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-254">In general, gains can be made when applications share component assemblies because after the first application has been started the shared components are already loaded for subsequent applications.</span></span> <span data-ttu-id="4b8fc-255">冷啟動 (必須從硬碟載入應用程式中的所有組件) 的優點沒有像從原生映像中載入那麼多，因為硬碟存取時間就具決定性。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-255">Cold startup, in which all the assemblies in an application must be loaded from the hard disk, does not benefit as much from native images because the hard disk access time predominates.</span></span>

<span data-ttu-id="4b8fc-256">硬式繫結會影響啟動時間，這是因為硬式繫結至主應用程式組件的所有映像都必須在同時間載入。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-256">Hard binding can affect startup time, because all images that are hard bound to the main application assembly must be loaded at the same time.</span></span>

> [!NOTE]
> <span data-ttu-id="4b8fc-257">在 [!INCLUDE[net_v35SP1_long](../../../includes/net-v35sp1-long-md.md)] 之前，您應該將共用、強式名稱的元件放在全域組件快取中，因為載入器會針對不在全域組件快取中的強式名稱組件執行額外驗證，進而有效地消除使用原生映像所取得的任何啟動時間改進。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-257">Before the [!INCLUDE[net_v35SP1_long](../../../includes/net-v35sp1-long-md.md)], you should put shared, strong-named components in the global assembly cache, because the loader performs extra validation on strong-named assemblies that are not in the global assembly cache, effectively eliminating any improvement in startup time gained by using native images.</span></span> <span data-ttu-id="4b8fc-258">在 [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] 中引入的最佳化移除額外的驗證。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-258">Optimizations that were introduced in the [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] removed the extra validation.</span></span>

<a name="UsageSummary"></a>

### <a name="summary-of-usage-considerations"></a><span data-ttu-id="4b8fc-259">使用方式考量摘要</span><span class="sxs-lookup"><span data-stu-id="4b8fc-259">Summary of usage considerations</span></span>

<span data-ttu-id="4b8fc-260">下列一般考量和應用程式考量可以幫助您決定是否要進行評估應用程式的原生映像：</span><span class="sxs-lookup"><span data-stu-id="4b8fc-260">The following general considerations and application considerations may assist you in deciding whether to undertake the effort of evaluating native images for your application:</span></span>

- <span data-ttu-id="4b8fc-261">原生映像的載入速度比 MSIL 快，因為原生映像可以減少許多不必要的啟動活動 (例如 JIT 編譯和類型安全驗證)。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-261">Native images load faster than MSIL because they eliminate the need for many startup activities, such as JIT compilation and type-safety verification.</span></span>

- <span data-ttu-id="4b8fc-262">由於不需要 JIT 編譯器，原生映像只需要較小的初始工作集。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-262">Native images require a smaller initial working set because there is no need for the JIT compiler.</span></span>

- <span data-ttu-id="4b8fc-263">原生映像可啟用處理序之間的程式碼共用。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-263">Native images enable code sharing between processes.</span></span>

- <span data-ttu-id="4b8fc-264">原生映像所需的硬碟空間比 MSIL 組件更多，而且可能需要相當長的時間才能產生。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-264">Native images require more hard disk space than MSIL assemblies and may require considerable time to generate.</span></span>

- <span data-ttu-id="4b8fc-265">必須維護原生映像。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-265">Native images must be maintained.</span></span>

  - <span data-ttu-id="4b8fc-266">在為原始組件或它的其中一個相依性提供服務時，需要重新產生影像。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-266">Images need to be regenerated when the original assembly or one of its dependencies is serviced.</span></span>

  - <span data-ttu-id="4b8fc-267">單一組件可能需要多個原生映像，以供不同的應用程式或不同的情節使用。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-267">A single assembly may need multiple native images for use in different applications or different scenarios.</span></span> <span data-ttu-id="4b8fc-268">例如，兩個應用程式中的組態資訊可能會為相同的相依組件產生不同的繫結決策。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-268">For example, the configuration information in two applications might result in different binding decisions for the same dependent assembly.</span></span>

  - <span data-ttu-id="4b8fc-269">原生映像必須由系統管理員產生，也就是來自系統管理員 (Administrator) 群組中的 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-269">Native images must be generated by an administrator; that is, from a Windows account in the Administrators group.</span></span>

<span data-ttu-id="4b8fc-270">除了這些一般考量之外，在判斷原生映像是否可能提供效能優勢時，應用程式的本質也必須列入考慮：</span><span class="sxs-lookup"><span data-stu-id="4b8fc-270">In addition to these general considerations, the nature of your application must be considered when determining whether native images might provide a performance benefit:</span></span>

- <span data-ttu-id="4b8fc-271">如果應用程式是在使用許多共用元件的環境中執行，原生映像可允許多個處理序共用元件。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-271">If your application runs in an environment that uses many shared components, native images allow the components to be shared by multiple processes.</span></span>

- <span data-ttu-id="4b8fc-272">如果您的應用程式使用多個應用程式定義域，原生映像就可讓字碼頁跨定義域共用。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-272">If your application uses multiple application domains, native images allow code pages to be shared across domains.</span></span>

    > [!NOTE]
    > <span data-ttu-id="4b8fc-273">在 .NET Framework 1.0 和 1.1 版中，無法跨應用程式定義域共用原生映像。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-273">In the .NET Framework versions 1.0 and 1.1, native images cannot be shared across application domains.</span></span> <span data-ttu-id="4b8fc-274">這不是 2.0 (含) 以後版本的情況。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-274">This is not the case in version 2.0 or later.</span></span>

- <span data-ttu-id="4b8fc-275">如果將在終端伺服器下執行應用程式，則原生映像允許共用字碼頁。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-275">If your application will be run under Terminal Server, native images allow sharing of code pages.</span></span>

- <span data-ttu-id="4b8fc-276">大型應用程式通常可以透過編譯取得原生映像的優勢。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-276">Large applications generally benefit from compilation to native images.</span></span> <span data-ttu-id="4b8fc-277">小型應用程式通常就沒有差別。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-277">Small applications generally do not benefit.</span></span>

- <span data-ttu-id="4b8fc-278">若是長時間執行的應用程式，執行階段 JIT 編譯的執行效能要比原生映像稍微好一點 </span><span class="sxs-lookup"><span data-stu-id="4b8fc-278">For long-running applications, run-time JIT compilation performs slightly better than native images.</span></span> <span data-ttu-id="4b8fc-279">(硬式繫結在某種程度上可稍微緩和這個效能差異)。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-279">(Hard binding can mitigate this performance difference to some degree.)</span></span>

<a name="BaseAddresses"></a>

## <a name="importance-of-assembly-base-addresses"></a><span data-ttu-id="4b8fc-280">組件基底位址的重要性</span><span class="sxs-lookup"><span data-stu-id="4b8fc-280">Importance of assembly base addresses</span></span>

<span data-ttu-id="4b8fc-281">由於原生映像是 Windows PE 檔案，因此和其他可執行檔一樣會有重定基底的問題。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-281">Because native images are Windows PE files, they are subject to the same rebasing issues as other executable files.</span></span> <span data-ttu-id="4b8fc-282">重新配置所耗用的效能甚至會比使用硬式繫結來得多。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-282">The performance cost of relocation is even more pronounced if hard binding is employed.</span></span>

<span data-ttu-id="4b8fc-283">若要設定原生映像的基底位址 (Base Address)，請使用適當的編譯器選項以設定組件的基底位址。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-283">To set the base address for a native image, use the appropriate option of your compiler to set the base address for the assembly.</span></span> <span data-ttu-id="4b8fc-284">Ngen.exe 會對原生映像使用此基底位址。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-284">Ngen.exe uses this base address for the native image.</span></span>

> [!NOTE]
> <span data-ttu-id="4b8fc-285">原生映像會比它們的建立來源 Managed 組件更大。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-285">Native images are larger than the managed assemblies from which they were created.</span></span> <span data-ttu-id="4b8fc-286">必須計算基底位址是否允許較大的大小。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-286">Base addresses must be calculated to allow for these larger sizes.</span></span>

<span data-ttu-id="4b8fc-287">您可以使用 dumpbin.exe 這類工具，檢視原生映像偏好的基底位址。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-287">You can use a tool such as dumpbin.exe to view the preferred base address of a native image.</span></span>

<a name="HardBinding"></a>

## <a name="hard-binding"></a><span data-ttu-id="4b8fc-288">硬式繫結</span><span class="sxs-lookup"><span data-stu-id="4b8fc-288">Hard binding</span></span>

<span data-ttu-id="4b8fc-289">硬式繫結會增加原生映像的輸送量，並降低工作集的大小。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-289">Hard binding increases throughput and reduces working set size for native images.</span></span> <span data-ttu-id="4b8fc-290">硬式繫結的缺點是載入組件時，必須載入所有硬式繫結至組件的映像。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-290">The disadvantage of hard binding is that all the images that are hard bound to an assembly must be loaded when the assembly is loaded.</span></span> <span data-ttu-id="4b8fc-291">這樣會大量增加大型應用程式的啟動時間。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-291">This can significantly increase startup time for a large application.</span></span>

<span data-ttu-id="4b8fc-292">硬式繫結適用於在所有應用程式的重要效能情節中載入的相依性。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-292">Hard binding is appropriate for dependencies that are loaded in all your application's performance-critical scenarios.</span></span> <span data-ttu-id="4b8fc-293">使用原生映像時，仔細的效能度量是唯一能判斷硬式繫結是否改進您應用程式效能的方法。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-293">As with any aspect of native image use, careful performance measurements are the only way to determine whether hard binding improves your application's performance.</span></span>

<span data-ttu-id="4b8fc-294"><xref:System.Runtime.CompilerServices.DependencyAttribute> 和 <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> 屬性可讓您對 Ngen.exe 提供硬式繫結提示。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-294">The <xref:System.Runtime.CompilerServices.DependencyAttribute> and <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> attributes allow you to provide hard binding hints to Ngen.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="4b8fc-295">這些屬性是 Ngen.exe 的提示，而非命令。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-295">These attributes are hints to Ngen.exe, not commands.</span></span> <span data-ttu-id="4b8fc-296">使用這些屬性不會保證執行硬式繫結。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-296">Using them does not guarantee hard binding.</span></span> <span data-ttu-id="4b8fc-297">這些屬性的意義在以後的版本中可能會變更。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-297">The meaning of these attributes may change in future releases.</span></span>

<a name="DependencyHint"></a>

### <a name="specifying-a-binding-hint-for-a-dependency"></a><span data-ttu-id="4b8fc-298">指定相依性的繫結提示</span><span class="sxs-lookup"><span data-stu-id="4b8fc-298">Specifying a binding hint for a dependency</span></span>

<span data-ttu-id="4b8fc-299">將 <xref:System.Runtime.CompilerServices.DependencyAttribute> 套用至組件，表示可能會載入指定的相依性組件。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-299">Apply the <xref:System.Runtime.CompilerServices.DependencyAttribute> to an assembly to indicate the likelihood that a specified dependency will be loaded.</span></span> <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> <span data-ttu-id="4b8fc-300">表示硬式繫結適用，<xref:System.Runtime.CompilerServices.LoadHint.Default> 表示應該使用相依性的預設值，而 <xref:System.Runtime.CompilerServices.LoadHint.Sometimes> 表示硬式繫結不適用。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-300">indicates that hard binding is appropriate, <xref:System.Runtime.CompilerServices.LoadHint.Default> indicates that the default for the dependency should be used, and <xref:System.Runtime.CompilerServices.LoadHint.Sometimes> indicates that hard binding is not appropriate.</span></span>

<span data-ttu-id="4b8fc-301">在下列程式碼中，示範具有兩個相依性的組件屬性。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-301">The following code shows the attributes for an assembly that has two dependencies.</span></span> <span data-ttu-id="4b8fc-302">第一個相依性 (Assembly1) 是硬式繫結的適當候選，但第二個 (Assembly2) 則不是。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-302">The first dependency (Assembly1) is an appropriate candidate for hard binding, and the second (Assembly2) is not.</span></span>

```vb
Imports System.Runtime.CompilerServices
<Assembly:DependencyAttribute("Assembly1", LoadHint.Always)>
<Assembly:DependencyAttribute("Assembly2", LoadHint.Sometimes)>
```

```csharp
using System.Runtime.CompilerServices;
[assembly:DependencyAttribute("Assembly1", LoadHint.Always)]
[assembly:DependencyAttribute("Assembly2", LoadHint.Sometimes)]
```

```cpp
using namespace System::Runtime::CompilerServices;
[assembly:DependencyAttribute("Assembly1", LoadHint.Always)];
[assembly:DependencyAttribute("Assembly2", LoadHint.Sometimes)];
```

<span data-ttu-id="4b8fc-303">組件名稱不包含副檔名。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-303">The assembly name does not include the file name extension.</span></span> <span data-ttu-id="4b8fc-304">可以使用顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-304">Display names can be used.</span></span>

<a name="AssemblyHint"></a>

### <a name="specifying-a-default-binding-hint-for-an-assembly"></a><span data-ttu-id="4b8fc-305">指定組件的預設繫結提示</span><span class="sxs-lookup"><span data-stu-id="4b8fc-305">Specifying a default binding hint for an assembly</span></span>

<span data-ttu-id="4b8fc-306">只有其中具有組件相依性的應用程式將立即且經常使用組件時，才會需要用到預設繫結提示。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-306">Default binding hints are only needed for assemblies that will be used immediately and frequently by any application that has a dependency on them.</span></span> <span data-ttu-id="4b8fc-307">將具有 <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> 的 <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> 套用至這類組件，以指定應該使用硬式繫結。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-307">Apply the <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> with <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> to such assemblies to specify that hard binding should be used.</span></span>

> [!NOTE]
> <span data-ttu-id="4b8fc-308">沒有理由要將 <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> 套用至不屬於這個分類的 .dll 組件，因為套用具有非 <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> 值的屬性，其作用就和完全不套用屬性一樣。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-308">There is no reason to apply <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> to .dll assemblies that do not fall into this category, because applying the attribute with any value other than <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> has the same effect as not applying the attribute at all.</span></span>

<span data-ttu-id="4b8fc-309">Microsoft 使用 <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> 指定硬式繫結是 .NET Framework 中極少數組件的預設值，例如 mscorlib.dll。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-309">Microsoft uses the <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> to specify that hard binding is the default for a very small number of assemblies in the .NET Framework, such as mscorlib.dll.</span></span>

<a name="Deferred"></a>

## <a name="deferred-processing"></a><span data-ttu-id="4b8fc-310">延後處理</span><span class="sxs-lookup"><span data-stu-id="4b8fc-310">Deferred processing</span></span>

<span data-ttu-id="4b8fc-311">對極大型的應用程式產生原生映像會需要相當長的時間。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-311">Generation of native images for a very large application can take considerable time.</span></span> <span data-ttu-id="4b8fc-312">同樣地，變更共用元件或變更電腦設定可能都需要更新許多原生映像。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-312">Similarly, changes to a shared component or changes to computer settings might require many native images to be updated.</span></span> <span data-ttu-id="4b8fc-313">`install` 和 `update` 動作具有 `/queue` 選項，可將原生映像服務的延後執行作業加入佇列。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-313">The `install` and `update` actions have a `/queue` option that queues the operation for deferred execution by the native image service.</span></span> <span data-ttu-id="4b8fc-314">此外，Ngen.exe 具有提供部分服務控制權的 `queue` 和 `executeQueuedItems` 動作。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-314">In addition, Ngen.exe has `queue` and `executeQueuedItems` actions that provide some control over the service.</span></span> <span data-ttu-id="4b8fc-315">如需詳細資訊，請參閱[原生映像服務](#native-image-service)。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-315">For more information, see [Native Image Service](#native-image-service).</span></span>

<a name="JITCompilation"></a>

## <a name="native-images-and-jit-compilation"></a><span data-ttu-id="4b8fc-316">原生映像和 JIT 編譯</span><span class="sxs-lookup"><span data-stu-id="4b8fc-316">Native images and JIT compilation</span></span>

<span data-ttu-id="4b8fc-317">如果 Ngen.exe 在組件上遇到它無法產生的任何方法，就會將其從原生映像排除。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-317">If Ngen.exe encounters any methods in an assembly that it cannot generate, it excludes them from the native image.</span></span> <span data-ttu-id="4b8fc-318">當執行階段執行這個組件時，它將會對這些沒有包括在原生映像中的方法還原成 JIT 編譯。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-318">When the runtime executes this assembly, it reverts to JIT compilation for the methods that were not included in the native image.</span></span>

<span data-ttu-id="4b8fc-319">此外，如果已升級組件，或者映像因任何原因而失效，都不會使用原生映像。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-319">In addition, native images are not used if the assembly has been upgraded, or if the image has been invalidated for any reason.</span></span>

<a name="InvalidImages"></a>

### <a name="invalid-images"></a><span data-ttu-id="4b8fc-320">無效的映像</span><span class="sxs-lookup"><span data-stu-id="4b8fc-320">Invalid images</span></span>

<span data-ttu-id="4b8fc-321">當您使用 Ngen.exe 建立組件的原生映像時，輸出會依您指定的命令列選項和電腦上的特定設定而有所不同。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-321">When you use Ngen.exe to create a native image of an assembly, the output depends upon the command-line options that you specify and certain settings on your computer.</span></span> <span data-ttu-id="4b8fc-322">這些設定包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="4b8fc-322">These settings include the following:</span></span>

- <span data-ttu-id="4b8fc-323">.NET Framework 的版本。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-323">The version of the .NET Framework.</span></span>

- <span data-ttu-id="4b8fc-324">如果是從 Windows 9x 系列變更到 Windows NT 系列，則表示作業系統的版本。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-324">The version of the operating system, if the change is from the Windows 9x family to the Windows NT family.</span></span>

- <span data-ttu-id="4b8fc-325">組件的確切識別 (重新編譯會變更識別)。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-325">The exact identity of the assembly (recompilation changes identity).</span></span>

- <span data-ttu-id="4b8fc-326">這個組件所參考之所有組件的確切識別 (重新編譯會變更識別)。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-326">The exact identity of all assemblies that the assembly references (recompilation changes identity).</span></span>

- <span data-ttu-id="4b8fc-327">安全性因素。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-327">Security factors.</span></span>

<span data-ttu-id="4b8fc-328">Ngen.exe 會在產生原生映像時記錄這項資訊。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-328">Ngen.exe records this information when it generates a native image.</span></span> <span data-ttu-id="4b8fc-329">當您執行組件時，執行階段會尋找由符合電腦目前執行環境之選項和設定所產生的原生映像。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-329">When you execute an assembly, the runtime looks for the native image generated with options and settings that match the computer's current environment.</span></span> <span data-ttu-id="4b8fc-330">如果找不到符合的原生映像，執行階段就會還原成組件的 JIT 編譯。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-330">The runtime reverts to JIT compilation of an assembly if it cannot find a matching native image.</span></span> <span data-ttu-id="4b8fc-331">下列對電腦設定和環境的變更會使原生映像變成無效：</span><span class="sxs-lookup"><span data-stu-id="4b8fc-331">The following changes to a computer's settings and environment cause native images to become invalid:</span></span>

- <span data-ttu-id="4b8fc-332">.NET Framework 的版本。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-332">The version of the .NET Framework.</span></span>

     <span data-ttu-id="4b8fc-333">如果您對 .NET Framework 套用更新，則使用 Ngen.exe 建立的所有原生映像都會變成無效。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-333">If you apply an update to the .NET Framework, all native images that you have created using Ngen.exe become invalid.</span></span> <span data-ttu-id="4b8fc-334">因此，.NET Framework 的所有更新都會執行 `Ngen Update` 命令，以確保重新產生所有的原生映像。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-334">For this reason, all updates of the .NET Framework execute the `Ngen Update` command, to ensure that all native images are regenerated.</span></span> <span data-ttu-id="4b8fc-335">.NET Framework 會自動為它所安裝的 .NET Framework 程式庫建立新的原生映像。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-335">The .NET Framework automatically creates new native images for the .NET Framework libraries that it installs.</span></span>

- <span data-ttu-id="4b8fc-336">如果是從 Windows 9x 系列變更為 Windows NT 系列，則表示作業系統的版本。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-336">The version of the operating system, if the change is from the Windows 9x family to the Windows NT family.</span></span>

     <span data-ttu-id="4b8fc-337">例如，如果電腦上執行的作業系統版本從 Windows 98 變更為 Windows XP，則存放在原生映像快取中的所有原生映像都會變成無效。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-337">For example, if the version of the operating system running on a computer changes from Windows 98 to Windows XP, all native images stored in the native image cache become invalid.</span></span> <span data-ttu-id="4b8fc-338">但是，如果作業系統從 Windows 2000 變更為 Windows XP，則映像不會失效。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-338">However, if the operating system changes from Windows 2000 to Windows XP, the images are not invalidated.</span></span>

- <span data-ttu-id="4b8fc-339">組件的確切識別。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-339">The exact identity of the assembly.</span></span>

     <span data-ttu-id="4b8fc-340">如果您重新編譯某個組件，這個組件對應的原生映像會變成無效。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-340">If you recompile an assembly, the assembly's corresponding native image becomes invalid.</span></span>

- <span data-ttu-id="4b8fc-341">這個組件所參考之任一組件的確切識別。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-341">The exact identity of any assemblies the assembly references.</span></span>

     <span data-ttu-id="4b8fc-342">如果您更新 Managed 組件，所有直接或間接以該組件為依據的原生映像都會變成無效，必須重新產生。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-342">If you update a managed assembly, all native images that directly or indirectly depend on that assembly become invalid and need to be regenerated.</span></span> <span data-ttu-id="4b8fc-343">這其中包括一般性的參考和硬式繫結的相依性。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-343">This includes both ordinary references and hard-bound dependencies.</span></span> <span data-ttu-id="4b8fc-344">每當套用軟體更新時，安裝程式都應執行 `Ngen Update` 命令，以確保重新產生所有相依的原生映像。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-344">Whenever a software update is applied, the installation program should execute an `Ngen Update` command to ensure that all dependent native images are regenerated.</span></span>

- <span data-ttu-id="4b8fc-345">安全性因素。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-345">Security factors.</span></span>

     <span data-ttu-id="4b8fc-346">變更電腦安全性原則，以限制先前對組件允許的使用權限，會使該組件先前已編譯的原生映像變成無效。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-346">Changing machine security policy to restrict permissions previously granted to an assembly can cause a previously compiled native image for that assembly to become invalid.</span></span>

     <span data-ttu-id="4b8fc-347">如需 Common Language Runtime 如何管理程式碼存取安全性，以及如何使用權限的詳細資訊，請參閱[程式碼存取安全性](../../../docs/framework/misc/code-access-security.md)。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-347">For detailed information about how the common language runtime administers code access security and how to use permissions, see [Code Access Security](../../../docs/framework/misc/code-access-security.md).</span></span>

<a name="Troubleshooting"></a>

## <a name="troubleshooting"></a><span data-ttu-id="4b8fc-348">疑難排解</span><span class="sxs-lookup"><span data-stu-id="4b8fc-348">Troubleshooting</span></span>

<span data-ttu-id="4b8fc-349">下列疑難排解主題可讓您查看正在使用的原生映像以及您的應用程式不能使用的原生映像、判斷 JIT 編譯器開始編譯方法的時機，以及顯示如何選擇不編譯所指定方法的原生映像。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-349">The following troubleshooting topics allow you to see which native images are being used and which cannot be used by your application, to determine when the JIT compiler starts to compile a method, and shows how to opt out of native image compilation of specified methods.</span></span>

<a name="Fusion"></a>

### <a name="assembly-binding-log-viewer"></a><span data-ttu-id="4b8fc-350">組件繫結記錄檔檢視器</span><span class="sxs-lookup"><span data-stu-id="4b8fc-350">Assembly Binding Log Viewer</span></span>

<span data-ttu-id="4b8fc-351">若要確認您的應用程式正在使用原生映像，可以使用 [Fuslogvw.exe (組件繫結記錄檔檢視器)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-351">To confirm that native images are being used by your application, you can use the [Fuslogvw.exe (Assembly Binding Log Viewer)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md).</span></span> <span data-ttu-id="4b8fc-352">在繫結記錄檔檢視器視窗的 [記錄檔類別] 方塊中，選取 [原生映像]。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-352">Select **Native Images** in the **Log Categories** box on the binding log viewer window.</span></span> <span data-ttu-id="4b8fc-353">Fuslogvw.exe 會提供為何會拒絕原生映像的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-353">Fuslogvw.exe provides information about why a native image was rejected.</span></span>

<a name="MDA"></a>

### <a name="the-jitcompilationstart-managed-debugging-assistant"></a><span data-ttu-id="4b8fc-354">JITCompilationStart Managed 偵錯助理</span><span class="sxs-lookup"><span data-stu-id="4b8fc-354">The JITCompilationStart managed debugging assistant</span></span>

<span data-ttu-id="4b8fc-355">您可以使用 [jitCompilationStart](../../../docs/framework/debug-trace-profile/jitcompilationstart-mda.md) Managed 偵錯助理 (MDA)，判斷 JIT 編譯器開始編譯函式的時間。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-355">You can use the [jitCompilationStart](../../../docs/framework/debug-trace-profile/jitcompilationstart-mda.md) managed debugging assistant (MDA) to determine when the JIT compiler starts to compile a function.</span></span>

<a name="OptOut"></a>

### <a name="opting-out-of-native-image-generation"></a><span data-ttu-id="4b8fc-356">選擇不產生原生映像</span><span class="sxs-lookup"><span data-stu-id="4b8fc-356">Opting out of native image generation</span></span>

<span data-ttu-id="4b8fc-357">在某些情況下，NGen.exe 可能無法產生特定方法的原生映像，或者，您可能會偏好使用 JIT 編譯的方法，而不是編譯成原生映像。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-357">In some cases, NGen.exe may have difficulty generating a native image for a specific method, or you may prefer that the method be JIT compiled rather then compiled to a native image.</span></span> <span data-ttu-id="4b8fc-358">在此情況下，您可以使用 `System.Runtime.BypassNGenAttribute` 屬性，防止 NGen.exe 產生特定方法的原生映像。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-358">In this case, you can use the `System.Runtime.BypassNGenAttribute` attribute to prevent NGen.exe from generating a native image for a particular method.</span></span> <span data-ttu-id="4b8fc-359">如果您不想要將方法的程式碼包含在原生映像中，則必須將此屬性個別套用至這類方法。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-359">The attribute must be applied individually to each method whose code you do not want to include in the native image.</span></span> <span data-ttu-id="4b8fc-360">NGen.exe 會辨識此屬性，而且不會在原生影像中產生對應方法的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-360">NGen.exe recognizes the attribute and does not generate code in the native image for the corresponding method.</span></span>

<span data-ttu-id="4b8fc-361">不過，請注意，`BypassNGenAttribute` 未定義為 .NET Framework 類別庫中的類型。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-361">Note, however, that `BypassNGenAttribute` is not defined as a type in the .NET Framework Class Library.</span></span> <span data-ttu-id="4b8fc-362">若要取用您程式碼中的屬性，您必須先定義它，如下所示︰</span><span class="sxs-lookup"><span data-stu-id="4b8fc-362">In order to consume the attribute in your code, you must first define it as follows:</span></span>

[!code-csharp[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#1)]
[!code-vb[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#1)]

<span data-ttu-id="4b8fc-363">您接著可以根據方法來套用屬性。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-363">You can then apply the attribute on a per-method basis.</span></span> <span data-ttu-id="4b8fc-364">下列範例指示原生映像產生器不應該產生 `ExampleClass.ToJITCompile` 方法的原生影像。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-364">The following example instructs the Native Image Generator that it should not generate a native image for the `ExampleClass.ToJITCompile` method.</span></span>

[!code-csharp[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#2)]
[!code-vb[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#2)]

## <a name="examples"></a><span data-ttu-id="4b8fc-365">範例</span><span class="sxs-lookup"><span data-stu-id="4b8fc-365">Examples</span></span>

<span data-ttu-id="4b8fc-366">下列命令會在目前的目錄中產生 `ClientApp.exe` 的原生映像，並在原生映像快取中安裝映像。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-366">The following command generates a native image for `ClientApp.exe`, located in the current directory, and installs the image in the native image cache.</span></span> <span data-ttu-id="4b8fc-367">如果組件有組態檔，Ngen.exe 就會使用它。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-367">If a configuration file exists for the assembly, Ngen.exe uses it.</span></span> <span data-ttu-id="4b8fc-368">此外，會針對 `ClientApp.exe` 參考的任何 .dll 檔案產生原生映像。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-368">In addition, native images are generated for any .dll files that `ClientApp.exe` references.</span></span>

```
ngen install ClientApp.exe
```

<span data-ttu-id="4b8fc-369">使用 Ngen.exe 安裝的映像也稱為根 (Root)。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-369">An image installed with Ngen.exe is also called a root.</span></span> <span data-ttu-id="4b8fc-370">根可以是應用程式或共用元件。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-370">A root can be an application or a shared component.</span></span>

<span data-ttu-id="4b8fc-371">下列命令會對指定路徑的 `MyAssembly.exe` 產生原生映像。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-371">The following command generates a native image for `MyAssembly.exe` with the specified path.</span></span>

```
ngen install c:\myfiles\MyAssembly.exe
```

<span data-ttu-id="4b8fc-372">尋找組件和它們的相依性時，Ngen.exe 使用的探查邏輯和通用語言執行平台所使用的一樣。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-372">When locating assemblies and their dependencies, Ngen.exe uses the same probing logic used by the common language runtime.</span></span> <span data-ttu-id="4b8fc-373">根據預設，包含 `ClientApp.exe` 的目錄會當做應用程式基底目錄使用，並且會在這個目錄中開始所有組件探查。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-373">By default, the directory that contains `ClientApp.exe` is used as the application base directory, and all assembly probing begins in this directory.</span></span> <span data-ttu-id="4b8fc-374">您可以使用 `/AppBase` 選項覆寫這個行為。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-374">You can override this behavior by using the `/AppBase` option.</span></span>

> [!NOTE]
> <span data-ttu-id="4b8fc-375">這是 .NET Framework 1.0 和 1.1 版之 Ngen.exe 行為的變更，其中的應用程式基底會設為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-375">This is a change from Ngen.exe behavior in the .NET Framework versions 1.0 and 1.1, where the application base is set to the current directory.</span></span>

<span data-ttu-id="4b8fc-376">組件可以擁有相依性，而不含參考，例如，當組件在使用 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> 方法載入 .dll 檔時。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-376">An assembly can have a dependency without a reference, for example if it loads a .dll file by using the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="4b8fc-377">您可以利用 `/ExeConfig` 選項，針對使用應用程式組件之組態資訊的這種 .dll 檔建立原生映像。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-377">You can create a native image for such a .dll file by using configuration information for the application assembly, with the `/ExeConfig` option.</span></span> <span data-ttu-id="4b8fc-378">下列命令會針對使用 `MyLib.dll,` 組態資訊的 `MyApp.exe` 產生原生映像。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-378">The following command generates a native image for `MyLib.dll,` using the configuration information from `MyApp.exe`.</span></span>

```
ngen install c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe
```

<span data-ttu-id="4b8fc-379">在移除應用程式時，不會移除以這種方式所安裝的組件。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-379">Assemblies installed in this way are not removed when the application is removed.</span></span>

<span data-ttu-id="4b8fc-380">若要解除安裝相依性，請使用安裝時所用的相同命令列選項。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-380">To uninstall a dependency, use the same command-line options that were used to install it.</span></span> <span data-ttu-id="4b8fc-381">下列命令會解除安裝上一個範例的 `MyLib.dll`。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-381">The following command uninstalls the `MyLib.dll` from the previous example.</span></span>

```
ngen uninstall c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe
```

<span data-ttu-id="4b8fc-382">若要在全域組件快取中建立組件的原生映像，請使用組件的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-382">To create a native image for an assembly in the global assembly cache, use the display name of the assembly.</span></span> <span data-ttu-id="4b8fc-383">例如：</span><span class="sxs-lookup"><span data-stu-id="4b8fc-383">For example:</span></span>

```
ngen install "ClientApp, Version=1.0.0.0, Culture=neutral,
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL"
```

<span data-ttu-id="4b8fc-384">NGen.exe 會對所安裝的每個情節產生不同的映像集。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-384">NGen.exe generates a separate set of images for each scenario you install.</span></span> <span data-ttu-id="4b8fc-385">例如，下列命令會安裝一般作業的完整原生映像集，再安裝另一個完整集供偵錯使用，然後針對程式碼剖析安裝第三個完整集：</span><span class="sxs-lookup"><span data-stu-id="4b8fc-385">For example, the following commands install a complete set of native images for normal operation, another complete set for debugging, and a third for profiling:</span></span>

```
ngen install MyApp.exe
ngen install MyApp.exe /debug
ngen install MyApp.exe /profile
```

### <a name="displaying-the-native-image-cache"></a><span data-ttu-id="4b8fc-386">顯示原生映像快取</span><span class="sxs-lookup"><span data-stu-id="4b8fc-386">Displaying the Native Image Cache</span></span>

<span data-ttu-id="4b8fc-387">一旦原生映像安裝在快取中，即可使用 Ngen.exe 顯示它們。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-387">Once native images are installed in the cache, they can be displayed using Ngen.exe.</span></span> <span data-ttu-id="4b8fc-388">下列命令會顯示原生映像快取中的所有原生映像。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-388">The following command displays all native images in the native image cache.</span></span>

```
ngen display
```

<span data-ttu-id="4b8fc-389">`display` 動作會先列出所有根組件，接下來是電腦上所有原生映像的清單。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-389">The `display` action lists all the root assemblies first, followed by a list of all the native images on the computer.</span></span>

<span data-ttu-id="4b8fc-390">使用組件的簡單名稱，僅顯示該組件的資訊。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-390">Use the simple name of an assembly to display information only for that assembly.</span></span> <span data-ttu-id="4b8fc-391">下列命令會顯示原生映像快取中所有符合部分名稱 `MyAssembly` 的原生映像、它們的相依性和所有在 `MyAssembly` 上具有相依性的根：</span><span class="sxs-lookup"><span data-stu-id="4b8fc-391">The following command displays all native images in the native image cache that match the partial name `MyAssembly`, their dependencies, and all roots that have a dependency on `MyAssembly`:</span></span>

```
ngen display MyAssembly
```

<span data-ttu-id="4b8fc-392">在升級共用元件之後，判斷 `update` 動作所造成的影響時，了解哪些根會相依於共用元件組件將很有幫助。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-392">Knowing what roots depend on a shared component assembly is useful in gauging the impact of an `update` action after the shared component is upgraded.</span></span>

<span data-ttu-id="4b8fc-393">如果指定組件的副檔名，您必須指定路徑或從包含組件的目錄執行 Ngen.exe：</span><span class="sxs-lookup"><span data-stu-id="4b8fc-393">If you specify an assembly's file extension, you must either specify the path or execute Ngen.exe from the directory containing the assembly:</span></span>

```
ngen display c:\myApps\MyAssembly.exe
```

<span data-ttu-id="4b8fc-394">下列命令會顯示原生映像快取中名稱為 `MyAssembly` 且版本為 1.0.0.0 的所有原生映像。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-394">The following command displays all native images in the native image cache with the name `MyAssembly` and the version 1.0.0.0.</span></span>

```
ngen display "myAssembly, version=1.0.0.0"
```

### <a name="updating-images"></a><span data-ttu-id="4b8fc-395">更新映像</span><span class="sxs-lookup"><span data-stu-id="4b8fc-395">Updating Images</span></span>

<span data-ttu-id="4b8fc-396">通常會在升級共用元件之後更新映像。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-396">Images are typically updated after a shared component has been upgraded.</span></span> <span data-ttu-id="4b8fc-397">若要更新已變更或已變更其相依性的所有原生映像，請使用 `update` 動作且不搭配任何引數。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-397">To update all native images that have changed, or whose dependencies have changed, use the `update` action with no arguments.</span></span>

```
ngen update
```

<span data-ttu-id="4b8fc-398">更新所有映像可能是耗時的處理。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-398">Updating all images can be a lengthy process.</span></span> <span data-ttu-id="4b8fc-399">您可以使用 `/queue` 選項，依原生映像服務將要執行的更新加入佇列。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-399">You can queue the updates for execution by the native image service by using the `/queue` option.</span></span> <span data-ttu-id="4b8fc-400">如需 `/queue` 選項和安裝優先權的詳細資訊，請參閱[原生映像服務](#native-image-service)。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-400">For more information on the `/queue` option and installation priorities, see [Native Image Service](#native-image-service).</span></span>

```
ngen update /queue
```

### <a name="uninstalling-images"></a><span data-ttu-id="4b8fc-401">解除安裝映像</span><span class="sxs-lookup"><span data-stu-id="4b8fc-401">Uninstalling Images</span></span>

<span data-ttu-id="4b8fc-402">Ngen.exe 會維護相依性清單，因此只有當相依於共用元件的所有組件已移除時，才會移除共用元件。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-402">Ngen.exe maintains a list of dependencies, so that shared components are removed only when all assemblies that depend on them have been removed.</span></span> <span data-ttu-id="4b8fc-403">此外，如果共用元件已安裝為根，則不會將它移除。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-403">In addition, a shared component is not removed if it has been installed as a root.</span></span>

<span data-ttu-id="4b8fc-404">下列命令會解除安裝根 `ClientApp.exe` 的所有情節：</span><span class="sxs-lookup"><span data-stu-id="4b8fc-404">The following command uninstalls all scenarios for the root `ClientApp.exe`:</span></span>

```
ngen uninstall ClientApp
```

<span data-ttu-id="4b8fc-405">`uninstall` 動作可以用來移除特定的情節。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-405">The `uninstall` action can be used to remove specific scenarios.</span></span> <span data-ttu-id="4b8fc-406">下列命令會解除安裝 `ClientApp.exe` 的所有偵錯情節：</span><span class="sxs-lookup"><span data-stu-id="4b8fc-406">The following command uninstalls all debug scenarios for `ClientApp.exe`:</span></span>

```
ngen uninstall ClientApp /debug
```

> [!NOTE]
> <span data-ttu-id="4b8fc-407">解除安裝 `/debug` 情節不會解除安裝情節 (同時包含 `/profile` 和</span><span class="sxs-lookup"><span data-stu-id="4b8fc-407">Uninstalling `/debug` scenarios does not uninstall a scenario that includes both `/profile` and</span></span> `/debug.`

<span data-ttu-id="4b8fc-408">下列命令會解除安裝 `ClientApp.exe` 特定版本的所有情節：</span><span class="sxs-lookup"><span data-stu-id="4b8fc-408">The following command uninstalls all scenarios for a specific version of `ClientApp.exe`:</span></span>

```
ngen uninstall "ClientApp, Version=1.0.0.0"
```

<span data-ttu-id="4b8fc-409">下列命令會解除安裝 `"ClientApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL",` 的所有情節，或僅解除安裝該組件的偵錯情節：</span><span class="sxs-lookup"><span data-stu-id="4b8fc-409">The following commands uninstall all scenarios for `"ClientApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL",` or just the debug scenario for that assembly:</span></span>

```
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL"
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL" /debug
```

<span data-ttu-id="4b8fc-410">搭配使用 `install` 動作時，提供副檔名需要從含有組件的目錄執行 Ngen.exe 或指定完整路徑。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-410">As with the `install` action, supplying an extension requires either executing Ngen.exe from the directory containing the assembly or specifying a full path.</span></span>

<span data-ttu-id="4b8fc-411">如需與原生映像服務相關的範例，請參閱[原生映像服務](#native-image-service)。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-411">For examples relating to the native image service, see [Native Image Service](#native-image-service).</span></span>

## <a name="native-image-task"></a><span data-ttu-id="4b8fc-412">原生映像工作</span><span class="sxs-lookup"><span data-stu-id="4b8fc-412">Native Image Task</span></span>

<span data-ttu-id="4b8fc-413">原生映像工作是產生及維護原生映像的 Windows 工作。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-413">The native image task is a Windows task that generates and maintains native images.</span></span> <span data-ttu-id="4b8fc-414">原生映像工作會自動為受支援的案例產生及回收原生映像。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-414">The native image task generates and reclaims native images automatically for supported scenarios.</span></span> <span data-ttu-id="4b8fc-415">它也可以讓安裝程式使用 [Ngen.exe (原生映像產生器)](../../../docs/framework/tools/ngen-exe-native-image-generator.md)，在延後的時間建立及更新原生映像。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-415">It also enables installers to use [Ngen.exe (Native Image Generator)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) to create and update native images at a deferred time.</span></span>

<span data-ttu-id="4b8fc-416">針對電腦上支援的每個 CPU 架構，會各註冊一次原生映像工作，以允許針對以各架構為目標的應用程式進行編譯：</span><span class="sxs-lookup"><span data-stu-id="4b8fc-416">The native image task is registered once for each CPU architecture supported on a computer, to allow compilation for applications that target each architecture:</span></span>

|<span data-ttu-id="4b8fc-417">工作名稱</span><span class="sxs-lookup"><span data-stu-id="4b8fc-417">Task name</span></span>|<span data-ttu-id="4b8fc-418">32 位元電腦</span><span class="sxs-lookup"><span data-stu-id="4b8fc-418">32-bit computer</span></span>|<span data-ttu-id="4b8fc-419">64 位元電腦</span><span class="sxs-lookup"><span data-stu-id="4b8fc-419">64-bit computer</span></span>|
|---------------|----------------------|----------------------|
|<span data-ttu-id="4b8fc-420">NET Framework NGEN v4.0.30319</span><span class="sxs-lookup"><span data-stu-id="4b8fc-420">NET Framework NGEN v4.0.30319</span></span>|<span data-ttu-id="4b8fc-421">是</span><span class="sxs-lookup"><span data-stu-id="4b8fc-421">Yes</span></span>|<span data-ttu-id="4b8fc-422">是</span><span class="sxs-lookup"><span data-stu-id="4b8fc-422">Yes</span></span>|
|<span data-ttu-id="4b8fc-423">NET Framework NGEN v4.0.30319 64</span><span class="sxs-lookup"><span data-stu-id="4b8fc-423">NET Framework NGEN v4.0.30319 64</span></span>|<span data-ttu-id="4b8fc-424">否</span><span class="sxs-lookup"><span data-stu-id="4b8fc-424">No</span></span>|<span data-ttu-id="4b8fc-425">是</span><span class="sxs-lookup"><span data-stu-id="4b8fc-425">Yes</span></span>|

<span data-ttu-id="4b8fc-426">在 Windows 8 或更新版本上執行時，可在 .NET Framework 4.5 和更新版本中使用原生映像工作。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-426">The native image task is available in the .NET Framework 4.5 and later versions, when running on Windows 8 or later.</span></span> <span data-ttu-id="4b8fc-427">在舊版 Windows 中，.NET Framework 會使用 [原生映像服務](#native-image-service)。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-427">On earlier versions of Windows, the .NET Framework uses the [Native Image Service](#native-image-service).</span></span>

### <a name="task-lifetime"></a><span data-ttu-id="4b8fc-428">工作存留期</span><span class="sxs-lookup"><span data-stu-id="4b8fc-428">Task Lifetime</span></span>

<span data-ttu-id="4b8fc-429">一般而言，Windows 工作排程器會在每天晚上電腦閒置時，開始原生映像工作。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-429">In general, the Windows Task Scheduler starts the native image task every night when the computer is idle.</span></span> <span data-ttu-id="4b8fc-430">此工作會檢查應用程式安裝程式佇列的任何延後工作、任何延後的原生映像更新要求，以及任何自動建立映像的工作。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-430">The task checks for any deferred work that is queued by application installers, any deferred native image update requests, and any automatic image creation.</span></span> <span data-ttu-id="4b8fc-431">此工作會完成未完成的工作項目，然後才關閉。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-431">The task completes outstanding work items and then shuts down.</span></span> <span data-ttu-id="4b8fc-432">如果電腦在工作執行時停止閒置，該工作就會停止。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-432">If the computer stops being idle while the task is running, the task stops.</span></span>

<span data-ttu-id="4b8fc-433">您也可以透過工作排程器 UI，或是透過手動呼叫 NGen.exe，以手動啟動原生映像工作。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-433">You can also start the native image task manually through the Task Scheduler UI or through manual calls to NGen.exe.</span></span> <span data-ttu-id="4b8fc-434">如果是透過上述其中一種方法來啟動工作，即使電腦不再閒置，還是會繼續執行該工作。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-434">If the task is started through either of these methods, it will continue running when the computer is no longer idle.</span></span> <span data-ttu-id="4b8fc-435">使用 NGen.exe 手動建立的映像會列為優先順序，以為應用程式安裝程式啟用可預期的行為。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-435">Images created manually by using NGen.exe are prioritized to enable predictable behavior for application installers.</span></span>

## <a name="native-image-service"></a><span data-ttu-id="4b8fc-436">原生映像服務</span><span class="sxs-lookup"><span data-stu-id="4b8fc-436">Native Image Service</span></span>

<span data-ttu-id="4b8fc-437">原生映像服務是產生及維護原生映像的 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-437">The native image service is a Windows service that generates and maintains native images.</span></span> <span data-ttu-id="4b8fc-438">原生映像服務可讓開發人員將原生映像的安裝和更新延後到電腦閒置時的時段。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-438">The native image service allows the developer to defer the installation and update of native images to periods when the computer is idle.</span></span>

<span data-ttu-id="4b8fc-439">一般來說，會由安裝程式 (installer) 為應用程式或更新啟始原生映像服務。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-439">Normally, the native image service is initiated by the installation program (installer) for an application or update.</span></span> <span data-ttu-id="4b8fc-440">針對優先順序 3 的動作，此服務會在電腦閒置期間執行。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-440">For priority 3 actions, the service executes during idle time on the computer.</span></span> <span data-ttu-id="4b8fc-441">此服務會儲存其狀態，而且必要時，可以在多次重新開機後再繼續。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-441">The service saves its state and is capable of continuing through multiple reboots if necessary.</span></span> <span data-ttu-id="4b8fc-442">多個影像編譯可排入佇列。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-442">Multiple image compilations can be queued.</span></span>

<span data-ttu-id="4b8fc-443">此服務也會與手動 Ngen.exe 命令互動。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-443">The service also interacts with the manual Ngen.exe command.</span></span> <span data-ttu-id="4b8fc-444">手動命令優先於背景活動。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-444">Manual commands take precedence over background activity.</span></span>

> [!NOTE]
> <span data-ttu-id="4b8fc-445">在 Windows Vista 上，為原生映像服務顯示的名稱是 "Microsoft.NET Framework NGEN v2.0.50727_X86" 或 "Microsoft.NET Framework NGEN v2.0.50727_X64"。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-445">On Windows Vista, the name displayed for the native image service is "Microsoft.NET Framework NGEN v2.0.50727_X86" or "Microsoft.NET Framework NGEN v2.0.50727_X64".</span></span> <span data-ttu-id="4b8fc-446">在所有舊版 Microsoft Windows 上，名稱為「.NET 執行階段最佳化服務  v2.0.50727_X86」或「.NET 執行階段最佳化服務  v2.0.50727_X64」。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-446">On all earlier versions of Microsoft Windows, the name is ".NET Runtime Optimization Service v2.0.50727_X86" or ".NET Runtime Optimization Service v2.0.50727_X64".</span></span>

### <a name="launching-deferred-operations"></a><span data-ttu-id="4b8fc-447">啟動延後的作業</span><span class="sxs-lookup"><span data-stu-id="4b8fc-447">Launching Deferred Operations</span></span>

<span data-ttu-id="4b8fc-448">在開始安裝或升級之前，建議先暫停服務。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-448">Before beginning an installation or upgrade, pausing the service is recommended.</span></span> <span data-ttu-id="4b8fc-449">這樣可以確保當安裝程式正在複製檔案或是在全域組件快取中放置組件時，該服務不會執行。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-449">This ensures that the service does not execute while the installer is copying files or putting assemblies in the global assembly cache.</span></span> <span data-ttu-id="4b8fc-450">下列 Ngen.exe 命令列會暫停服務：</span><span class="sxs-lookup"><span data-stu-id="4b8fc-450">The following Ngen.exe command line pauses the service:</span></span>

```
ngen queue pause
```

<span data-ttu-id="4b8fc-451">當所有延後的作業都排入佇列時，下列命令可讓服務繼續：</span><span class="sxs-lookup"><span data-stu-id="4b8fc-451">When all deferred operations have been queued, the following command allows the service to resume:</span></span>

```
ngen queue continue
```

<span data-ttu-id="4b8fc-452">若要在安裝新應用程式或是更新共用元件時，延後產生原生映像，請使用 `/queue` 選項搭配 `install` 或 `update` 動作。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-452">To defer native image generation when installing a new application or when updating a shared component, use the `/queue` option with the `install` or `update` actions.</span></span> <span data-ttu-id="4b8fc-453">下列 Ngen.exe 命令列會為共用元件安裝原生映像，並針對可能受影響的所有根目錄執行更新：</span><span class="sxs-lookup"><span data-stu-id="4b8fc-453">The following Ngen.exe command lines install a native image for a shared component and perform an update of all roots that may have been affected:</span></span>

```
ngen install MyComponent /queue
ngen update /queue
```

<span data-ttu-id="4b8fc-454">`update` 動作會重新產生已經失效的所有原生映像，而不只是使用 `MyComponent` 的那些原生映像。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-454">The `update` action regenerates all native images that have been invalidated, not just those that use `MyComponent`.</span></span>

<span data-ttu-id="4b8fc-455">如果您的應用程式包含許多根目錄，您可以控制延後動作的優先順序。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-455">If your application consists of many roots, you can control the priority of the deferred actions.</span></span> <span data-ttu-id="4b8fc-456">下列命令會將三個根目錄的安裝排入佇列。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-456">The following commands queue the installation of three roots.</span></span> `Assembly1` <span data-ttu-id="4b8fc-457">會先安裝，而不會等到閒置時間。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-457">is installed first, without waiting for idle time.</span></span> `Assembly2` <span data-ttu-id="4b8fc-458">也是不會等到閒置時間，但要等到所有優先權 1 動作都完成之後才安裝。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-458">is also installed without waiting for idle time, but after all priority 1 actions have completed.</span></span> `Assembly3` <span data-ttu-id="4b8fc-459">則會在服務偵測到電腦閒置時安裝。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-459">is installed when the service detects that the computer is idle.</span></span>

```
ngen install Assembly1 /queue:1
ngen install Assembly2 /queue:2
ngen install Assembly3 /queue:3
```

<span data-ttu-id="4b8fc-460">您可以使用 `executeQueuedItems` 動作，強制佇列的動作同步執行。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-460">You can force queued actions to occur synchronously by using the `executeQueuedItems` action.</span></span> <span data-ttu-id="4b8fc-461">如果您提供選擇性的優先權，這個動作只會影響具有相等或較低優先權的佇列動作。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-461">If you supply the optional priority, this action affects only the queued actions that have equal or lower priority.</span></span> <span data-ttu-id="4b8fc-462">預設優先權為 3，因此下列 Ngen.exe 命令會立即處理所有佇列的動作，並且在完成之前都不會傳回：</span><span class="sxs-lookup"><span data-stu-id="4b8fc-462">The default priority is 3, so the following Ngen.exe command processes all queued actions immediately, and does not return until they are finished:</span></span>

```
ngen executeQueuedItems
```

<span data-ttu-id="4b8fc-463">同步命令是由 Ngen.exe 執行，而且不會使用原生映像服務。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-463">Synchronous commands are executed by Ngen.exe and do not use the native image service.</span></span> <span data-ttu-id="4b8fc-464">您可以在原生映像服務執行時，使用 Ngen.exe 來執行動作。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-464">You can execute actions using Ngen.exe while the native image service is running.</span></span>

### <a name="service-shutdown"></a><span data-ttu-id="4b8fc-465">服務關閉</span><span class="sxs-lookup"><span data-stu-id="4b8fc-465">Service Shutdown</span></span>

<span data-ttu-id="4b8fc-466">在執行包含 `/queue` 選項的 Ngen.exe 命令來啟始服務之後，服務會在背景執行，直到所有動作完成為止。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-466">After being initiated by the execution of an Ngen.exe command that includes the `/queue` option, the service runs in the background until all actions have been completed.</span></span> <span data-ttu-id="4b8fc-467">此服務會儲存其狀態，因此必要時，可以在多次重新開機後再繼續。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-467">The service saves its state so that it can continue through multiple reboots if necessary.</span></span> <span data-ttu-id="4b8fc-468">當服務偵測到已經沒有動作佇列時，會重設其狀態，使其不會在下次電腦開機時重新啟動，然後將服務本身關閉。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-468">When the service detects that there are no more actions queued, it resets its status so that it will not restart the next time the computer is booted, and then it shuts itself down.</span></span>

### <a name="service-interaction-with-clients"></a><span data-ttu-id="4b8fc-469">服務與用戶端互動</span><span class="sxs-lookup"><span data-stu-id="4b8fc-469">Service Interaction with Clients</span></span>

<span data-ttu-id="4b8fc-470">在 .NET Framework 2.0 版中，與原生映像服務的唯一互動，是透過命令列工具 Ngen.exe。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-470">In the .NET Framework version 2.0, the only interaction with the native image service is through the command-line tool Ngen.exe.</span></span> <span data-ttu-id="4b8fc-471">在安裝指令碼中使用命令列工具，將原生映像服務的動作加入佇列中，並與服務互動。</span><span class="sxs-lookup"><span data-stu-id="4b8fc-471">Use the command-line tool in installation scripts to queue actions for the native image service and to interact with the service.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b8fc-472">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b8fc-472">See also</span></span>

- [<span data-ttu-id="4b8fc-473">工具</span><span class="sxs-lookup"><span data-stu-id="4b8fc-473">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="4b8fc-474">Managed 執行程序</span><span class="sxs-lookup"><span data-stu-id="4b8fc-474">Managed Execution Process</span></span>](../../../docs/standard/managed-execution-process.md)
- [<span data-ttu-id="4b8fc-475">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="4b8fc-475">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="4b8fc-476">命令提示字元</span><span class="sxs-lookup"><span data-stu-id="4b8fc-476">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

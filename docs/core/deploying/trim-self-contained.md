---
title: 修剪自包含應用程式
description: 瞭解如何修剪自包含應用以減小其大小。 .NET Core 將運行時與自包含發佈的應用捆綁在一起,並且通常包含更多運行時,因此有必要這樣做。
author: jamshedd
ms.author: jamshedd
ms.date: 01/23/2020
ms.openlocfilehash: 5206ca255c500b382402ac4e7dd3300b7face1cf
ms.sourcegitcommit: 45cced471d59d5dac3f0c92abc9d4849716098a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/04/2020
ms.locfileid: "80665632"
---
# <a name="trim-self-contained-deployments-and-executables"></a><span data-ttu-id="4a480-104">修剪自包含部署及可執行檔</span><span class="sxs-lookup"><span data-stu-id="4a480-104">Trim self-contained deployments and executables</span></span>

<span data-ttu-id="4a480-105">發佈應用程式自包含時,.NET Core 運行時與應用程式捆綁在一起。</span><span class="sxs-lookup"><span data-stu-id="4a480-105">When publishing an application self-contained, the .NET Core runtime is bundled together with the application.</span></span> <span data-ttu-id="4a480-106">這種捆綁為打包的應用程式增加了大量內容。</span><span class="sxs-lookup"><span data-stu-id="4a480-106">This bundling adds a significant amount of content to your packaged application.</span></span>

<span data-ttu-id="4a480-107">在部署應用程式時,大小通常是一個重要因素。</span><span class="sxs-lookup"><span data-stu-id="4a480-107">When it comes to deploying your application, size is often an important factor.</span></span> <span data-ttu-id="4a480-108">保持包應用程式的大小盡可能小通常是應用程式開發人員的目標。</span><span class="sxs-lookup"><span data-stu-id="4a480-108">Keeping the size of the package application as small as possible is typically a goal for application developers.</span></span>

<span data-ttu-id="4a480-109">根據應用程式的複雜性,運行應用程式只需要運行時的子集。</span><span class="sxs-lookup"><span data-stu-id="4a480-109">Depending on the complexity of the application, only a subset of the runtime is required to run the application.</span></span> <span data-ttu-id="4a480-110">這些未使用的運行時部分是不必要的,可以從打包的應用程式修剪。</span><span class="sxs-lookup"><span data-stu-id="4a480-110">These unused parts of the runtime are unnecessary and can be trimmed from the packaged application.</span></span>

> [!NOTE]
> <span data-ttu-id="4a480-111">修剪是 .NET Core 3.1 中的實驗功能,_僅適用於_自包含發布的應用程式。</span><span class="sxs-lookup"><span data-stu-id="4a480-111">Trimming is an experimental feature in .NET Core 3.1 and is _only_ available to applications that are published self-contained.</span></span>

## <a name="trim-your-application"></a><span data-ttu-id="4a480-112">修剪應用程式</span><span class="sxs-lookup"><span data-stu-id="4a480-112">Trim your application</span></span>

<span data-ttu-id="4a480-113">下面的範例簡用如何使用[dotnet 發布](../tools/dotnet-publish.md)指令修剪應用程式:</span><span class="sxs-lookup"><span data-stu-id="4a480-113">The following example shows how to trim your application using the [dotnet publish](../tools/dotnet-publish.md) command:</span></span>

```dotnetcli
dotnet publish -c Release -r win10-x64 --self-contained true /p:PublishSingleFile=false /p:PublishTrimmed=true
```

<span data-ttu-id="4a480-114">修剪功能的工作原理是檢查應用程式二進位檔,以發現和生成所需運行時程式集的圖形。</span><span class="sxs-lookup"><span data-stu-id="4a480-114">The trimming feature works by examining the application binaries to discover and build a graph of the required runtime assemblies.</span></span> <span data-ttu-id="4a480-115">將修剪未引用的剩餘運行時程式集。</span><span class="sxs-lookup"><span data-stu-id="4a480-115">The remaining runtime assemblies that aren't referenced are trimmed.</span></span>

## <a name="trimming-issues-when-using-reflection"></a><span data-ttu-id="4a480-116">使用反射時的修剪問題</span><span class="sxs-lookup"><span data-stu-id="4a480-116">Trimming issues when using reflection</span></span>

<span data-ttu-id="4a480-117">在某些情況下,修剪功能將無法檢測引用。</span><span class="sxs-lookup"><span data-stu-id="4a480-117">There are scenarios in which the trimming functionality will fail to detect references.</span></span> <span data-ttu-id="4a480-118">例如,使用反射的應用程式可能會遇到此問題,因為對程式集的依賴項僅在運行時已知。</span><span class="sxs-lookup"><span data-stu-id="4a480-118">For example, an application that uses reflection could run into this issue because the dependency on the assembly will only be known at run time.</span></span>

<span data-ttu-id="4a480-119">僅當反射用法依賴於未直接引用的運行時程式集時,修剪才成問題。</span><span class="sxs-lookup"><span data-stu-id="4a480-119">Trimming is only a problem if the reflection usage depends on a runtime assembly that isn't referenced directly.</span></span> <span data-ttu-id="4a480-120">請記住,應用程式代碼可能不會直接使用反射,但您引用的第三方程式集可能正在使用它。</span><span class="sxs-lookup"><span data-stu-id="4a480-120">Keep in mind that your application code may not be using reflection directly, but a third-party assembly you're referencing may be using it.</span></span>

<span data-ttu-id="4a480-121">當代碼通過反射引用 API 並且不希望連結器修剪包含該 API 的程式集時,可以修改專案檔以從修剪過程中排除程式集。</span><span class="sxs-lookup"><span data-stu-id="4a480-121">When the code is referencing an API through reflection and you don't want the linker to trim the assembly that contains that API, you can modify your project file to exclude the assembly from the trimming process.</span></span> <span data-ttu-id="4a480-122">下面的範例簡報如何防止修剪呼`System.Security`叫的程式集:</span><span class="sxs-lookup"><span data-stu-id="4a480-122">The following example shows how to prevent an assembly called `System.Security` from being trimmed:</span></span>

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="see-also"></a><span data-ttu-id="4a480-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a480-123">See also</span></span>

- [<span data-ttu-id="4a480-124">.NET 核心應用程式部署</span><span class="sxs-lookup"><span data-stu-id="4a480-124">.NET Core application deployment</span></span>](index.md)

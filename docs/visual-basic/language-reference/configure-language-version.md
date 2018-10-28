---
title: 選取 Visual Basic 語言版本
description: 設定編譯器執行特定編譯器版本搭配使用的語法驗證。
ms.date: 05/24/2018
ms.openlocfilehash: 7628b5a7c27f5b26171d42e44a58598ef3d5d49f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194718"
---
# <a name="select-the-visual-basic-language-version"></a><span data-ttu-id="c593e-103">選取 Visual Basic 語言版本</span><span class="sxs-lookup"><span data-stu-id="c593e-103">Select the Visual Basic language version</span></span>

<span data-ttu-id="c593e-104">Visual Basic 編譯器會預設為最新的主要版本已發行的語言。</span><span class="sxs-lookup"><span data-stu-id="c593e-104">The Visual Basic compiler defaults to the latest major version of the language that has been released.</span></span> <span data-ttu-id="c593e-105">您可以選擇使用語言的新點發行來編譯任何專案。</span><span class="sxs-lookup"><span data-stu-id="c593e-105">You may choose to compile any project using a new point release of the language.</span></span> <span data-ttu-id="c593e-106">選擇語言的較新版本可讓您的專案利用最新的語言功能。</span><span class="sxs-lookup"><span data-stu-id="c593e-106">Choosing a newer version of the language enables your project to make use of the latest language features.</span></span> <span data-ttu-id="c593e-107">在其他情況下，使用較舊版本的語言時，您可能需要驗證專案全新地進行編譯。</span><span class="sxs-lookup"><span data-stu-id="c593e-107">In other scenarios, you may need to validate that a project compiles cleanly when using an older version of the language.</span></span>

<span data-ttu-id="c593e-108">此功能可讓在您開發環境中決定安裝新版本的 SDK 和工具，與在專案中決定納入新語言功能這兩件事分開。</span><span class="sxs-lookup"><span data-stu-id="c593e-108">This capability decouples the decision to install new versions of the SDK and tools in your development environment from the decision to incorporate new language features in a project.</span></span> <span data-ttu-id="c593e-109">您可以在組建電腦上安裝最新的 SDK 和工具。</span><span class="sxs-lookup"><span data-stu-id="c593e-109">You can install the latest SDK and tools on your build machine.</span></span> <span data-ttu-id="c593e-110">每個專案可以設定為針對其組建使用特定版本的語言。</span><span class="sxs-lookup"><span data-stu-id="c593e-110">Each project can be configured to use a specific version of the language for its build.</span></span>

<span data-ttu-id="c593e-111">有三種方式可設定的語言版本：</span><span class="sxs-lookup"><span data-stu-id="c593e-111">There are three ways to set the language version:</span></span>

- <span data-ttu-id="c593e-112">手動編輯您[ **.vbproj**檔案](#edit-the-vbproj-file)</span><span class="sxs-lookup"><span data-stu-id="c593e-112">Manually edit your [**.vbproj** file](#edit-the-vbproj-file)</span></span>
- <span data-ttu-id="c593e-113">設定語言版本[子目錄中的多個專案](#configure-multiple-projects)</span><span class="sxs-lookup"><span data-stu-id="c593e-113">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects)</span></span>
- <span data-ttu-id="c593e-114">設定[`-langversion`編譯器選項](#set-the-langversion-compiler-option)</span><span class="sxs-lookup"><span data-stu-id="c593e-114">Configure the [`-langversion` compiler option](#set-the-langversion-compiler-option)</span></span>

## <a name="edit-the-vbproj-file"></a><span data-ttu-id="c593e-115">編輯 vbproj 檔案</span><span class="sxs-lookup"><span data-stu-id="c593e-115">Edit the vbproj file</span></span>

<span data-ttu-id="c593e-116">您可以設定的語言版本，您 **.vbproj**檔案。</span><span class="sxs-lookup"><span data-stu-id="c593e-116">You can set the language version in your **.vbproj** file.</span></span> <span data-ttu-id="c593e-117">新增下列項目：</span><span class="sxs-lookup"><span data-stu-id="c593e-117">Add the following element:</span></span>

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="c593e-118">值`latest`使用 Visual Basic 語言的最新次要版本。</span><span class="sxs-lookup"><span data-stu-id="c593e-118">The value `latest` uses the latest minor version of the Visual Basic language.</span></span> <span data-ttu-id="c593e-119">有效值為：</span><span class="sxs-lookup"><span data-stu-id="c593e-119">Valid values are:</span></span>

|<span data-ttu-id="c593e-120">值</span><span class="sxs-lookup"><span data-stu-id="c593e-120">Value</span></span>|<span data-ttu-id="c593e-121">意義</span><span class="sxs-lookup"><span data-stu-id="c593e-121">Meaning</span></span>|
|------------|-------------|
|<span data-ttu-id="c593e-122">default</span><span class="sxs-lookup"><span data-stu-id="c593e-122">default</span></span>|<span data-ttu-id="c593e-123">編譯器會接受它可支援之最新主要版本的所有有效語言語法。</span><span class="sxs-lookup"><span data-stu-id="c593e-123">The compiler accepts all valid language syntax from the latest major version that it can support.</span></span>|
|<span data-ttu-id="c593e-124">9</span><span class="sxs-lookup"><span data-stu-id="c593e-124">9</span></span>|<span data-ttu-id="c593e-125">編譯器會接受包含在 Visual Basic 9.0 或較低的語法。</span><span class="sxs-lookup"><span data-stu-id="c593e-125">The compiler accepts only syntax that is included in Visual Basic 9.0 or lower.</span></span>|
|<span data-ttu-id="c593e-126">10</span><span class="sxs-lookup"><span data-stu-id="c593e-126">10</span></span>|<span data-ttu-id="c593e-127">編譯器會接受包含在 Visual Basic 10.0 或更低的語法。</span><span class="sxs-lookup"><span data-stu-id="c593e-127">The compiler accepts only syntax that is included in Visual Basic 10.0 or lower.</span></span>|
|<span data-ttu-id="c593e-128">11</span><span class="sxs-lookup"><span data-stu-id="c593e-128">11</span></span>|<span data-ttu-id="c593e-129">編譯器會接受包含在 Visual Basic 11.0 或更低的語法。</span><span class="sxs-lookup"><span data-stu-id="c593e-129">The compiler accepts only syntax that is included in Visual Basic 11.0 or lower.</span></span>|
|<span data-ttu-id="c593e-130">12</span><span class="sxs-lookup"><span data-stu-id="c593e-130">12</span></span>|<span data-ttu-id="c593e-131">編譯器會接受包含在 Visual Basic 12.0 或較低的語法。</span><span class="sxs-lookup"><span data-stu-id="c593e-131">The compiler accepts only syntax that is included in Visual Basic 12.0 or lower.</span></span>|
|<span data-ttu-id="c593e-132">14</span><span class="sxs-lookup"><span data-stu-id="c593e-132">14</span></span>|<span data-ttu-id="c593e-133">編譯器會接受包含在 Visual Basic 14.0 或較低的語法。</span><span class="sxs-lookup"><span data-stu-id="c593e-133">The compiler accepts only syntax that is included in Visual Basic 14.0 or lower.</span></span>|
|<span data-ttu-id="c593e-134">15</span><span class="sxs-lookup"><span data-stu-id="c593e-134">15</span></span>|<span data-ttu-id="c593e-135">編譯器會接受包含在 Visual Basic 15.0 或更低的語法。</span><span class="sxs-lookup"><span data-stu-id="c593e-135">The compiler accepts only syntax that is included in Visual Basic 15.0 or lower.</span></span>|
|<span data-ttu-id="c593e-136">15.3</span><span class="sxs-lookup"><span data-stu-id="c593e-136">15.3</span></span>|<span data-ttu-id="c593e-137">編譯器會接受包含在 Visual Basic 15.3 或更低的語法。</span><span class="sxs-lookup"><span data-stu-id="c593e-137">The compiler accepts only syntax that is included in Visual Basic 15.3 or lower.</span></span>|
|<span data-ttu-id="c593e-138">15.5</span><span class="sxs-lookup"><span data-stu-id="c593e-138">15.5</span></span>|<span data-ttu-id="c593e-139">編譯器會接受包含在 Visual Basic 15.5 或較低的語法。</span><span class="sxs-lookup"><span data-stu-id="c593e-139">The compiler accepts only syntax that is included in Visual Basic 15.5 or lower.</span></span>|
|<span data-ttu-id="c593e-140">latest</span><span class="sxs-lookup"><span data-stu-id="c593e-140">latest</span></span>|<span data-ttu-id="c593e-141">編譯器會接受它可支援的所有有效語言語法。</span><span class="sxs-lookup"><span data-stu-id="c593e-141">The compiler accepts all valid language syntax that it can support.</span></span>|

<span data-ttu-id="c593e-142">特殊字串 `default` 和 `latest` 會分別解析成安裝在組建電腦上的最新主要和次要語言版本。</span><span class="sxs-lookup"><span data-stu-id="c593e-142">The special strings `default` and `latest` resolve to the latest major and minor language versions installed on the build machine, respectively.</span></span>

## <a name="configure-multiple-projects"></a><span data-ttu-id="c593e-143">設定多個專案</span><span class="sxs-lookup"><span data-stu-id="c593e-143">Configure multiple projects</span></span>

<span data-ttu-id="c593e-144">您可以建立 **Directory.build.props** 檔案，其中包含 `<LangVersion>` 元素來設定多個目錄。</span><span class="sxs-lookup"><span data-stu-id="c593e-144">You can create a **Directory.build.props** file that contains the `<LangVersion>` element to configure multiple directories.</span></span> <span data-ttu-id="c593e-145">您通常會在解決方案目錄中進行。</span><span class="sxs-lookup"><span data-stu-id="c593e-145">You typically do that in your solution directory.</span></span> <span data-ttu-id="c593e-146">將下列內容新增到解決方案目錄中的 **Directory.build.props** 檔案：</span><span class="sxs-lookup"><span data-stu-id="c593e-146">Add the following to a **Directory.build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>15.5</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="c593e-147">現在，每個子目錄包含該檔案的目錄中的組建將會使用 Visual Basic 15.5 版語法。</span><span class="sxs-lookup"><span data-stu-id="c593e-147">Now, builds in every subdirectory of the directory containing that file will use Visual Basic version 15.5 syntax.</span></span> <span data-ttu-id="c593e-148">如需詳細資訊，請參閱[自訂組建](/visualstudio/msbuild/customize-your-build.md)。</span><span class="sxs-lookup"><span data-stu-id="c593e-148">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build.md).</span></span>

## <a name="set-the-langversion-compiler-option"></a><span data-ttu-id="c593e-149">設定 langversion 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="c593e-149">Set the langversion compiler option</span></span>

<span data-ttu-id="c593e-150">您可以使用 `-langversion` 命令列選項。</span><span class="sxs-lookup"><span data-stu-id="c593e-150">You can use the `-langversion` command-line option.</span></span> <span data-ttu-id="c593e-151">如需詳細資訊，請參閱 [-langversion](../reference/command-line-compiler/langversion.md) 編譯器選項的文章。</span><span class="sxs-lookup"><span data-stu-id="c593e-151">For more information, see the article on the [-langversion](../reference/command-line-compiler/langversion.md) compiler option.</span></span> <span data-ttu-id="c593e-152">您可以看到一份有效的值輸入`vbc -langversion:?`。</span><span class="sxs-lookup"><span data-stu-id="c593e-152">You can see a list of the valid values by typing  `vbc -langversion:?` .</span></span>

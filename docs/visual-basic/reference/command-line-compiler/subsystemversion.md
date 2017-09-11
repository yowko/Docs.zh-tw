---
title: "/subsystemversion (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /subsystemversion compiler option [Visual Basic]
- -subsystemversion compiler option [Visual Basic]
- subsystemversion compiler option [Visual Basic]
ms.assetid: 08be22b2-f447-4cd3-8203-120b1b920b54
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: efeade3fcde18f02b3a760adc50d3555df6c9ed7
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="subsystemversion-visual-basic"></a><span data-ttu-id="a600b-102">/subsystemversion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a600b-102">/subsystemversion (Visual Basic)</span></span>
<span data-ttu-id="a600b-103">指定的子系統可以執行產生的可執行檔，以決定可以執行的可執行檔的 Windows 版本的最小版本。</span><span class="sxs-lookup"><span data-stu-id="a600b-103">Specifies the minimum version of the subsystem on which the generated executable file can run, thereby determining the versions of Windows on which the executable file can run.</span></span> <span data-ttu-id="a600b-104">大多數情況下，此選項可確保可執行檔可以利用特定的安全性功能，與舊版本的 Windows。</span><span class="sxs-lookup"><span data-stu-id="a600b-104">Most commonly, this option ensures that the executable file can leverage particular security features that aren’t available with older versions of Windows.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a600b-105">若要指定的子系統本身，請使用[/目標](../../../csharp/language-reference/compiler-options/target-compiler-option.md)編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="a600b-105">To specify the subsystem itself, use the [/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) compiler option.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a600b-106">語法</span><span class="sxs-lookup"><span data-stu-id="a600b-106">Syntax</span></span>  
  
```vb  
/subsystemversion:major.minor  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a600b-107">參數</span><span class="sxs-lookup"><span data-stu-id="a600b-107">Parameters</span></span>  
 `major.minor`  
 <span data-ttu-id="a600b-108">最小必要版本的子系統，主要和次要版本的點標記法中表示。</span><span class="sxs-lookup"><span data-stu-id="a600b-108">The minimum required version of the subsystem, as expressed in a dot notation for major and minor versions.</span></span> <span data-ttu-id="a600b-109">例如，您可以指定應用程式不能是早於 Windows 7 如果您將此選項的值設定為 6.01，如本主題稍後的表格所述的作業系統上執行。</span><span class="sxs-lookup"><span data-stu-id="a600b-109">For example, you can specify that an application can't run on an operating system that's older than Windows 7 if you set the value of this option to 6.01, as the table later in this topic describes.</span></span> <span data-ttu-id="a600b-110">您必須指定的值`major`和`minor`為整數。</span><span class="sxs-lookup"><span data-stu-id="a600b-110">You must specify the values for `major` and `minor` as integers.</span></span>  
  
 <span data-ttu-id="a600b-111">前置歸零，然後`minor`版本不會變更版本，但尾端為零。</span><span class="sxs-lookup"><span data-stu-id="a600b-111">Leading zeroes in the `minor` version don't change the version, but trailing zeroes do.</span></span> <span data-ttu-id="a600b-112">比方說，6.1 和 6.01 參考相同的版本，但 6.10 指的是不同的版本。</span><span class="sxs-lookup"><span data-stu-id="a600b-112">For example, 6.1 and 6.01 refer to the same version, but 6.10 refers to a different version.</span></span> <span data-ttu-id="a600b-113">我們建議以避免產生混淆的兩位數表示的次要版本。</span><span class="sxs-lookup"><span data-stu-id="a600b-113">We recommend expressing the minor version as two digits to avoid confusion.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a600b-114">備註</span><span class="sxs-lookup"><span data-stu-id="a600b-114">Remarks</span></span>  
 <span data-ttu-id="a600b-115">下表列出常見的子系統版本的 Windows。</span><span class="sxs-lookup"><span data-stu-id="a600b-115">The following table lists common subsystem versions of Windows.</span></span>  
  
|<span data-ttu-id="a600b-116">Windows 版本</span><span class="sxs-lookup"><span data-stu-id="a600b-116">Windows version</span></span>|<span data-ttu-id="a600b-117">子系統的版本</span><span class="sxs-lookup"><span data-stu-id="a600b-117">Subsystem version</span></span>|  
|---------------------|-----------------------|  
|<span data-ttu-id="a600b-118">Windows 2000</span><span class="sxs-lookup"><span data-stu-id="a600b-118">Windows 2000</span></span>|<span data-ttu-id="a600b-119">5.00</span><span class="sxs-lookup"><span data-stu-id="a600b-119">5.00</span></span>|  
|<span data-ttu-id="a600b-120">Windows XP</span><span class="sxs-lookup"><span data-stu-id="a600b-120">Windows XP</span></span>|<span data-ttu-id="a600b-121">5.01</span><span class="sxs-lookup"><span data-stu-id="a600b-121">5.01</span></span>|  
|<span data-ttu-id="a600b-122">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="a600b-122">Windows Server 2003</span></span>|<span data-ttu-id="a600b-123">5.02</span><span class="sxs-lookup"><span data-stu-id="a600b-123">5.02</span></span>|  
|<span data-ttu-id="a600b-124">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="a600b-124">Windows Vista</span></span>|<span data-ttu-id="a600b-125">6.00</span><span class="sxs-lookup"><span data-stu-id="a600b-125">6.00</span></span>|  
|<span data-ttu-id="a600b-126">Windows 7</span><span class="sxs-lookup"><span data-stu-id="a600b-126">Windows 7</span></span>|<span data-ttu-id="a600b-127">6.01</span><span class="sxs-lookup"><span data-stu-id="a600b-127">6.01</span></span>|  
|<span data-ttu-id="a600b-128">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="a600b-128">Windows Server 2008</span></span>|<span data-ttu-id="a600b-129">6.01</span><span class="sxs-lookup"><span data-stu-id="a600b-129">6.01</span></span>|  
|[!INCLUDE[win8](../../../csharp/language-reference/compiler-options/includes/win8_md.md)]|<span data-ttu-id="a600b-130">6.02</span><span class="sxs-lookup"><span data-stu-id="a600b-130">6.02</span></span>|  
  
## <a name="default-values"></a><span data-ttu-id="a600b-131">預設值</span><span class="sxs-lookup"><span data-stu-id="a600b-131">Default values</span></span>  
 <span data-ttu-id="a600b-132">預設值的**/subsystemversion**編譯器選項取決於下列清單中的條件︰</span><span class="sxs-lookup"><span data-stu-id="a600b-132">The default value of the **/subsystemversion** compiler option depends on the conditions in the following list:</span></span>  
  
-   <span data-ttu-id="a600b-133">預設值為 6.02，如果下列清單中的任何編譯器選項設定︰</span><span class="sxs-lookup"><span data-stu-id="a600b-133">The default value is 6.02 if any compiler option in the following list is set:</span></span>  
  
    -   [<span data-ttu-id="a600b-134">/target: appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="a600b-134">/target:appcontainerexe</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
  
    -   [<span data-ttu-id="a600b-135">/target: winmdobj</span><span class="sxs-lookup"><span data-stu-id="a600b-135">/target:winmdobj</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
  
    -   [<span data-ttu-id="a600b-136">/platform:arm</span><span class="sxs-lookup"><span data-stu-id="a600b-136">/platform:arm</span></span>](../../../visual-basic/reference/command-line-compiler/platform.md)  
  
-   <span data-ttu-id="a600b-137">如果您使用 MSBuild，預設值是 6.00、 您的目標[!INCLUDE[net_v45](../../../csharp/language-reference/compiler-options/includes/net_v45_md.md)]，而且您還沒有設定任何稍早在此清單中所指定的編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="a600b-137">The default value is 6.00 if you're using MSBuild, you're targeting [!INCLUDE[net_v45](../../../csharp/language-reference/compiler-options/includes/net_v45_md.md)], and you haven't set any of the compiler options that were specified earlier in this list.</span></span>  
  
-   <span data-ttu-id="a600b-138">預設值是 4.00 如果前一個條件為 true。</span><span class="sxs-lookup"><span data-stu-id="a600b-138">The default value is 4.00 if none of the previous conditions is true.</span></span>  
  
## <a name="setting-this-option"></a><span data-ttu-id="a600b-139">設定這個選項</span><span class="sxs-lookup"><span data-stu-id="a600b-139">Setting this option</span></span>  
 <span data-ttu-id="a600b-140">若要設定**/subsystemversion**編譯器選項在 Visual Studio 中，您必須開啟.vbproj 檔案，並指定的值`SubsystemVersion`MSBuild XML 中的屬性。</span><span class="sxs-lookup"><span data-stu-id="a600b-140">To set the **/subsystemversion** compiler option in Visual Studio, you must open the .vbproj file and specify a value for the `SubsystemVersion` property in the MSBuild XML.</span></span> <span data-ttu-id="a600b-141">您無法在 Visual Studio IDE 中設定這個選項。</span><span class="sxs-lookup"><span data-stu-id="a600b-141">You can't set this option in the Visual Studio IDE.</span></span> <span data-ttu-id="a600b-142">詳細資訊，請參閱本主題前面的 「 預設值 」 或[一般 MSBuild 專案屬性](https://docs.microsoft.com/visualstudio/msbuild/common-msbuild-project-properties)。</span><span class="sxs-lookup"><span data-stu-id="a600b-142">For more information, see "Default values" earlier in this topic or [Common MSBuild Project Properties](https://docs.microsoft.com/visualstudio/msbuild/common-msbuild-project-properties).</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="a600b-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a600b-143">See Also</span></span>  
[<span data-ttu-id="a600b-144">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="a600b-144">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)

[<span data-ttu-id="a600b-145">MSBuild 屬性</span><span class="sxs-lookup"><span data-stu-id="a600b-145">MSBuild Properties</span></span>](https://docs.microsoft.com/visualstudio/msbuild/msbuild-properties)


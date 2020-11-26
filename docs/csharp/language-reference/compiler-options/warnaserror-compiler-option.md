---
description: -warnaserror (C# 編譯器選項)
title: -warnaserror (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /warnaserror
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
ms.openlocfilehash: 9c3b307668968865b401aedc04c79f95d4f32513
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "91171334"
---
# <a name="-warnaserror-c-compiler-options"></a><span data-ttu-id="7794a-103">-warnaserror (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="7794a-103">-warnaserror (C# Compiler Options)</span></span>

<span data-ttu-id="7794a-104">**-warnaserror+** 選項會將所有警告都視為錯誤</span><span class="sxs-lookup"><span data-stu-id="7794a-104">The **-warnaserror+** option treats all warnings as errors</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7794a-105">語法</span><span class="sxs-lookup"><span data-stu-id="7794a-105">Syntax</span></span>  
  
```console  
-warnaserror[+ | -][:warning-list]  
```  
  
## <a name="remarks"></a><span data-ttu-id="7794a-106">備註</span><span class="sxs-lookup"><span data-stu-id="7794a-106">Remarks</span></span>  

 <span data-ttu-id="7794a-107">任何原本報告為警告的訊息都會改成報告為錯誤，並中止建置程序 (不會建置輸出檔)。</span><span class="sxs-lookup"><span data-stu-id="7794a-107">Any messages that would ordinarily be reported as warnings are instead reported as errors, and the build process is halted (no output files are built).</span></span>  
  
 <span data-ttu-id="7794a-108">根據預設，**-warnaserror-** 會生效，這會導致無法產生輸出檔案的警告。</span><span class="sxs-lookup"><span data-stu-id="7794a-108">By default, **-warnaserror-** is in effect, which causes warnings to not prevent the generation of an output file.</span></span> <span data-ttu-id="7794a-109">**-warnaserror** 與 **-warnaserror+** 相同，都會將警告視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="7794a-109">**-warnaserror**, which is the same as **-warnaserror+**, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="7794a-110">選擇性，如果您只想要將少數特定警告視為錯誤，則可以指定將以逗號分隔的警告編號清單視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="7794a-110">Optionally, if you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span> <span data-ttu-id="7794a-111">您可以使用 **可為 null** 的速記來指定所有可 null 性警告的集合。</span><span class="sxs-lookup"><span data-stu-id="7794a-111">The set of all nullability warnings can be specified with the **nullable** shorthand.</span></span>
  
 <span data-ttu-id="7794a-112">使用 [-warn](./warn-compiler-option.md) 指定您想要編譯器顯示的警告層級。</span><span class="sxs-lookup"><span data-stu-id="7794a-112">Use [-warn](./warn-compiler-option.md) to specify the level of warnings that you want the compiler to display.</span></span> <span data-ttu-id="7794a-113">使用 [-nowarn](./nowarn-compiler-option.md) 停用特定警告。</span><span class="sxs-lookup"><span data-stu-id="7794a-113">Use [-nowarn](./nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="7794a-114">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="7794a-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="7794a-115">開啟專案的 [屬性] 頁面。</span><span class="sxs-lookup"><span data-stu-id="7794a-115">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="7794a-116">按一下 [建置] 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="7794a-116">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="7794a-117">修改 [警告視為錯誤] 屬性。</span><span class="sxs-lookup"><span data-stu-id="7794a-117">Modify the **Treat Warnings As Errors** property.</span></span>  
  
 <span data-ttu-id="7794a-118">若要以程式設計方式設定這個編譯器選項，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>。</span><span class="sxs-lookup"><span data-stu-id="7794a-118">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7794a-119">範例</span><span class="sxs-lookup"><span data-stu-id="7794a-119">Example</span></span>  

 <span data-ttu-id="7794a-120">編譯 `in.cs`，並讓編譯器不要顯示任何警告：</span><span class="sxs-lookup"><span data-stu-id="7794a-120">Compile `in.cs` and have the compiler display no warnings:</span></span>  
  
```console  
csc -warnaserror in.cs  
csc -warnaserror:642,649,652,nullable in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="7794a-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7794a-121">See also</span></span>

- [<span data-ttu-id="7794a-122">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="7794a-122">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="7794a-123">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="7794a-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

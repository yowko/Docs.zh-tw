---
title: -warnaserror (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /warnaserror
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
ms.openlocfilehash: a29b0a6095453e3d2747cad9d9f71b463d8f6b1f
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44081497"
---
# <a name="-warnaserror-c-compiler-options"></a><span data-ttu-id="763be-102">-warnaserror (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="763be-102">-warnaserror (C# Compiler Options)</span></span>
<span data-ttu-id="763be-103">**-warnaserror+** 選項會將所有警告都視為錯誤</span><span class="sxs-lookup"><span data-stu-id="763be-103">The **-warnaserror+** option treats all warnings as errors</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="763be-104">語法</span><span class="sxs-lookup"><span data-stu-id="763be-104">Syntax</span></span>  
  
```console  
-warnaserror[+ | -][:warning-list]  
```  
  
## <a name="remarks"></a><span data-ttu-id="763be-105">備註</span><span class="sxs-lookup"><span data-stu-id="763be-105">Remarks</span></span>  
 <span data-ttu-id="763be-106">任何原本報告為警告的訊息都會改成報告為錯誤，並中止建置程序 (不會建置輸出檔)。</span><span class="sxs-lookup"><span data-stu-id="763be-106">Any messages that would ordinarily be reported as warnings are instead reported as errors, and the build process is halted (no output files are built).</span></span>  
  
 <span data-ttu-id="763be-107">根據預設，**-warnaserror-** 會生效，這會導致無法產生輸出檔案的警告。</span><span class="sxs-lookup"><span data-stu-id="763be-107">By default, **-warnaserror-** is in effect, which causes warnings to not prevent the generation of an output file.</span></span> <span data-ttu-id="763be-108">**-warnaserror** 與 **-warnaserror+** 相同，都會將警告視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="763be-108">**-warnaserror**, which is the same as **-warnaserror+**, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="763be-109">選擇性，如果您只想要將少數特定警告視為錯誤，則可以指定將以逗號分隔的警告編號清單視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="763be-109">Optionally, if you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
 <span data-ttu-id="763be-110">使用 [-warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md) 指定您想要編譯器顯示的警告層級。</span><span class="sxs-lookup"><span data-stu-id="763be-110">Use [-warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md) to specify the level of warnings that you want the compiler to display.</span></span> <span data-ttu-id="763be-111">使用 [-nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) 停用特定警告。</span><span class="sxs-lookup"><span data-stu-id="763be-111">Use [-nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="763be-112">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="763be-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="763be-113">開啟專案的 [屬性] 頁面。</span><span class="sxs-lookup"><span data-stu-id="763be-113">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="763be-114">按一下 [建置] 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="763be-114">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="763be-115">修改 [警告視為錯誤] 屬性。</span><span class="sxs-lookup"><span data-stu-id="763be-115">Modify the **Treat Warnings As Errors** property.</span></span>  
  
 <span data-ttu-id="763be-116">若要以程式設計方式設定這個編譯器選項，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>。</span><span class="sxs-lookup"><span data-stu-id="763be-116">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="763be-117">範例</span><span class="sxs-lookup"><span data-stu-id="763be-117">Example</span></span>  
 <span data-ttu-id="763be-118">編譯 `in.cs`，並讓編譯器不要顯示任何警告：</span><span class="sxs-lookup"><span data-stu-id="763be-118">Compile `in.cs` and have the compiler display no warnings:</span></span>  
  
```console  
csc -warnaserror in.cs  
csc -warnaserror:642,649,652 in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="763be-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="763be-119">See Also</span></span>  

- [<span data-ttu-id="763be-120">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="763be-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="763be-121">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="763be-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

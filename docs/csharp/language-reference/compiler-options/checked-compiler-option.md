---
title: -checked (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /checked
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
ms.openlocfilehash: 4ed8467b0e1923aedf38edfd4a25414cbcb88b7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="-checked-c-compiler-options"></a><span data-ttu-id="6d443-102">-checked (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="6d443-102">-checked (C# Compiler Options)</span></span>
<span data-ttu-id="6d443-103">**-checked** 選項會指定產生超出該資料類型範圍之值且不在 [checked](../../../csharp/language-reference/keywords/checked.md) 或 [unchecked](../../../csharp/language-reference/keywords/unchecked.md) 關鍵字範圍內的整數算術陳述式是否導致執行階段例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6d443-103">The **-checked** option specifies whether an integer arithmetic statement that results in a value that is outside the range of the data type, and that is not in the scope of a [checked](../../../csharp/language-reference/keywords/checked.md) or [unchecked](../../../csharp/language-reference/keywords/unchecked.md) keyword, causes a run-time exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d443-104">語法</span><span class="sxs-lookup"><span data-stu-id="6d443-104">Syntax</span></span>  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="6d443-105">備註</span><span class="sxs-lookup"><span data-stu-id="6d443-105">Remarks</span></span>  
 <span data-ttu-id="6d443-106">在 `checked` 或 `unchecked` 關鍵字範圍內的整數算術陳述式不一定會有 **-checked** 選項的效果。</span><span class="sxs-lookup"><span data-stu-id="6d443-106">An integer arithmetic statement that is in the scope of a `checked` or `unchecked` keyword is not subject to the effect of the **-checked** option.</span></span>  
  
 <span data-ttu-id="6d443-107">如果不在 `checked` 或 `unchecked` 關鍵字範圍內的整數算術陳述式產生超出該資料類型範圍的值，並在編譯時使用 **-checked+** (**-checked**)，則該陳述式會在執行階段導致例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6d443-107">If an integer arithmetic statement that is not in the scope of a `checked` or `unchecked` keyword results in a value outside the range of the data type, and **-checked+** (**-checked**) is used in the compilation, that statement causes an exception at run time.</span></span> <span data-ttu-id="6d443-108">如果在編譯時使用 **-checked-**，則該陳述式不會在執行階段導致例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6d443-108">If **-checked-** is used in the compilation, that statement does not cause an exception at run time.</span></span>  
  
 <span data-ttu-id="6d443-109">這個選項的預設值是 **-checked-**。</span><span class="sxs-lookup"><span data-stu-id="6d443-109">The default value for this option is **-checked-**.</span></span> <span data-ttu-id="6d443-110">使用 **-checked-** 的其中一個案例是建置大型應用程式。</span><span class="sxs-lookup"><span data-stu-id="6d443-110">One scenario for using **-checked-** is in building large applications.</span></span> <span data-ttu-id="6d443-111">自動化工具有時是用來建置這類應用程式，而且這類工具可能會將 **-checked** 自動設為 +。</span><span class="sxs-lookup"><span data-stu-id="6d443-111">Sometimes automated tools are used to build such applications, and such a tool might automatically set **-checked** to +.</span></span> <span data-ttu-id="6d443-112">您可以指定 **-checked-** 來覆寫工具的全域預設值。</span><span class="sxs-lookup"><span data-stu-id="6d443-112">You can override the tool's global default by specifying **-checked-**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="6d443-113">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="6d443-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="6d443-114">開啟專案的 [屬性] 頁面。</span><span class="sxs-lookup"><span data-stu-id="6d443-114">Open the project's **Properties** page.</span></span> <span data-ttu-id="6d443-115">如需詳細資訊，請參閱[專案設計工具、建置頁 (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)。</span><span class="sxs-lookup"><span data-stu-id="6d443-115">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2.  <span data-ttu-id="6d443-116">按一下 [建置] 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="6d443-116">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="6d443-117">按一下 [ **進階** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="6d443-117">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="6d443-118">修改 [檢查算術溢位/反向溢位] 屬性。</span><span class="sxs-lookup"><span data-stu-id="6d443-118">Modify the **Check for arithmetic overflow/underflow** property.</span></span>  
  
 <span data-ttu-id="6d443-119">若要以程式設計方式存取這個編譯器選項，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>。</span><span class="sxs-lookup"><span data-stu-id="6d443-119">To access this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d443-120">範例</span><span class="sxs-lookup"><span data-stu-id="6d443-120">Example</span></span>  
 <span data-ttu-id="6d443-121">下列命令會編譯 `t2.cs`。</span><span class="sxs-lookup"><span data-stu-id="6d443-121">The following command compiles `t2.cs`.</span></span> <span data-ttu-id="6d443-122">在命令中使用 `-checked` 會指定檔案中不在 `checked` 或 `unchecked` 關鍵字範圍內且產生超出該資料型別範圍之值的任何整數算術陳述式，都會在執行階段導致例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6d443-122">The use of `-checked` in the command specifies that any integer arithmetic statement in the file that is not in the scope of a `checked` or `unchecked` keyword, and that results in a value that is outside the range of the data type, causes an exception at run time.</span></span>  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a><span data-ttu-id="6d443-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="6d443-123">See Also</span></span>  
 [<span data-ttu-id="6d443-124">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="6d443-124">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="6d443-125">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="6d443-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  

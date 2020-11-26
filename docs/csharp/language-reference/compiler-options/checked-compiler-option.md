---
description: -checked (C# 編譯器選項)
title: -checked (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /checked
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
ms.openlocfilehash: c92ad61b2f482631230e0e6aeb0af5716a4fcb61
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "91196828"
---
# <a name="-checked-c-compiler-options"></a><span data-ttu-id="b38ef-103">-checked (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="b38ef-103">-checked (C# Compiler Options)</span></span>

<span data-ttu-id="b38ef-104">**-checked** 選項會指定產生超出該資料類型範圍之值且不在 [checked](../keywords/checked.md) 或 [unchecked](../keywords/unchecked.md) 關鍵字範圍內的整數算術陳述式是否導致執行階段例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b38ef-104">The **-checked** option specifies whether an integer arithmetic statement that results in a value that is outside the range of the data type, and that is not in the scope of a [checked](../keywords/checked.md) or [unchecked](../keywords/unchecked.md) keyword, causes a run-time exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b38ef-105">語法</span><span class="sxs-lookup"><span data-stu-id="b38ef-105">Syntax</span></span>  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="b38ef-106">備註</span><span class="sxs-lookup"><span data-stu-id="b38ef-106">Remarks</span></span>  

 <span data-ttu-id="b38ef-107">在 `checked` 或 `unchecked` 關鍵字範圍內的整數算術陳述式不一定會有 **-checked** 選項的效果。</span><span class="sxs-lookup"><span data-stu-id="b38ef-107">An integer arithmetic statement that is in the scope of a `checked` or `unchecked` keyword is not subject to the effect of the **-checked** option.</span></span>  
  
 <span data-ttu-id="b38ef-108">如果不在 `checked` 或 `unchecked` 關鍵字範圍內的整數算術陳述式產生超出該資料類型範圍的值，並在編譯時使用 **-checked+** (或 **-checked**)，則該陳述式會在執行階段導致例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b38ef-108">If an integer arithmetic statement that is not in the scope of a `checked` or `unchecked` keyword results in a value outside the range of the data type, and **-checked+** (or **-checked**) is used in the compilation, that statement causes an exception at run time.</span></span> <span data-ttu-id="b38ef-109">如果在編譯時使用 **-checked-**，則該陳述式不會在執行階段導致例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b38ef-109">If **-checked-** is used in the compilation, that statement does not cause an exception at run time.</span></span>  
  
 <span data-ttu-id="b38ef-110">這個選項的預設值是 **-checked-**；溢位檢查已停用。</span><span class="sxs-lookup"><span data-stu-id="b38ef-110">The default value for this option is **-checked-**; overflow checking is disabled.</span></span>

 <span data-ttu-id="b38ef-111">有時候，用來建置大型應用程式的自動化工具會將 -checked 設定為 +。</span><span class="sxs-lookup"><span data-stu-id="b38ef-111">Sometimes, automated tools that are used to build large applications set -checked to +.</span></span> <span data-ttu-id="b38ef-112">一種使用 -checked- 的情況是透過指定 -checked- 來覆寫工具的全域預設值。</span><span class="sxs-lookup"><span data-stu-id="b38ef-112">One scenario for using -checked- is to override the tool's global default by specifying -checked-.</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="b38ef-113">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="b38ef-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="b38ef-114">開啟專案的 [屬性] 頁面。</span><span class="sxs-lookup"><span data-stu-id="b38ef-114">Open the project's **Properties** page.</span></span> <span data-ttu-id="b38ef-115">如需詳細資訊，請參閱[專案設計工具、建置頁 (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)。</span><span class="sxs-lookup"><span data-stu-id="b38ef-115">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2. <span data-ttu-id="b38ef-116">按一下 [建置] 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="b38ef-116">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="b38ef-117">按一下 [進階]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="b38ef-117">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="b38ef-118">修改 [ **算術溢** 位] 屬性的 [檢查]。</span><span class="sxs-lookup"><span data-stu-id="b38ef-118">Modify the **Check for arithmetic overflow** property.</span></span>  
  
 <span data-ttu-id="b38ef-119">若要以程式設計方式存取這個編譯器選項，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>。</span><span class="sxs-lookup"><span data-stu-id="b38ef-119">To access this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b38ef-120">範例</span><span class="sxs-lookup"><span data-stu-id="b38ef-120">Example</span></span>  

 <span data-ttu-id="b38ef-121">下列命令會編譯 `t2.cs`。</span><span class="sxs-lookup"><span data-stu-id="b38ef-121">The following command compiles `t2.cs`.</span></span> <span data-ttu-id="b38ef-122">在命令中使用 `-checked` 會指定檔案中不在 `checked` 或 `unchecked` 關鍵字範圍內且產生超出該資料型別範圍之值的任何整數算術陳述式，都會在執行階段導致例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b38ef-122">The use of `-checked` in the command specifies that any integer arithmetic statement in the file that is not in the scope of a `checked` or `unchecked` keyword, and that results in a value that is outside the range of the data type, causes an exception at run time.</span></span>  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a><span data-ttu-id="b38ef-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b38ef-123">See also</span></span>

- [<span data-ttu-id="b38ef-124">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="b38ef-124">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="b38ef-125">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="b38ef-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

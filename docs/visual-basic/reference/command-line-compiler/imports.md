---
title: -匯入 (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: 330a5e6821c9c76f3503a35a5a5eabf24c686b42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="-imports-visual-basic"></a><span data-ttu-id="55a4f-102">-匯入 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="55a4f-102">-imports (Visual Basic)</span></span>
<span data-ttu-id="55a4f-103">從指定的組件，匯入命名空間。</span><span class="sxs-lookup"><span data-stu-id="55a4f-103">Imports namespaces from a specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55a4f-104">語法</span><span class="sxs-lookup"><span data-stu-id="55a4f-104">Syntax</span></span>  
  
```  
-imports:namespaceList  
```  
  
## <a name="arguments"></a><span data-ttu-id="55a4f-105">引數</span><span class="sxs-lookup"><span data-stu-id="55a4f-105">Arguments</span></span>  
  
|<span data-ttu-id="55a4f-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="55a4f-106">Term</span></span>|<span data-ttu-id="55a4f-107">定義</span><span class="sxs-lookup"><span data-stu-id="55a4f-107">Definition</span></span>|  
|---|---|  
|`namespaceList`|<span data-ttu-id="55a4f-108">必要。</span><span class="sxs-lookup"><span data-stu-id="55a4f-108">Required.</span></span> <span data-ttu-id="55a4f-109">要匯入的命名空間的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="55a4f-109">Comma-delimited list of namespaces to be imported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55a4f-110">備註</span><span class="sxs-lookup"><span data-stu-id="55a4f-110">Remarks</span></span>  
 <span data-ttu-id="55a4f-111">`-imports`選項匯入目前的資料集的來源檔案，或從任何參考的組件內定義的命名空間。</span><span class="sxs-lookup"><span data-stu-id="55a4f-111">The `-imports` option imports any namespace defined within the current set of source files or from any referenced assembly.</span></span>  
  
 <span data-ttu-id="55a4f-112">使用指定的命名空間中的成員`-imports`可用來在編譯中的所有原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="55a4f-112">The members in a namespace specified with `-imports` are available to all source-code files in the compilation.</span></span> <span data-ttu-id="55a4f-113">使用[Imports 陳述式 （.NET 命名空間和類型）](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)單一原始程式碼檔案中使用命名空間。</span><span class="sxs-lookup"><span data-stu-id="55a4f-113">Use the [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to use a namespace in a single source-code file.</span></span>  
  
|<span data-ttu-id="55a4f-114">若要設定 Visual Studio 整合式的開發環境中匯入 /</span><span class="sxs-lookup"><span data-stu-id="55a4f-114">To set /imports in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="55a4f-115">1.在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="55a4f-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="55a4f-116">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="55a4f-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="55a4f-117">2.按一下 [參考] 節點。</span><span class="sxs-lookup"><span data-stu-id="55a4f-117">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="55a4f-118">3.旁邊的方塊中輸入命名空間名稱**加入使用者匯入** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="55a4f-118">3.  Enter the namespace name in the box beside the **Add User Import** button.</span></span><br /><span data-ttu-id="55a4f-119">4.按一下**加入使用者匯入** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="55a4f-119">4.  Click the **Add User Import** button.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="55a4f-120">範例</span><span class="sxs-lookup"><span data-stu-id="55a4f-120">Example</span></span>  
 <span data-ttu-id="55a4f-121">下列程式碼會編譯時`/imports:system.globalization`指定。</span><span class="sxs-lookup"><span data-stu-id="55a4f-121">The following code compiles when `/imports:system.globalization` is specified.</span></span> <span data-ttu-id="55a4f-122">未安裝，成功編譯需要任一`Imports System.Globalization`陳述式的原始程式碼檔案中，開頭是包含或做為完整限定屬性`System.Globalization.CultureInfo.CurrentCulture.Name`。</span><span class="sxs-lookup"><span data-stu-id="55a4f-122">Without it, successful compilation requires either that an `Imports System.Globalization` statement be included at the beginning of the source code file, or that the property be fully qualified as `System.Globalization.CultureInfo.CurrentCulture.Name`.</span></span> 
  
 [!code-vb[imports example](codesnippet/VisualBasic/imports_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="55a4f-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55a4f-123">See Also</span></span>  
 [<span data-ttu-id="55a4f-124">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="55a4f-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="55a4f-125">參考和 Imports 陳述式</span><span class="sxs-lookup"><span data-stu-id="55a4f-125">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [<span data-ttu-id="55a4f-126">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="55a4f-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

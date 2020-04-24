---
title: -imports
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: 2a1dd19189ff65413255b9bc137e1a7f0227bbe1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716654"
---
# <a name="-imports-visual-basic"></a><span data-ttu-id="fc989-102">-imports （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="fc989-102">-imports (Visual Basic)</span></span>
<span data-ttu-id="fc989-103">從指定的元件匯入命名空間。</span><span class="sxs-lookup"><span data-stu-id="fc989-103">Imports namespaces from a specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc989-104">語法</span><span class="sxs-lookup"><span data-stu-id="fc989-104">Syntax</span></span>  
  
```console  
-imports:namespaceList  
```  
  
## <a name="arguments"></a><span data-ttu-id="fc989-105">引數</span><span class="sxs-lookup"><span data-stu-id="fc989-105">Arguments</span></span>  
  
|<span data-ttu-id="fc989-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="fc989-106">Term</span></span>|<span data-ttu-id="fc989-107">定義</span><span class="sxs-lookup"><span data-stu-id="fc989-107">Definition</span></span>|  
|---|---|  
|`namespaceList`|<span data-ttu-id="fc989-108">必要。</span><span class="sxs-lookup"><span data-stu-id="fc989-108">Required.</span></span> <span data-ttu-id="fc989-109">要匯入的命名空間清單（以逗號分隔）。</span><span class="sxs-lookup"><span data-stu-id="fc989-109">Comma-delimited list of namespaces to be imported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc989-110">備註</span><span class="sxs-lookup"><span data-stu-id="fc989-110">Remarks</span></span>  
 <span data-ttu-id="fc989-111">`-imports`選項會匯入目前來源檔案集或任何參考元件中定義的任何命名空間。</span><span class="sxs-lookup"><span data-stu-id="fc989-111">The `-imports` option imports any namespace defined within the current set of source files or from any referenced assembly.</span></span>  
  
 <span data-ttu-id="fc989-112">使用`-imports`指定之命名空間中的成員，可供編譯中的所有原始程式碼檔案使用。</span><span class="sxs-lookup"><span data-stu-id="fc989-112">The members in a namespace specified with `-imports` are available to all source-code files in the compilation.</span></span> <span data-ttu-id="fc989-113">使用[Imports 語句（.Net 命名空間和類型）](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) ，在單一原始程式碼檔案中使用命名空間。</span><span class="sxs-lookup"><span data-stu-id="fc989-113">Use the [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to use a namespace in a single source-code file.</span></span>  
  
|<span data-ttu-id="fc989-114">若要在 Visual Studio 的整合式開發環境中設定匯入</span><span class="sxs-lookup"><span data-stu-id="fc989-114">To set -imports in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="fc989-115">1. 在**方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="fc989-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="fc989-116">按一下 [專案]\*\*\*\* 功能表上的 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fc989-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="fc989-117">2. 按一下 [**參考**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="fc989-117">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="fc989-118">3. 在 [**新增使用者匯入**] 按鈕旁邊的方塊中輸入命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="fc989-118">3.  Enter the namespace name in the box beside the **Add User Import** button.</span></span><br /><span data-ttu-id="fc989-119">4. 按一下 [**新增使用者匯入**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="fc989-119">4.  Click the **Add User Import** button.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fc989-120">範例</span><span class="sxs-lookup"><span data-stu-id="fc989-120">Example</span></span>  
 <span data-ttu-id="fc989-121">當指定時`-imports:system.globalization` ，下列程式碼會進行編譯。</span><span class="sxs-lookup"><span data-stu-id="fc989-121">The following code compiles when `-imports:system.globalization` is specified.</span></span> <span data-ttu-id="fc989-122">如果沒有它，成功的編譯就必須`Imports System.Globalization`在原始程式碼檔的開頭包含語句，或是屬性必須完整限定為`System.Globalization.CultureInfo.CurrentCulture.Name`。</span><span class="sxs-lookup"><span data-stu-id="fc989-122">Without it, successful compilation requires either that an `Imports System.Globalization` statement be included at the beginning of the source code file, or that the property be fully qualified as `System.Globalization.CultureInfo.CurrentCulture.Name`.</span></span>

```vb
Module Example
   Public Sub Main()
      Console.WriteLine($"The current culture is {CultureInfo.CurrentCulture.Name}")
   End Sub
End Module
```

## <a name="see-also"></a><span data-ttu-id="fc989-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc989-123">See also</span></span>

- [<span data-ttu-id="fc989-124">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="fc989-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="fc989-125">參考和 Imports 陳述式</span><span class="sxs-lookup"><span data-stu-id="fc989-125">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="fc989-126">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="fc989-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

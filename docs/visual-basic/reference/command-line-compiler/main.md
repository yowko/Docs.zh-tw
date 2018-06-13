---
title: -主要
ms.date: 03/13/2018
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51a527dfddd2b78ac1c0559420298a66eb4b63f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652918"
---
# <a name="-main"></a><span data-ttu-id="578be-102">-主要</span><span class="sxs-lookup"><span data-stu-id="578be-102">-main</span></span>
<span data-ttu-id="578be-103">指定包含 `Sub Main` 程序的類別或模組。</span><span class="sxs-lookup"><span data-stu-id="578be-103">Specifies the class or module that contains the `Sub Main` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="578be-104">語法</span><span class="sxs-lookup"><span data-stu-id="578be-104">Syntax</span></span>  
  
```  
-main:location  
```  
  
## <a name="arguments"></a><span data-ttu-id="578be-105">引數</span><span class="sxs-lookup"><span data-stu-id="578be-105">Arguments</span></span>  
 `location`  
 <span data-ttu-id="578be-106">必要。</span><span class="sxs-lookup"><span data-stu-id="578be-106">Required.</span></span> <span data-ttu-id="578be-107">類別或包含的模組名稱`Sub Main`程式啟動時要呼叫的程序。</span><span class="sxs-lookup"><span data-stu-id="578be-107">The name of the class or module that contains the `Sub Main` procedure to be called when the program starts.</span></span> <span data-ttu-id="578be-108">這可能是在表單中 **-主要： module**或 **-main:namespace.module**。</span><span class="sxs-lookup"><span data-stu-id="578be-108">This may be in the form **-main:module** or **-main:namespace.module**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="578be-109">備註</span><span class="sxs-lookup"><span data-stu-id="578be-109">Remarks</span></span>  
 <span data-ttu-id="578be-110">當您建立可執行檔或 Windows 可執行程式時，請使用此選項。</span><span class="sxs-lookup"><span data-stu-id="578be-110">Use this option when you create an executable file or Windows executable program.</span></span> <span data-ttu-id="578be-111">如果 **-主要**省略選項，編譯器就會搜尋有效的共用`Sub Main`所有公用類別和模組中。</span><span class="sxs-lookup"><span data-stu-id="578be-111">If the **-main** option is omitted, the compiler searches for a valid shared `Sub Main` in all public classes and modules.</span></span>  
  
 <span data-ttu-id="578be-112">請參閱[Main 程序，在 Visual Basic 中](../../../visual-basic/programming-guide/program-structure/main-procedure.md)的各種形式的討論`Main`程序。</span><span class="sxs-lookup"><span data-stu-id="578be-112">See [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) for a discussion of the various forms of the `Main` procedure.</span></span>  
  
 <span data-ttu-id="578be-113">當`location`是繼承自一個類別<xref:System.Windows.Forms.Form>，編譯器會提供預設值`Main`如果類別沒有啟動的應用程式的程序`Main`程序。</span><span class="sxs-lookup"><span data-stu-id="578be-113">When `location` is a class that inherits from <xref:System.Windows.Forms.Form>, the compiler provides a default `Main` procedure that starts the application if the class has no `Main` procedure.</span></span> <span data-ttu-id="578be-114">這可讓您在命令列開發環境中所建立的程式碼編譯。</span><span class="sxs-lookup"><span data-stu-id="578be-114">This lets you compile code at the command line that was created in the development environment.</span></span>  
  
 [!code-vb[VbVbalrCompiler#16](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/main_1.vb)]  
  
### <a name="to-set--main-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="578be-115">若要設定的主要 Visual Studio 整合式的開發環境中</span><span class="sxs-lookup"><span data-stu-id="578be-115">To set -main in the Visual Studio integrated development environment</span></span>  
  
1.  <span data-ttu-id="578be-116">在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="578be-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="578be-117">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="578be-117">On the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="578be-118">按一下 [應用程式]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="578be-118">Click the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="578be-119">請確定**啟用應用程式架構**未核取核取方塊。</span><span class="sxs-lookup"><span data-stu-id="578be-119">Make sure the **Enable application framework** check box is not checked.</span></span>  
  
4.  <span data-ttu-id="578be-120">修改中的值**啟始物件**方塊。</span><span class="sxs-lookup"><span data-stu-id="578be-120">Modify the value in the **Startup object** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="578be-121">範例</span><span class="sxs-lookup"><span data-stu-id="578be-121">Example</span></span>  
 <span data-ttu-id="578be-122">下列程式碼編譯`T2.vb`和`T3.vb`，並指定，`Sub Main`程序中將可以找到`Test2`類別。</span><span class="sxs-lookup"><span data-stu-id="578be-122">The following code compiles `T2.vb` and `T3.vb`, specifying that the `Sub Main` procedure will be found in the `Test2` class.</span></span>  
  
```console
vbc t2.vb t3.vb -main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="578be-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="578be-123">See Also</span></span>  
 [<span data-ttu-id="578be-124">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="578be-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="578be-125">-目標 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="578be-125">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="578be-126">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="578be-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="578be-127">在 Visual Basic 中的 main 程序</span><span class="sxs-lookup"><span data-stu-id="578be-127">Main Procedure in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/main-procedure.md)

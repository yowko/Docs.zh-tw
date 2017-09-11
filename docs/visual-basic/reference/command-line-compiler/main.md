---
title: "/main |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
caps.latest.revision: 19
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
ms.openlocfilehash: 61aa78e131ba8903035f630a540f49848f1acd3f
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="main"></a><span data-ttu-id="528e1-102">/main</span><span class="sxs-lookup"><span data-stu-id="528e1-102">/main</span></span>
<span data-ttu-id="528e1-103">指定類別或模組，其中包含`Sub Main`程序。</span><span class="sxs-lookup"><span data-stu-id="528e1-103">Specifies the class or module that contains the `Sub Main` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="528e1-104">語法</span><span class="sxs-lookup"><span data-stu-id="528e1-104">Syntax</span></span>  
  
```  
/main:location  
```  
  
## <a name="arguments"></a><span data-ttu-id="528e1-105">引數</span><span class="sxs-lookup"><span data-stu-id="528e1-105">Arguments</span></span>  
 `location`  
 <span data-ttu-id="528e1-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="528e1-106">Required.</span></span> <span data-ttu-id="528e1-107">類別或模組，其中包含完整限定性條件`Sub Main`在程式啟動時要呼叫的程序。</span><span class="sxs-lookup"><span data-stu-id="528e1-107">A full qualification to the class or module that contains the `Sub Main` procedure to be called when the program starts.</span></span> <span data-ttu-id="528e1-108">這可能是在表單中**/main:module**或**/main:namespace.module**。</span><span class="sxs-lookup"><span data-stu-id="528e1-108">This may be in the form **/main:module** or **/main:namespace.module**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="528e1-109">備註</span><span class="sxs-lookup"><span data-stu-id="528e1-109">Remarks</span></span>  
 <span data-ttu-id="528e1-110">當您建立可執行檔或 Windows 可執行程式時，請使用此選項。</span><span class="sxs-lookup"><span data-stu-id="528e1-110">Use this option when you create an executable file or Windows executable program.</span></span> <span data-ttu-id="528e1-111">如果**/main**省略選項，編譯器會搜尋有效的共用`Sub Main`所有公用類別和模組中。</span><span class="sxs-lookup"><span data-stu-id="528e1-111">If the **/main** option is omitted, the compiler searches for a valid shared `Sub Main` in all public classes and modules.</span></span>  
  
 <span data-ttu-id="528e1-112">請參閱[Main 程序，在 Visual Basic 中](../../../visual-basic/programming-guide/program-structure/main-procedure.md)的各種形式的討論`Main`程序。</span><span class="sxs-lookup"><span data-stu-id="528e1-112">See [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) for a discussion of the various forms of the `Main` procedure.</span></span>  
  
 <span data-ttu-id="528e1-113">當`location`是繼承自類別<xref:System.Windows.Forms.Form>，編譯器會提供預設值`Main`如果類別沒有啟動應用程式的程序`Main`程序。</xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="528e1-113">When `location` is a class that inherits from <xref:System.Windows.Forms.Form>, the compiler provides a default `Main` procedure that starts the application if the class has no `Main` procedure.</span></span> <span data-ttu-id="528e1-114">這可讓您在命令列在開發環境中所建立的程式碼編譯。</span><span class="sxs-lookup"><span data-stu-id="528e1-114">This lets you compile code at the command line that was created in the development environment.</span></span>  
  
 <span data-ttu-id="528e1-115">[!code-vb[VbVbalrCompiler #&16;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/main_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="528e1-115">[!code-vb[VbVbalrCompiler#16](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/main_1.vb)]</span></span>  
  
### <a name="to-set-main-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="528e1-116">在 Visual Studio 中設定 /main 整合式開發環境</span><span class="sxs-lookup"><span data-stu-id="528e1-116">To set /main in the Visual Studio integrated development environment</span></span>  
  
1.  <span data-ttu-id="528e1-117">在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="528e1-117">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="528e1-118">在**專案**] 功能表上，按一下 [**屬性**。</span><span class="sxs-lookup"><span data-stu-id="528e1-118">On the **Project** menu, click **Properties**.</span></span>  
  
     <span data-ttu-id="528e1-119">如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。</span><span class="sxs-lookup"><span data-stu-id="528e1-119">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="528e1-120">按一下 [應用程式] **** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="528e1-120">Click the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="528e1-121">請確定**啟用應用程式架構**未核取核取方塊。</span><span class="sxs-lookup"><span data-stu-id="528e1-121">Make sure the **Enable application framework** check box is not checked.</span></span>  
  
4.  <span data-ttu-id="528e1-122">修改中的值**啟始物件**方塊。</span><span class="sxs-lookup"><span data-stu-id="528e1-122">Modify the value in the **Startup object** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="528e1-123">範例</span><span class="sxs-lookup"><span data-stu-id="528e1-123">Example</span></span>  
 <span data-ttu-id="528e1-124">下列程式碼編譯`T2.vb`和`T3.vb`，並指定，`Sub Main`程序將位於`Test2`類別。</span><span class="sxs-lookup"><span data-stu-id="528e1-124">The following code compiles `T2.vb` and `T3.vb`, specifying that the `Sub Main` procedure will be found in the `Test2` class.</span></span>  
  
```  
vbc t2.vb t3.vb /main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="528e1-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="528e1-125">See Also</span></span>  
 <span data-ttu-id="528e1-126">[Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="528e1-126">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="528e1-127"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span><span class="sxs-lookup"><span data-stu-id="528e1-127"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span></span>  
<span data-ttu-id="528e1-128"> [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="528e1-128"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="528e1-129"> [NIB: Hello，World Visual Basic 版本](http://msdn.microsoft.com/en-us/9d030b60-e148-4366-a462-69532f02294c) </span><span class="sxs-lookup"><span data-stu-id="528e1-129"> [NIB: Visual Basic Version of Hello, World](http://msdn.microsoft.com/en-us/9d030b60-e148-4366-a462-69532f02294c) </span></span>  
<span data-ttu-id="528e1-130"> [在 Visual Basic 中的 main 程序](../../../visual-basic/programming-guide/program-structure/main-procedure.md)</span><span class="sxs-lookup"><span data-stu-id="528e1-130"> [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)</span></span>

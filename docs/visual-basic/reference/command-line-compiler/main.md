---
title: -主要
ms.date: 03/13/2018
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
ms.openlocfilehash: e1e636da1d277f80f58268b24b69802006eb8315
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966277"
---
# <a name="-main"></a><span data-ttu-id="1f844-102">-主要</span><span class="sxs-lookup"><span data-stu-id="1f844-102">-main</span></span>
<span data-ttu-id="1f844-103">指定包含 `Sub Main` 程序的類別或模組。</span><span class="sxs-lookup"><span data-stu-id="1f844-103">Specifies the class or module that contains the `Sub Main` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f844-104">語法</span><span class="sxs-lookup"><span data-stu-id="1f844-104">Syntax</span></span>  
  
```  
-main:location  
```  
  
## <a name="arguments"></a><span data-ttu-id="1f844-105">引數</span><span class="sxs-lookup"><span data-stu-id="1f844-105">Arguments</span></span>  
 `location`  
 <span data-ttu-id="1f844-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="1f844-106">Required.</span></span> <span data-ttu-id="1f844-107">名稱的類別或模組，其中包含`Sub Main`程式啟動時要呼叫的程序。</span><span class="sxs-lookup"><span data-stu-id="1f844-107">The name of the class or module that contains the `Sub Main` procedure to be called when the program starts.</span></span> <span data-ttu-id="1f844-108">這可能是在表單 **-主要： module**或是 **-main:namespace.module**。</span><span class="sxs-lookup"><span data-stu-id="1f844-108">This may be in the form **-main:module** or **-main:namespace.module**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f844-109">備註</span><span class="sxs-lookup"><span data-stu-id="1f844-109">Remarks</span></span>  
 <span data-ttu-id="1f844-110">當您建立可執行檔或 Windows 可執行程式時，請使用此選項。</span><span class="sxs-lookup"><span data-stu-id="1f844-110">Use this option when you create an executable file or Windows executable program.</span></span> <span data-ttu-id="1f844-111">如果 **-主要**略過選項，編譯器會搜尋有效的共用`Sub Main`所有公用類別和模組中。</span><span class="sxs-lookup"><span data-stu-id="1f844-111">If the **-main** option is omitted, the compiler searches for a valid shared `Sub Main` in all public classes and modules.</span></span>  
  
 <span data-ttu-id="1f844-112">請參閱[在 Visual Basic 中的 Main 程序](../../../visual-basic/programming-guide/program-structure/main-procedure.md)的各種形式的討論`Main`程序。</span><span class="sxs-lookup"><span data-stu-id="1f844-112">See [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) for a discussion of the various forms of the `Main` procedure.</span></span>  
  
 <span data-ttu-id="1f844-113">當`location`是一個類別，繼承自<xref:System.Windows.Forms.Form>，編譯器會提供預設值`Main`程序，啟動應用程式，如果類別沒有`Main`程序。</span><span class="sxs-lookup"><span data-stu-id="1f844-113">When `location` is a class that inherits from <xref:System.Windows.Forms.Form>, the compiler provides a default `Main` procedure that starts the application if the class has no `Main` procedure.</span></span> <span data-ttu-id="1f844-114">這可讓您在命令列建立開發環境中的程式碼編譯。</span><span class="sxs-lookup"><span data-stu-id="1f844-114">This lets you compile code at the command line that was created in the development environment.</span></span>  
  
 [!code-vb[VbVbalrCompiler#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#16)]  
  
### <a name="to-set--main-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="1f844-115">若要設定-主要 Visual Studio 整合式的開發環境</span><span class="sxs-lookup"><span data-stu-id="1f844-115">To set -main in the Visual Studio integrated development environment</span></span>  
  
1.  <span data-ttu-id="1f844-116">在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="1f844-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="1f844-117">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="1f844-117">On the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="1f844-118">按一下 [應用程式]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1f844-118">Click the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="1f844-119">請確定**啟用應用程式架構**未核取核取方塊。</span><span class="sxs-lookup"><span data-stu-id="1f844-119">Make sure the **Enable application framework** check box is not checked.</span></span>  
  
4.  <span data-ttu-id="1f844-120">修改中的值**啟始物件** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="1f844-120">Modify the value in the **Startup object** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f844-121">範例</span><span class="sxs-lookup"><span data-stu-id="1f844-121">Example</span></span>  
 <span data-ttu-id="1f844-122">下列程式碼會編譯`T2.vb`並`T3.vb`，並指定可`Sub Main`程序就會出現在`Test2`類別。</span><span class="sxs-lookup"><span data-stu-id="1f844-122">The following code compiles `T2.vb` and `T3.vb`, specifying that the `Sub Main` procedure will be found in the `Test2` class.</span></span>  
  
```console
vbc t2.vb t3.vb -main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="1f844-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f844-123">See also</span></span>
- [<span data-ttu-id="1f844-124">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="1f844-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="1f844-125">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1f844-125">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="1f844-126">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="1f844-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="1f844-127">在 Visual Basic 中的 main 程序</span><span class="sxs-lookup"><span data-stu-id="1f844-127">Main Procedure in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/main-procedure.md)

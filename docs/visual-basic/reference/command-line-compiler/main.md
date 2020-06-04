---
title: -main
ms.date: 03/13/2018
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
ms.openlocfilehash: 5530da4c784346df4a1088998b8d2027feee08e3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403157"
---
# <a name="-main"></a><span data-ttu-id="f5842-102">-main</span><span class="sxs-lookup"><span data-stu-id="f5842-102">-main</span></span>
<span data-ttu-id="f5842-103">指定包含 `Sub Main` 程序的類別或模組。</span><span class="sxs-lookup"><span data-stu-id="f5842-103">Specifies the class or module that contains the `Sub Main` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5842-104">語法</span><span class="sxs-lookup"><span data-stu-id="f5842-104">Syntax</span></span>  
  
```console  
-main:location  
```  
  
## <a name="arguments"></a><span data-ttu-id="f5842-105">引數</span><span class="sxs-lookup"><span data-stu-id="f5842-105">Arguments</span></span>  
 `location`  
 <span data-ttu-id="f5842-106">必要。</span><span class="sxs-lookup"><span data-stu-id="f5842-106">Required.</span></span> <span data-ttu-id="f5842-107">類別或模組的名稱，其中包含 `Sub Main` 程式啟動時要呼叫的程式。</span><span class="sxs-lookup"><span data-stu-id="f5842-107">The name of the class or module that contains the `Sub Main` procedure to be called when the program starts.</span></span> <span data-ttu-id="f5842-108">此格式可能為 **-main： module**或 **-main： namespace. 模組**。</span><span class="sxs-lookup"><span data-stu-id="f5842-108">This may be in the form **-main:module** or **-main:namespace.module**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5842-109">備註</span><span class="sxs-lookup"><span data-stu-id="f5842-109">Remarks</span></span>  
 <span data-ttu-id="f5842-110">當您建立可執行檔或 Windows 可執行程式時，請使用此選項。</span><span class="sxs-lookup"><span data-stu-id="f5842-110">Use this option when you create an executable file or Windows executable program.</span></span> <span data-ttu-id="f5842-111">如果省略 **-main**選項，編譯器會搜尋 `Sub Main` 所有公用類別和模組中的有效共用。</span><span class="sxs-lookup"><span data-stu-id="f5842-111">If the **-main** option is omitted, the compiler searches for a valid shared `Sub Main` in all public classes and modules.</span></span>  
  
 <span data-ttu-id="f5842-112">如需程式各種形式的討論，請參閱[Visual Basic 中的主要](../../programming-guide/program-structure/main-procedure.md)程式 `Main` 。</span><span class="sxs-lookup"><span data-stu-id="f5842-112">See [Main Procedure in Visual Basic](../../programming-guide/program-structure/main-procedure.md) for a discussion of the various forms of the `Main` procedure.</span></span>  
  
 <span data-ttu-id="f5842-113">當 `location` 是繼承自的類別時 <xref:System.Windows.Forms.Form> ，編譯器會提供 `Main` 啟動應用程式的預設程式（如果該類別沒有程式） `Main` 。</span><span class="sxs-lookup"><span data-stu-id="f5842-113">When `location` is a class that inherits from <xref:System.Windows.Forms.Form>, the compiler provides a default `Main` procedure that starts the application if the class has no `Main` procedure.</span></span> <span data-ttu-id="f5842-114">這可讓您在開發環境中建立的命令列編譯器代碼。</span><span class="sxs-lookup"><span data-stu-id="f5842-114">This lets you compile code at the command line that was created in the development environment.</span></span>  
  
 [!code-vb[VbVbalrCompiler#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#16)]  
  
### <a name="to-set--main-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="f5842-115">在 Visual Studio 整合式開發環境中設定-main</span><span class="sxs-lookup"><span data-stu-id="f5842-115">To set -main in the Visual Studio integrated development environment</span></span>  
  
1. <span data-ttu-id="f5842-116">在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="f5842-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="f5842-117">按一下 [專案]\*\*\*\* 功能表上的 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f5842-117">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="f5842-118">按一下 [應用程式] \*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f5842-118">Click the **Application** tab.</span></span>  
  
3. <span data-ttu-id="f5842-119">請確定未核取 [**啟用應用程式架構**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="f5842-119">Make sure the **Enable application framework** check box is not checked.</span></span>  
  
4. <span data-ttu-id="f5842-120">修改 [**啟始物件**] 方塊中的值。</span><span class="sxs-lookup"><span data-stu-id="f5842-120">Modify the value in the **Startup object** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5842-121">範例</span><span class="sxs-lookup"><span data-stu-id="f5842-121">Example</span></span>  
 <span data-ttu-id="f5842-122">下列程式碼 `T2.vb` 會編譯和 `T3.vb` ，並指定 `Sub Main` 要在類別中找到該程式 `Test2` 。</span><span class="sxs-lookup"><span data-stu-id="f5842-122">The following code compiles `T2.vb` and `T3.vb`, specifying that the `Sub Main` procedure will be found in the `Test2` class.</span></span>  
  
```console
vbc t2.vb t3.vb -main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="f5842-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5842-123">See also</span></span>

- [<span data-ttu-id="f5842-124">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="f5842-124">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="f5842-125">-target （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="f5842-125">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="f5842-126">編譯命令列的範例</span><span class="sxs-lookup"><span data-stu-id="f5842-126">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="f5842-127">Visual Basic 中的 Main 程序</span><span class="sxs-lookup"><span data-stu-id="f5842-127">Main Procedure in Visual Basic</span></span>](../../programming-guide/program-structure/main-procedure.md)

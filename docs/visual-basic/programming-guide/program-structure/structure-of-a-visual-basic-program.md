---
title: "Visual Basic 程式的結構 |Microsoft 文件"
ms.custom: 
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
- conditional compilation, Visual Basic
- program structure, Visual Basic
- procedures, structure
- Visual Basic code, program structure
ms.assetid: ad0c6531-d762-4c77-a700-de16b07b6119
caps.latest.revision: 17
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
ms.openlocfilehash: 3e16ea51d0f766fcb5866cde89e5384a153ac050
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="structure-of-a-visual-basic-program"></a><span data-ttu-id="22aff-102">Visual Basic 程式的結構</span><span class="sxs-lookup"><span data-stu-id="22aff-102">Structure of a Visual Basic Program</span></span>
<span data-ttu-id="22aff-103">A[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]程式並建立從標準建置組塊。</span><span class="sxs-lookup"><span data-stu-id="22aff-103">A [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] program is built up from standard building blocks.</span></span> <span data-ttu-id="22aff-104">A*方案*可以包含一或多個專案。</span><span class="sxs-lookup"><span data-stu-id="22aff-104">A *solution* comprises one or more projects.</span></span> <span data-ttu-id="22aff-105">A*專案*」 可以包含一或多個組件。</span><span class="sxs-lookup"><span data-stu-id="22aff-105">A *project* in turn can contain one or more assemblies.</span></span> <span data-ttu-id="22aff-106">每個*組件*編譯從一或多個原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="22aff-106">Each *assembly* is compiled from one or more source files.</span></span> <span data-ttu-id="22aff-107">A*原始程式檔*提供定義和實作的類別、 結構、 模組和介面，最後會包含所有的程式碼。</span><span class="sxs-lookup"><span data-stu-id="22aff-107">A *source file* provides the definition and implementation of classes, structures, modules, and interfaces, which ultimately contain all your code.</span></span>  
  
 <span data-ttu-id="22aff-108">如需有關這些建置組塊[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]程式，請參閱[方案和專案](https://docs.microsoft.com/visualstudio/ide/solutions-and-projects-in-visual-studio)和[組件和全域組件快取](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)。</span><span class="sxs-lookup"><span data-stu-id="22aff-108">For more information about these building blocks of a [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] program, see [Solutions and Projects](https://docs.microsoft.com/visualstudio/ide/solutions-and-projects-in-visual-studio) and [Assemblies and the Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md).</span></span>  
  
## <a name="file-level-programming-elements"></a><span data-ttu-id="22aff-109">檔案層級的程式設計項目</span><span class="sxs-lookup"><span data-stu-id="22aff-109">File-Level Programming Elements</span></span>  
 <span data-ttu-id="22aff-110">當您啟動專案或檔案，並開啟程式碼編輯器中時，您會看到一些程式碼已經位於正確位置，以及正確的順序。</span><span class="sxs-lookup"><span data-stu-id="22aff-110">When you start a project or file and open the code editor, you see some code already in place and in the correct order.</span></span> <span data-ttu-id="22aff-111">您撰寫任何程式碼應該依照下列順序︰</span><span class="sxs-lookup"><span data-stu-id="22aff-111">Any code that you write should follow the following sequence:</span></span>  
  
1.  <span data-ttu-id="22aff-112">`Option`陳述式</span><span class="sxs-lookup"><span data-stu-id="22aff-112">`Option` statements</span></span>  
  
2.  <span data-ttu-id="22aff-113">`Imports`陳述式</span><span class="sxs-lookup"><span data-stu-id="22aff-113">`Imports` statements</span></span>  
  
3.  <span data-ttu-id="22aff-114">`Namespace`陳述式和命名空間層級項目</span><span class="sxs-lookup"><span data-stu-id="22aff-114">`Namespace` statements and namespace-level elements</span></span>  
  
 <span data-ttu-id="22aff-115">如果您在不同的順序輸入陳述式，會造成編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="22aff-115">If you enter statements in a different order, compilation errors can result.</span></span>  
  
 <span data-ttu-id="22aff-116">程式也可以包含條件式編譯陳述式。</span><span class="sxs-lookup"><span data-stu-id="22aff-116">A program can also contain conditional compilation statements.</span></span> <span data-ttu-id="22aff-117">您可以顛倒這些原始程式檔之間的上述順序的陳述式中。</span><span class="sxs-lookup"><span data-stu-id="22aff-117">You can intersperse these in the source file among the statements of the preceding sequence.</span></span>  
  
### <a name="option-statements"></a><span data-ttu-id="22aff-118">選項陳述式</span><span class="sxs-lookup"><span data-stu-id="22aff-118">Option Statements</span></span>  
 <span data-ttu-id="22aff-119">`Option`陳述式會建立後續的程式碼，協助避免語法以及邏輯錯誤的基本規則。</span><span class="sxs-lookup"><span data-stu-id="22aff-119">`Option` statements establish ground rules for subsequent code, helping prevent syntax and logic errors.</span></span> <span data-ttu-id="22aff-120">[Option Explicit 陳述式](../../../visual-basic/language-reference/statements/option-explicit-statement.md)確保所有的變數會宣告和拼字是否正確，因此能減少偵錯的時間。</span><span class="sxs-lookup"><span data-stu-id="22aff-120">The [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md) ensures that all variables are declared and spelled correctly, which reduces debugging time.</span></span> <span data-ttu-id="22aff-121">[Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)可協助您減少可能會發生，當您使用不同的資料型別的變數之間的邏輯錯誤或資料遺失。</span><span class="sxs-lookup"><span data-stu-id="22aff-121">The [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) helps to minimize logic errors and data loss that can occur when you work between variables of different data types.</span></span> <span data-ttu-id="22aff-122">[選項比較陳述式](../../../visual-basic/language-reference/statements/option-compare-statement.md)指定方法的字串會互相比較，根據其`Binary`或`Text`值。</span><span class="sxs-lookup"><span data-stu-id="22aff-122">The [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md) specifies the way strings are compared to each other, based on either their `Binary` or `Text` values.</span></span>  
  
### <a name="imports-statements"></a><span data-ttu-id="22aff-123">Imports 陳述式</span><span class="sxs-lookup"><span data-stu-id="22aff-123">Imports Statements</span></span>  
 <span data-ttu-id="22aff-124">您可以包含[Imports 陳述式 （.NET 命名空間和類型）](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)匯入您的專案之外定義的名稱。</span><span class="sxs-lookup"><span data-stu-id="22aff-124">You can include an [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to import names defined outside your project.</span></span> <span data-ttu-id="22aff-125">`Imports`陳述式可讓您的程式碼，來參考類別和其他類型的匯入的命名空間內定義而不需要加以限定。</span><span class="sxs-lookup"><span data-stu-id="22aff-125">An `Imports` statement allows your code to refer to classes and other types defined within the imported namespace, without having to qualify them.</span></span> <span data-ttu-id="22aff-126">您可以使用最大數量`Imports`視陳述式。</span><span class="sxs-lookup"><span data-stu-id="22aff-126">You can use as many `Imports` statements as appropriate.</span></span> <span data-ttu-id="22aff-127">如需詳細資訊，請參閱[參考和 Imports 陳述式](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="22aff-127">For more information, see [References and the Imports Statement](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md).</span></span>  
  
### <a name="namespace-statements"></a><span data-ttu-id="22aff-128">命名空間陳述式</span><span class="sxs-lookup"><span data-stu-id="22aff-128">Namespace Statements</span></span>  
 <span data-ttu-id="22aff-129">命名空間可以協助您組織及分類以方便群組和存取程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="22aff-129">Namespaces help you organize and classify your programming elements for ease of grouping and accessing.</span></span> <span data-ttu-id="22aff-130">您使用[命名空間陳述式](../../../visual-basic/language-reference/statements/namespace-statement.md)來分類特定命名空間內的下列陳述式。</span><span class="sxs-lookup"><span data-stu-id="22aff-130">You use the [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md) to classify the following statements within a particular namespace.</span></span> <span data-ttu-id="22aff-131">如需詳細資訊，請參閱[在 Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="22aff-131">For more information, see [Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).</span></span>  
  
### <a name="conditional-compilation-statements"></a><span data-ttu-id="22aff-132">條件式編譯陳述式</span><span class="sxs-lookup"><span data-stu-id="22aff-132">Conditional Compilation Statements</span></span>  
 <span data-ttu-id="22aff-133">條件式編譯陳述式可以出現在原始程式檔的幾乎任何地方。</span><span class="sxs-lookup"><span data-stu-id="22aff-133">Conditional compilation statements can appear almost anywhere in your source file.</span></span> <span data-ttu-id="22aff-134">它們會導致程式碼来包含或排除在編譯時期，根據特定條件的組件。</span><span class="sxs-lookup"><span data-stu-id="22aff-134">They cause parts of your code to be included or excluded at compile time depending on certain conditions.</span></span> <span data-ttu-id="22aff-135">您也可以使用它們進行偵錯您的應用程式，因為條件式程式碼是偵錯模式中執行。</span><span class="sxs-lookup"><span data-stu-id="22aff-135">You can also use them for debugging your application, because conditional code runs in debugging mode only.</span></span> <span data-ttu-id="22aff-136">如需詳細資訊，請參閱[條件式編譯](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)。</span><span class="sxs-lookup"><span data-stu-id="22aff-136">For more information, see [Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md).</span></span>  
  
## <a name="namespace-level-programming-elements"></a><span data-ttu-id="22aff-137">命名空間層級的程式設計項目</span><span class="sxs-lookup"><span data-stu-id="22aff-137">Namespace-Level Programming Elements</span></span>  
 <span data-ttu-id="22aff-138">類別、 結構和模組包含原始程式檔中的所有程式碼。</span><span class="sxs-lookup"><span data-stu-id="22aff-138">Classes, structures, and modules contain all the code in your source file.</span></span> <span data-ttu-id="22aff-139">它們是*命名空間層級*項目，則可能會出現在命名空間或來源檔案層級。</span><span class="sxs-lookup"><span data-stu-id="22aff-139">They are *namespace-level* elements, which can appear within a namespace or at the source file level.</span></span> <span data-ttu-id="22aff-140">它們會保存所有其他程式設計項目的宣告。</span><span class="sxs-lookup"><span data-stu-id="22aff-140">They hold the declarations of all other programming elements.</span></span> <span data-ttu-id="22aff-141">介面，可定義項目簽章，但不提供任何實作，也會出現在模組層級。</span><span class="sxs-lookup"><span data-stu-id="22aff-141">Interfaces, which define element signatures but provide no implementation, also appear at module level.</span></span> <span data-ttu-id="22aff-142">如需有關模組層級元素的詳細資訊，請參閱下列各項︰</span><span class="sxs-lookup"><span data-stu-id="22aff-142">For more information on the module-level elements, see the following:</span></span>  
  
-   [<span data-ttu-id="22aff-143">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="22aff-143">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
-   [<span data-ttu-id="22aff-144">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="22aff-144">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
-   [<span data-ttu-id="22aff-145">Module 陳述式</span><span class="sxs-lookup"><span data-stu-id="22aff-145">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
-   [<span data-ttu-id="22aff-146">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="22aff-146">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 <span data-ttu-id="22aff-147">命名空間層級的資料元素會列舉和委派。</span><span class="sxs-lookup"><span data-stu-id="22aff-147">Data elements at namespace level are enumerations and delegates.</span></span>  
  
## <a name="module-level-programming-elements"></a><span data-ttu-id="22aff-148">模組層級的程式設計項目</span><span class="sxs-lookup"><span data-stu-id="22aff-148">Module-Level Programming Elements</span></span>  
 <span data-ttu-id="22aff-149">程序、 運算子、 屬性和事件是唯一的程式設計項目可包含可執行程式碼 （陳述式會在執行階段執行的動作）。</span><span class="sxs-lookup"><span data-stu-id="22aff-149">Procedures, operators, properties, and events are the only programming elements that can hold executable code (statements that perform actions at run time).</span></span> <span data-ttu-id="22aff-150">它們是*模組層級*的程式項目。</span><span class="sxs-lookup"><span data-stu-id="22aff-150">They are the *module-level* elements of your program.</span></span> <span data-ttu-id="22aff-151">如需有關程序層級元素的詳細資訊，請參閱下列各項︰</span><span class="sxs-lookup"><span data-stu-id="22aff-151">For more information on the procedure-level elements, see the following:</span></span>  
  
-   [<span data-ttu-id="22aff-152">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="22aff-152">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [<span data-ttu-id="22aff-153">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="22aff-153">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
-   [<span data-ttu-id="22aff-154">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="22aff-154">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [<span data-ttu-id="22aff-155">Operator 陳述式</span><span class="sxs-lookup"><span data-stu-id="22aff-155">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
-   [<span data-ttu-id="22aff-156">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="22aff-156">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [<span data-ttu-id="22aff-157">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="22aff-157">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 <span data-ttu-id="22aff-158">在模組層級的資料元素是變數、 常數、 列舉和委派。</span><span class="sxs-lookup"><span data-stu-id="22aff-158">Data elements at module level are variables, constants, enumerations, and delegates.</span></span>  
  
## <a name="procedure-level-programming-elements"></a><span data-ttu-id="22aff-159">程序層級的程式設計項目</span><span class="sxs-lookup"><span data-stu-id="22aff-159">Procedure-Level Programming Elements</span></span>  
 <span data-ttu-id="22aff-160">大部分的內容*程序層級*項目是構成您程式的執行階段程式碼的可執行陳述式。</span><span class="sxs-lookup"><span data-stu-id="22aff-160">Most of the contents of *procedure-level* elements are executable statements, which constitute the run-time code of your program.</span></span> <span data-ttu-id="22aff-161">所有的可執行程式碼必須在某些程序 (`Function`， `Sub`， `Operator`， `Get`， `Set`， `AddHandler`， `RemoveHandler`， `RaiseEvent`)。</span><span class="sxs-lookup"><span data-stu-id="22aff-161">All executable code must be in some procedure (`Function`, `Sub`, `Operator`, `Get`, `Set`, `AddHandler`, `RemoveHandler`, `RaiseEvent`).</span></span> <span data-ttu-id="22aff-162">如需詳細資訊，請參閱[陳述式](../../../visual-basic/programming-guide/language-features/statements.md)。</span><span class="sxs-lookup"><span data-stu-id="22aff-162">For more information, see [Statements](../../../visual-basic/programming-guide/language-features/statements.md).</span></span>  
  
 <span data-ttu-id="22aff-163">在程序層級的資料元素僅限於本機變數和常數。</span><span class="sxs-lookup"><span data-stu-id="22aff-163">Data elements at procedure level are limited to local variables and constants.</span></span>  
  
## <a name="the-main-procedure"></a><span data-ttu-id="22aff-164">主要程序</span><span class="sxs-lookup"><span data-stu-id="22aff-164">The Main Procedure</span></span>  
 <span data-ttu-id="22aff-165">`Main`程序是已載入您的應用程式時執行的第一個程式碼。</span><span class="sxs-lookup"><span data-stu-id="22aff-165">The `Main` procedure is the first code to run when your application has been loaded.</span></span> <span data-ttu-id="22aff-166">`Main`可做為起始點和應用程式的整體控制項。</span><span class="sxs-lookup"><span data-stu-id="22aff-166">`Main` serves as the starting point and overall control for your application.</span></span> <span data-ttu-id="22aff-167">有四種`Main`:</span><span class="sxs-lookup"><span data-stu-id="22aff-167">There are four varieties of `Main`:</span></span>  
  
-   `Sub Main()`  
  
-   `Sub Main(ByVal cmdArgs() As String)`  
  
-   `Function Main() As Integer`  
  
-   `Function Main(ByVal cmdArgs() As String) As Integer`  
  
 <span data-ttu-id="22aff-168">此程序的最常見的各種不同的是`Sub Main()`。</span><span class="sxs-lookup"><span data-stu-id="22aff-168">The most common variety of this procedure is `Sub Main()`.</span></span> <span data-ttu-id="22aff-169">如需詳細資訊，請參閱[Main 程序，在 Visual Basic 中](../../../visual-basic/programming-guide/program-structure/main-procedure.md)。</span><span class="sxs-lookup"><span data-stu-id="22aff-169">For more information, see [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22aff-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22aff-170">See Also</span></span>  
 <span data-ttu-id="22aff-171">[在 Visual Basic 中的 main 程序](../../../visual-basic/programming-guide/program-structure/main-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="22aff-171">[Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) </span></span>  
<span data-ttu-id="22aff-172"> [Visual Basic 命名慣例](../../../visual-basic/programming-guide/program-structure/naming-conventions.md) </span><span class="sxs-lookup"><span data-stu-id="22aff-172"> [Visual Basic Naming Conventions](../../../visual-basic/programming-guide/program-structure/naming-conventions.md) </span></span>  
<span data-ttu-id="22aff-173"> [Visual Basic 的限制](../../../visual-basic/programming-guide/program-structure/limitations.md)</span><span class="sxs-lookup"><span data-stu-id="22aff-173"> [Visual Basic Limitations](../../../visual-basic/programming-guide/program-structure/limitations.md)</span></span>

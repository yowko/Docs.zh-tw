---
title: Visual Basic 程式的結構
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], Visual Basic
- program structure [Visual Basic], Visual Basic
- procedures [Visual Basic], structure
- Visual Basic code, program structure
ms.assetid: ad0c6531-d762-4c77-a700-de16b07b6119
ms.openlocfilehash: 90bc1fd62a05f670424e1fac368376401d1030c0
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097770"
---
# <a name="structure-of-a-visual-basic-program"></a><span data-ttu-id="e95e2-102">Visual Basic 程式的結構</span><span class="sxs-lookup"><span data-stu-id="e95e2-102">Structure of a Visual Basic Program</span></span>

<span data-ttu-id="e95e2-103">Visual Basic 的程式是從標準建立區塊所建立。</span><span class="sxs-lookup"><span data-stu-id="e95e2-103">A Visual Basic program is built up from standard building blocks.</span></span> <span data-ttu-id="e95e2-104">*方案*包含一或多個專案。</span><span class="sxs-lookup"><span data-stu-id="e95e2-104">A *solution* comprises one or more projects.</span></span> <span data-ttu-id="e95e2-105">然後， *專案* 可以包含一或多個元件。</span><span class="sxs-lookup"><span data-stu-id="e95e2-105">A *project* in turn can contain one or more assemblies.</span></span> <span data-ttu-id="e95e2-106">每個元件都是從一或多個原始 *程式* 檔所編譯。</span><span class="sxs-lookup"><span data-stu-id="e95e2-106">Each *assembly* is compiled from one or more source files.</span></span> <span data-ttu-id="e95e2-107">*原始*程式檔提供類別、結構、模組和介面的定義和執行，這些類別、結構、模組和介面最後都會包含您的所有程式碼。</span><span class="sxs-lookup"><span data-stu-id="e95e2-107">A *source file* provides the definition and implementation of classes, structures, modules, and interfaces, which ultimately contain all your code.</span></span>  
  
 <span data-ttu-id="e95e2-108">如需 Visual Basic 程式的這些構成要素的詳細資訊，請參閱[.net 中](../../../standard/assembly/index.md)的[方案和專案](/visualstudio/ide/solutions-and-projects-in-visual-studio)和元件。</span><span class="sxs-lookup"><span data-stu-id="e95e2-108">For more information about these building blocks of a Visual Basic program, see [Solutions and Projects](/visualstudio/ide/solutions-and-projects-in-visual-studio) and [Assemblies in .NET](../../../standard/assembly/index.md).</span></span>  
  
## <a name="file-level-programming-elements"></a><span data-ttu-id="e95e2-109">檔案層級程式設計項目</span><span class="sxs-lookup"><span data-stu-id="e95e2-109">File-Level Programming Elements</span></span>  

 <span data-ttu-id="e95e2-110">當您啟動專案或檔案並開啟程式碼編輯器時，您會看到已有一些已在使用中的程式碼，並以正確的順序顯示。</span><span class="sxs-lookup"><span data-stu-id="e95e2-110">When you start a project or file and open the code editor, you see some code already in place and in the correct order.</span></span> <span data-ttu-id="e95e2-111">您撰寫的任何程式碼應該遵循下列順序：</span><span class="sxs-lookup"><span data-stu-id="e95e2-111">Any code that you write should follow the following sequence:</span></span>  
  
1. <span data-ttu-id="e95e2-112">`Option` 語句</span><span class="sxs-lookup"><span data-stu-id="e95e2-112">`Option` statements</span></span>  
  
2. <span data-ttu-id="e95e2-113">`Imports` 語句</span><span class="sxs-lookup"><span data-stu-id="e95e2-113">`Imports` statements</span></span>  
  
3. <span data-ttu-id="e95e2-114">`Namespace` 語句和命名空間層級元素</span><span class="sxs-lookup"><span data-stu-id="e95e2-114">`Namespace` statements and namespace-level elements</span></span>  
  
 <span data-ttu-id="e95e2-115">如果您以不同的順序輸入語句，則會產生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="e95e2-115">If you enter statements in a different order, compilation errors can result.</span></span>  
  
 <span data-ttu-id="e95e2-116">程式也可以包含條件式編譯語句。</span><span class="sxs-lookup"><span data-stu-id="e95e2-116">A program can also contain conditional compilation statements.</span></span> <span data-ttu-id="e95e2-117">您可以在原始程式檔中，于上述順序的語句之間散置這些檔案。</span><span class="sxs-lookup"><span data-stu-id="e95e2-117">You can intersperse these in the source file among the statements of the preceding sequence.</span></span>  
  
### <a name="option-statements"></a><span data-ttu-id="e95e2-118">Option 語句</span><span class="sxs-lookup"><span data-stu-id="e95e2-118">Option Statements</span></span>  

 <span data-ttu-id="e95e2-119">`Option` 語句會建立後續程式碼的基礎規則，以協助防止語法和邏輯錯誤。</span><span class="sxs-lookup"><span data-stu-id="e95e2-119">`Option` statements establish ground rules for subsequent code, helping prevent syntax and logic errors.</span></span> <span data-ttu-id="e95e2-120">[Option Explicit 語句](../../language-reference/statements/option-explicit-statement.md)可確保所有變數都已宣告且拼寫正確，以減少調試時間。</span><span class="sxs-lookup"><span data-stu-id="e95e2-120">The [Option Explicit Statement](../../language-reference/statements/option-explicit-statement.md) ensures that all variables are declared and spelled correctly, which reduces debugging time.</span></span> <span data-ttu-id="e95e2-121">[Option Strict 語句](../../language-reference/statements/option-strict-statement.md)有助於將當您在不同資料類型的變數之間工作時，可能發生的邏輯錯誤和資料遺失降至最低。</span><span class="sxs-lookup"><span data-stu-id="e95e2-121">The [Option Strict Statement](../../language-reference/statements/option-strict-statement.md) helps to minimize logic errors and data loss that can occur when you work between variables of different data types.</span></span> <span data-ttu-id="e95e2-122">[Option Compare 語句](../../language-reference/statements/option-compare-statement.md)會根據其或值指定字串的比較方式 `Binary` `Text` 。</span><span class="sxs-lookup"><span data-stu-id="e95e2-122">The [Option Compare Statement](../../language-reference/statements/option-compare-statement.md) specifies the way strings are compared to each other, based on either their `Binary` or `Text` values.</span></span>  
  
### <a name="imports-statements"></a><span data-ttu-id="e95e2-123">Imports 語句</span><span class="sxs-lookup"><span data-stu-id="e95e2-123">Imports Statements</span></span>  

 <span data-ttu-id="e95e2-124">您可以包含 [Imports 語句 ( .Net 命名空間和類型) ](../../language-reference/statements/imports-statement-net-namespace-and-type.md) ，以匯入在專案之外定義的名稱。</span><span class="sxs-lookup"><span data-stu-id="e95e2-124">You can include an [Imports Statement (.NET Namespace and Type)](../../language-reference/statements/imports-statement-net-namespace-and-type.md) to import names defined outside your project.</span></span> <span data-ttu-id="e95e2-125">`Imports`語句可讓您的程式碼參考已匯入之命名空間內所定義的類別和其他類型，而不需要限定它們。</span><span class="sxs-lookup"><span data-stu-id="e95e2-125">An `Imports` statement allows your code to refer to classes and other types defined within the imported namespace, without having to qualify them.</span></span> <span data-ttu-id="e95e2-126">您可以視需要使用任意數目的 `Imports` 語句。</span><span class="sxs-lookup"><span data-stu-id="e95e2-126">You can use as many `Imports` statements as appropriate.</span></span> <span data-ttu-id="e95e2-127">如需詳細資訊，請參閱 [參考和 Imports 語句](references-and-the-imports-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="e95e2-127">For more information, see [References and the Imports Statement](references-and-the-imports-statement.md).</span></span>  
  
### <a name="namespace-statements"></a><span data-ttu-id="e95e2-128">Namespace 語句</span><span class="sxs-lookup"><span data-stu-id="e95e2-128">Namespace Statements</span></span>  

 <span data-ttu-id="e95e2-129">命名空間可協助您組織和分類程式設計專案，以簡化群組和存取。</span><span class="sxs-lookup"><span data-stu-id="e95e2-129">Namespaces help you organize and classify your programming elements for ease of grouping and accessing.</span></span> <span data-ttu-id="e95e2-130">您可以使用 [Namespace 語句](../../language-reference/statements/namespace-statement.md) 來分類特定命名空間內的下列語句。</span><span class="sxs-lookup"><span data-stu-id="e95e2-130">You use the [Namespace Statement](../../language-reference/statements/namespace-statement.md) to classify the following statements within a particular namespace.</span></span> <span data-ttu-id="e95e2-131">如需詳細資訊，請參閱 [Visual Basic 中的命名空間](namespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="e95e2-131">For more information, see [Namespaces in Visual Basic](namespaces.md).</span></span>  
  
### <a name="conditional-compilation-statements"></a><span data-ttu-id="e95e2-132">條件式編譯語句</span><span class="sxs-lookup"><span data-stu-id="e95e2-132">Conditional Compilation Statements</span></span>  

 <span data-ttu-id="e95e2-133">條件式編譯語句幾乎可以出現在原始程式檔中的任何位置。</span><span class="sxs-lookup"><span data-stu-id="e95e2-133">Conditional compilation statements can appear almost anywhere in your source file.</span></span> <span data-ttu-id="e95e2-134">它們會根據特定條件，在編譯時期包含或排除部分程式碼。</span><span class="sxs-lookup"><span data-stu-id="e95e2-134">They cause parts of your code to be included or excluded at compile time depending on certain conditions.</span></span> <span data-ttu-id="e95e2-135">您也可以使用它們來對應用程式進行偵錯工具，因為條件式程式碼只會在偵錯工具模式中執行。</span><span class="sxs-lookup"><span data-stu-id="e95e2-135">You can also use them for debugging your application, because conditional code runs in debugging mode only.</span></span> <span data-ttu-id="e95e2-136">如需詳細資訊，請參閱 [條件式編譯](conditional-compilation.md)。</span><span class="sxs-lookup"><span data-stu-id="e95e2-136">For more information, see [Conditional Compilation](conditional-compilation.md).</span></span>  
  
## <a name="namespace-level-programming-elements"></a><span data-ttu-id="e95e2-137">命名空間層級的程式設計項目</span><span class="sxs-lookup"><span data-stu-id="e95e2-137">Namespace-Level Programming Elements</span></span>  

 <span data-ttu-id="e95e2-138">類別、結構和模組包含原始程式檔中的所有程式碼。</span><span class="sxs-lookup"><span data-stu-id="e95e2-138">Classes, structures, and modules contain all the code in your source file.</span></span> <span data-ttu-id="e95e2-139">它們是 *命名空間層級* 的元素，可以出現在命名空間或來源檔案層級。</span><span class="sxs-lookup"><span data-stu-id="e95e2-139">They are *namespace-level* elements, which can appear within a namespace or at the source file level.</span></span> <span data-ttu-id="e95e2-140">它們包含所有其他程式設計專案的宣告。</span><span class="sxs-lookup"><span data-stu-id="e95e2-140">They hold the declarations of all other programming elements.</span></span> <span data-ttu-id="e95e2-141">介面（定義專案簽章但不提供任何實作為）也會出現在模組層級上。</span><span class="sxs-lookup"><span data-stu-id="e95e2-141">Interfaces, which define element signatures but provide no implementation, also appear at module level.</span></span> <span data-ttu-id="e95e2-142">如需模組層級元素的詳細資訊，請參閱下列各項：</span><span class="sxs-lookup"><span data-stu-id="e95e2-142">For more information on the module-level elements, see the following:</span></span>  
  
- [<span data-ttu-id="e95e2-143">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="e95e2-143">Class Statement</span></span>](../../language-reference/statements/class-statement.md)  
  
- [<span data-ttu-id="e95e2-144">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="e95e2-144">Structure Statement</span></span>](../../language-reference/statements/structure-statement.md)  
  
- [<span data-ttu-id="e95e2-145">Module 陳述式</span><span class="sxs-lookup"><span data-stu-id="e95e2-145">Module Statement</span></span>](../../language-reference/statements/module-statement.md)  
  
- [<span data-ttu-id="e95e2-146">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="e95e2-146">Interface Statement</span></span>](../../language-reference/statements/interface-statement.md)  
  
 <span data-ttu-id="e95e2-147">命名空間層級的資料元素為列舉和委派。</span><span class="sxs-lookup"><span data-stu-id="e95e2-147">Data elements at namespace level are enumerations and delegates.</span></span>  
  
## <a name="module-level-programming-elements"></a><span data-ttu-id="e95e2-148">模組層級程式設計項目</span><span class="sxs-lookup"><span data-stu-id="e95e2-148">Module-Level Programming Elements</span></span>  

 <span data-ttu-id="e95e2-149">程式、運算子、屬性和事件是唯一可保存可執行程式碼 (語句的程式設計項目，這些專案會在執行時間) 執行動作。</span><span class="sxs-lookup"><span data-stu-id="e95e2-149">Procedures, operators, properties, and events are the only programming elements that can hold executable code (statements that perform actions at run time).</span></span> <span data-ttu-id="e95e2-150">它們是您程式的 *模組層級* 元素。</span><span class="sxs-lookup"><span data-stu-id="e95e2-150">They are the *module-level* elements of your program.</span></span> <span data-ttu-id="e95e2-151">如需程式層級元素的詳細資訊，請參閱下列各項：</span><span class="sxs-lookup"><span data-stu-id="e95e2-151">For more information on the procedure-level elements, see the following:</span></span>  
  
- [<span data-ttu-id="e95e2-152">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="e95e2-152">Function Statement</span></span>](../../language-reference/statements/function-statement.md)  
  
- [<span data-ttu-id="e95e2-153">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="e95e2-153">Sub Statement</span></span>](../../language-reference/statements/sub-statement.md)  
  
- [<span data-ttu-id="e95e2-154">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="e95e2-154">Declare Statement</span></span>](../../language-reference/statements/declare-statement.md)  
  
- [<span data-ttu-id="e95e2-155">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="e95e2-155">Operator Statement</span></span>](../../language-reference/statements/operator-statement.md)  
  
- [<span data-ttu-id="e95e2-156">Property Statement</span><span class="sxs-lookup"><span data-stu-id="e95e2-156">Property Statement</span></span>](../../language-reference/statements/property-statement.md)  
  
- [<span data-ttu-id="e95e2-157">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="e95e2-157">Event Statement</span></span>](../../language-reference/statements/event-statement.md)  
  
 <span data-ttu-id="e95e2-158">模組層級的資料元素為變數、常數、列舉和委派。</span><span class="sxs-lookup"><span data-stu-id="e95e2-158">Data elements at module level are variables, constants, enumerations, and delegates.</span></span>  
  
## <a name="procedure-level-programming-elements"></a><span data-ttu-id="e95e2-159">程式層級程式設計項目</span><span class="sxs-lookup"><span data-stu-id="e95e2-159">Procedure-Level Programming Elements</span></span>  

 <span data-ttu-id="e95e2-160">程式 *層級* 元素的大部分內容都是可執行檔語句，其構成程式的執行時間程式碼。</span><span class="sxs-lookup"><span data-stu-id="e95e2-160">Most of the contents of *procedure-level* elements are executable statements, which constitute the run-time code of your program.</span></span> <span data-ttu-id="e95e2-161">所有可執行程式碼都必須在某些程式中， (、、、、、、 `Function` `Sub` `Operator` `Get` `Set` `AddHandler` `RemoveHandler` `RaiseEvent`) 。</span><span class="sxs-lookup"><span data-stu-id="e95e2-161">All executable code must be in some procedure (`Function`, `Sub`, `Operator`, `Get`, `Set`, `AddHandler`, `RemoveHandler`, `RaiseEvent`).</span></span> <span data-ttu-id="e95e2-162">如需詳細資訊，請參閱[陳述式](../language-features/statements.md)。</span><span class="sxs-lookup"><span data-stu-id="e95e2-162">For more information, see [Statements](../language-features/statements.md).</span></span>  
  
 <span data-ttu-id="e95e2-163">程式層級的資料元素限制為本機變數和常數。</span><span class="sxs-lookup"><span data-stu-id="e95e2-163">Data elements at procedure level are limited to local variables and constants.</span></span>  
  
## <a name="the-main-procedure"></a><span data-ttu-id="e95e2-164">主要程式</span><span class="sxs-lookup"><span data-stu-id="e95e2-164">The Main Procedure</span></span>  

 <span data-ttu-id="e95e2-165">`Main`程式是在載入應用程式時要執行的第一個程式碼。</span><span class="sxs-lookup"><span data-stu-id="e95e2-165">The `Main` procedure is the first code to run when your application has been loaded.</span></span> <span data-ttu-id="e95e2-166">`Main` 作為應用程式的起點和整體控制。</span><span class="sxs-lookup"><span data-stu-id="e95e2-166">`Main` serves as the starting point and overall control for your application.</span></span> <span data-ttu-id="e95e2-167">有四種種類 `Main` ：</span><span class="sxs-lookup"><span data-stu-id="e95e2-167">There are four varieties of `Main`:</span></span>  
  
- `Sub Main()`  
  
- `Sub Main(ByVal cmdArgs() As String)`  
  
- `Function Main() As Integer`  
  
- `Function Main(ByVal cmdArgs() As String) As Integer`  
  
 <span data-ttu-id="e95e2-168">此程式最常見的不同之處為 `Sub Main()` 。</span><span class="sxs-lookup"><span data-stu-id="e95e2-168">The most common variety of this procedure is `Sub Main()`.</span></span> <span data-ttu-id="e95e2-169">如需詳細資訊，請參閱 [Visual Basic 中的 Main](main-procedure.md)程式。</span><span class="sxs-lookup"><span data-stu-id="e95e2-169">For more information, see [Main Procedure in Visual Basic](main-procedure.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e95e2-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e95e2-170">See also</span></span>

- [<span data-ttu-id="e95e2-171">Visual Basic 中的 Main 程序</span><span class="sxs-lookup"><span data-stu-id="e95e2-171">Main Procedure in Visual Basic</span></span>](main-procedure.md)
- [<span data-ttu-id="e95e2-172">Visual Basic 命名慣例</span><span class="sxs-lookup"><span data-stu-id="e95e2-172">Visual Basic Naming Conventions</span></span>](naming-conventions.md)
- [<span data-ttu-id="e95e2-173">Visual Basic 的限制</span><span class="sxs-lookup"><span data-stu-id="e95e2-173">Visual Basic Limitations</span></span>](limitations.md)

---
title: 程式結構和程式碼慣例 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions
- Visual Basic code, coding conventions
- coding conventions [Visual Basic], Visual Basic
- programs [Visual Basic], structure
- program structure [Visual Basic]
- naming conventions [Visual Basic], Visual Basic
- best practices [Visual Basic], coding conventions
- conventions [Visual Basic], Visual Basic coding
- Visual Basic code
- programming [Visual Basic], Visual Basic coding conventions
ms.assetid: dd9be76f-6944-4e78-ad72-0b6084a3fc13
ms.openlocfilehash: b79e339ebe81a7228a02837e5c0c23c80a8132e9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916938"
---
# <a name="program-structure-and-code-conventions-visual-basic"></a><span data-ttu-id="039a7-102">程式結構和程式碼慣例 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="039a7-102">Program Structure and Code Conventions (Visual Basic)</span></span>
<span data-ttu-id="039a7-103">本節介紹典型的 Visual Basic 程式結構，提供簡單的 Visual Basic 程式，"Hello，World"，並討論 Visual Basic 程式碼慣例。</span><span class="sxs-lookup"><span data-stu-id="039a7-103">This section introduces the typical Visual Basic program structure, provides a simple Visual Basic program, "Hello, World", and discusses Visual Basic code conventions.</span></span> <span data-ttu-id="039a7-104">程式碼慣例是建議，焦點不在程式的邏輯，但在其實體結構和外觀。</span><span class="sxs-lookup"><span data-stu-id="039a7-104">Code conventions are suggestions that focus not on a program's logic but on its physical structure and appearance.</span></span> <span data-ttu-id="039a7-105">遵守這些建議可讓您更輕鬆地閱讀、 瞭解並維護程式碼。</span><span class="sxs-lookup"><span data-stu-id="039a7-105">Following them makes your code easier to read, understand, and maintain.</span></span> <span data-ttu-id="039a7-106">可以包含其他項目程式碼慣例：</span><span class="sxs-lookup"><span data-stu-id="039a7-106">Code conventions can include, among others:</span></span>  
  
- <span data-ttu-id="039a7-107">標籤與註解的程式碼的標準化的格式。</span><span class="sxs-lookup"><span data-stu-id="039a7-107">Standardized formats for labeling and commenting code.</span></span>  
  
- <span data-ttu-id="039a7-108">間距、 格式與縮排程式碼的指導方針。</span><span class="sxs-lookup"><span data-stu-id="039a7-108">Guidelines for spacing, formatting, and indenting code.</span></span>  
  
- <span data-ttu-id="039a7-109">物件、 變數和程序的命名慣例。</span><span class="sxs-lookup"><span data-stu-id="039a7-109">Naming conventions for objects, variables, and procedures.</span></span>  
  
 <span data-ttu-id="039a7-110">下列主題提供了一套程式設計指南針對 Visual Basic 程式，以及正確使用方式的範例。</span><span class="sxs-lookup"><span data-stu-id="039a7-110">The following topics present a set of programming guidelines for Visual Basic programs, along with examples of good usage.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="039a7-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="039a7-111">In This Section</span></span>  
 [<span data-ttu-id="039a7-112">Visual Basic 程式的結構</span><span class="sxs-lookup"><span data-stu-id="039a7-112">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 <span data-ttu-id="039a7-113">提供 Visual Basic 程式構成之元素的概觀。</span><span class="sxs-lookup"><span data-stu-id="039a7-113">Provides an overview of the elements that make up a Visual Basic program.</span></span>  
  
 [<span data-ttu-id="039a7-114">在 Visual Basic 中的 main 程序</span><span class="sxs-lookup"><span data-stu-id="039a7-114">Main Procedure in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/main-procedure.md)  
 <span data-ttu-id="039a7-115">討論可作為起始點和整體控制您的應用程式的程序。</span><span class="sxs-lookup"><span data-stu-id="039a7-115">Discusses the procedure that serves as the starting point and overall control for your application.</span></span>  
  
 [<span data-ttu-id="039a7-116">參考和 Imports 陳述式</span><span class="sxs-lookup"><span data-stu-id="039a7-116">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 <span data-ttu-id="039a7-117">討論如何參考其他組件中的物件。</span><span class="sxs-lookup"><span data-stu-id="039a7-117">Discusses how to reference objects in other assemblies.</span></span>  
  
 [<span data-ttu-id="039a7-118">在 Visual Basic 中的命名空間</span><span class="sxs-lookup"><span data-stu-id="039a7-118">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 <span data-ttu-id="039a7-119">描述如何命名空間可組織組件內的物件。</span><span class="sxs-lookup"><span data-stu-id="039a7-119">Describes how namespaces organize objects within assemblies.</span></span>  
  
 [<span data-ttu-id="039a7-120">Visual Basic 命名慣例</span><span class="sxs-lookup"><span data-stu-id="039a7-120">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 <span data-ttu-id="039a7-121">包含命名程序、 常數、 變數、 引數和物件的一般指導方針。</span><span class="sxs-lookup"><span data-stu-id="039a7-121">Includes general guidelines for naming procedures, constants, variables, arguments, and objects.</span></span>  
  
 [<span data-ttu-id="039a7-122">Visual Basic 編碼慣例</span><span class="sxs-lookup"><span data-stu-id="039a7-122">Visual Basic Coding Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)  
 <span data-ttu-id="039a7-123">檢閱指導方針來開發這份文件中的範例。</span><span class="sxs-lookup"><span data-stu-id="039a7-123">Reviews the guidelines used in developing the samples in this documentation.</span></span>  
  
 [<span data-ttu-id="039a7-124">條件式編譯</span><span class="sxs-lookup"><span data-stu-id="039a7-124">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 <span data-ttu-id="039a7-125">說明如何選擇性地編譯的程式碼的特定區塊，而使編譯器忽略其他項目。</span><span class="sxs-lookup"><span data-stu-id="039a7-125">Describes how to compile particular blocks of code selectively while directing the compiler to ignore others.</span></span>  
  
 [<span data-ttu-id="039a7-126">如何：在程式碼內中斷和合併陳述式</span><span class="sxs-lookup"><span data-stu-id="039a7-126">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 <span data-ttu-id="039a7-127">示範如何分割成多行長的陳述式和合併在同一行的簡短陳述式。</span><span class="sxs-lookup"><span data-stu-id="039a7-127">Shows how to divide long statements into multiple lines and combine short statements on one line.</span></span>  
  
 [<span data-ttu-id="039a7-128">如何：摺疊和隱藏程式碼區段</span><span class="sxs-lookup"><span data-stu-id="039a7-128">How to: Collapse and Hide Sections of Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)  
 <span data-ttu-id="039a7-129">顯示如何摺疊和隱藏在 Visual Basic 中的程式碼區段的程式碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="039a7-129">Shows how to collapse and hide sections of code in the Visual Basic code editor.</span></span>  
  
 [<span data-ttu-id="039a7-130">如何：標記陳述式</span><span class="sxs-lookup"><span data-stu-id="039a7-130">How to: Label Statements</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)  
 <span data-ttu-id="039a7-131">示範如何標記一行程式碼來加以識別，以便使用陳述式這類`On Error Goto`。</span><span class="sxs-lookup"><span data-stu-id="039a7-131">Shows how to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 [<span data-ttu-id="039a7-132">程式碼中的特殊字元</span><span class="sxs-lookup"><span data-stu-id="039a7-132">Special Characters in Code</span></span>](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 <span data-ttu-id="039a7-133">顯示方式和位置來使用非數字和非字母字元。</span><span class="sxs-lookup"><span data-stu-id="039a7-133">Shows how and where to use non-numeric and non-alphabetic characters.</span></span>  
  
 [<span data-ttu-id="039a7-134">程式碼中的註解</span><span class="sxs-lookup"><span data-stu-id="039a7-134">Comments in Code</span></span>](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)  
 <span data-ttu-id="039a7-135">討論如何將描述性註解新增至您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="039a7-135">Discusses how to add descriptive comments to your code.</span></span>  
  
 [<span data-ttu-id="039a7-136">程式碼中以關鍵字做為項目名稱</span><span class="sxs-lookup"><span data-stu-id="039a7-136">Keywords as Element Names in Code</span></span>](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 <span data-ttu-id="039a7-137">描述如何使用方括號 (`[]`) 來分隔同時也是 Visual Basic 關鍵字的變數名稱。</span><span class="sxs-lookup"><span data-stu-id="039a7-137">Describes how to use brackets (`[]`) to delimit variable names that are also Visual Basic keywords.</span></span>  
  
 [<span data-ttu-id="039a7-138">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="039a7-138">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 <span data-ttu-id="039a7-139">說明 Visual Basic 程式的項目參考的各種方式。</span><span class="sxs-lookup"><span data-stu-id="039a7-139">Describes various ways to refer to elements of a Visual Basic program.</span></span>  
  
 [<span data-ttu-id="039a7-140">Visual Basic 的限制</span><span class="sxs-lookup"><span data-stu-id="039a7-140">Visual Basic Limitations</span></span>](../../../visual-basic/programming-guide/program-structure/limitations.md)  
 <span data-ttu-id="039a7-141">討論 Visual Basic 中的已知編碼限制移除。</span><span class="sxs-lookup"><span data-stu-id="039a7-141">Discusses the removal of known coding limits within Visual Basic.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="039a7-142">相關章節</span><span class="sxs-lookup"><span data-stu-id="039a7-142">Related Sections</span></span>  
 [<span data-ttu-id="039a7-143">印刷樣式與程式碼慣例</span><span class="sxs-lookup"><span data-stu-id="039a7-143">Typographic and Code Conventions</span></span>](../../../visual-basic/language-reference/typographic-and-code-conventions.md)  
 <span data-ttu-id="039a7-144">適用於 Visual Basic 中提供標準的程式碼撰寫慣例。</span><span class="sxs-lookup"><span data-stu-id="039a7-144">Provides standard coding conventions for Visual Basic.</span></span>  
  
 [<span data-ttu-id="039a7-145">撰寫程式碼</span><span class="sxs-lookup"><span data-stu-id="039a7-145">Writing Code</span></span>](/visualstudio/ide/writing-code-in-the-code-and-text-editor)  
 <span data-ttu-id="039a7-146">說明功能，可讓您更輕鬆地撰寫並管理您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="039a7-146">Describes features that make it easier for you to write and manage your code.</span></span>

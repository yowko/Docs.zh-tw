---
title: "程式結構和程式碼慣例 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b38ba9623a20dcd1be4bc96f4aff1eb646b0a053
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="program-structure-and-code-conventions-visual-basic"></a><span data-ttu-id="42dce-102">程式結構和程式碼慣例 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="42dce-102">Program Structure and Code Conventions (Visual Basic)</span></span>
<span data-ttu-id="42dce-103">本節將介紹典型[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]程式結構，提供簡單[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]程式，"Hello World"，並討論[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]程式碼慣例。</span><span class="sxs-lookup"><span data-stu-id="42dce-103">This section introduces the typical [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program structure, provides a simple [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program, "Hello, World", and discusses [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] code conventions.</span></span> <span data-ttu-id="42dce-104">程式碼慣例是將焦點放不上程式邏輯，但其實體結構和外觀上的建議。</span><span class="sxs-lookup"><span data-stu-id="42dce-104">Code conventions are suggestions that focus not on a program's logic but on its physical structure and appearance.</span></span> <span data-ttu-id="42dce-105">後面，可讓您的程式碼容易閱讀、 了解和維護。</span><span class="sxs-lookup"><span data-stu-id="42dce-105">Following them makes your code easier to read, understand, and maintain.</span></span> <span data-ttu-id="42dce-106">包括程式碼慣例，和其他項目：</span><span class="sxs-lookup"><span data-stu-id="42dce-106">Code conventions can include, among others:</span></span>  
  
-   <span data-ttu-id="42dce-107">標籤與註解程式碼的標準化的格式。</span><span class="sxs-lookup"><span data-stu-id="42dce-107">Standardized formats for labeling and commenting code.</span></span>  
  
-   <span data-ttu-id="42dce-108">間距、 格式和縮排程式碼的指導方針。</span><span class="sxs-lookup"><span data-stu-id="42dce-108">Guidelines for spacing, formatting, and indenting code.</span></span>  
  
-   <span data-ttu-id="42dce-109">物件、 變數和程序的命名慣例。</span><span class="sxs-lookup"><span data-stu-id="42dce-109">Naming conventions for objects, variables, and procedures.</span></span>  
  
 <span data-ttu-id="42dce-110">下列主題提供一組程式設計指導方針的[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]程式，以及正確使用方式的範例。</span><span class="sxs-lookup"><span data-stu-id="42dce-110">The following topics present a set of programming guidelines for [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programs, along with examples of good usage.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="42dce-111">本章節內容</span><span class="sxs-lookup"><span data-stu-id="42dce-111">In This Section</span></span>  
 [<span data-ttu-id="42dce-112">Visual Basic 程式的結構</span><span class="sxs-lookup"><span data-stu-id="42dce-112">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 <span data-ttu-id="42dce-113">提供的構成項目概觀[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]程式。</span><span class="sxs-lookup"><span data-stu-id="42dce-113">Provides an overview of the elements that make up a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.</span></span>  
  
 [<span data-ttu-id="42dce-114">在 Visual Basic 中的 main 程序</span><span class="sxs-lookup"><span data-stu-id="42dce-114">Main Procedure in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/main-procedure.md)  
 <span data-ttu-id="42dce-115">討論可做為起始點和整體控制您的應用程式的程序。</span><span class="sxs-lookup"><span data-stu-id="42dce-115">Discusses the procedure that serves as the starting point and overall control for your application.</span></span>  
  
 [<span data-ttu-id="42dce-116">參考和 Imports 陳述式</span><span class="sxs-lookup"><span data-stu-id="42dce-116">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 <span data-ttu-id="42dce-117">討論如何參考其他組件中的物件。</span><span class="sxs-lookup"><span data-stu-id="42dce-117">Discusses how to reference objects in other assemblies.</span></span>  
  
 [<span data-ttu-id="42dce-118">在 Visual Basic 中的命名空間</span><span class="sxs-lookup"><span data-stu-id="42dce-118">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 <span data-ttu-id="42dce-119">描述如何命名空間組織內的組件的物件。</span><span class="sxs-lookup"><span data-stu-id="42dce-119">Describes how namespaces organize objects within assemblies.</span></span>  
  
 [<span data-ttu-id="42dce-120">Visual Basic 命名慣例</span><span class="sxs-lookup"><span data-stu-id="42dce-120">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 <span data-ttu-id="42dce-121">包含命名程序、 常數、 變數、 引數和物件的一般指導方針。</span><span class="sxs-lookup"><span data-stu-id="42dce-121">Includes general guidelines for naming procedures, constants, variables, arguments, and objects.</span></span>  
  
 [<span data-ttu-id="42dce-122">Visual Basic 編碼慣例</span><span class="sxs-lookup"><span data-stu-id="42dce-122">Visual Basic Coding Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)  
 <span data-ttu-id="42dce-123">檢閱的指導方針來開發這份文件中的範例。</span><span class="sxs-lookup"><span data-stu-id="42dce-123">Reviews the guidelines used in developing the samples in this documentation.</span></span>  
  
 [<span data-ttu-id="42dce-124">條件式編譯</span><span class="sxs-lookup"><span data-stu-id="42dce-124">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 <span data-ttu-id="42dce-125">說明如何選擇性地編譯而使編譯器忽略其他的特定程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="42dce-125">Describes how to compile particular blocks of code selectively while directing the compiler to ignore others.</span></span>  
  
 [<span data-ttu-id="42dce-126">操作說明：在程式碼內中斷和合併陳述式</span><span class="sxs-lookup"><span data-stu-id="42dce-126">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 <span data-ttu-id="42dce-127">示範如何將分割成多行長的陳述式和合併在一行的簡短陳述式。</span><span class="sxs-lookup"><span data-stu-id="42dce-127">Shows how to divide long statements into multiple lines and combine short statements on one line.</span></span>  
  
 [<span data-ttu-id="42dce-128">操作說明：摺疊和隱藏程式碼區段</span><span class="sxs-lookup"><span data-stu-id="42dce-128">How to: Collapse and Hide Sections of Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)  
 <span data-ttu-id="42dce-129">示範如何摺疊和隱藏程式碼中的區段[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]程式碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="42dce-129">Shows how to collapse and hide sections of code in the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] code editor.</span></span>  
  
 [<span data-ttu-id="42dce-130">操作說明：標記陳述式</span><span class="sxs-lookup"><span data-stu-id="42dce-130">How to: Label Statements</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)  
 <span data-ttu-id="42dce-131">示範如何將標示一行程式碼，以識別使用陳述式例如`On Error Goto`。</span><span class="sxs-lookup"><span data-stu-id="42dce-131">Shows how to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 [<span data-ttu-id="42dce-132">程式碼中的特殊字元</span><span class="sxs-lookup"><span data-stu-id="42dce-132">Special Characters in Code</span></span>](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 <span data-ttu-id="42dce-133">示範如何及在何處使用非數字與非字母字元。</span><span class="sxs-lookup"><span data-stu-id="42dce-133">Shows how and where to use non-numeric and non-alphabetic characters.</span></span>  
  
 [<span data-ttu-id="42dce-134">程式碼中的註解</span><span class="sxs-lookup"><span data-stu-id="42dce-134">Comments in Code</span></span>](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)  
 <span data-ttu-id="42dce-135">討論如何將描述性註解加入至您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="42dce-135">Discusses how to add descriptive comments to your code.</span></span>  
  
 [<span data-ttu-id="42dce-136">程式碼中以關鍵字做為項目名稱</span><span class="sxs-lookup"><span data-stu-id="42dce-136">Keywords as Element Names in Code</span></span>](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 <span data-ttu-id="42dce-137">描述如何使用方括號 (`[]`) 來分隔變數名稱，也是[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]關鍵字。</span><span class="sxs-lookup"><span data-stu-id="42dce-137">Describes how to use brackets (`[]`) to delimit variable names that are also [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] keywords.</span></span>  
  
 [<span data-ttu-id="42dce-138">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="42dce-138">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 <span data-ttu-id="42dce-139">描述各種方式來參考的項目[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]程式。</span><span class="sxs-lookup"><span data-stu-id="42dce-139">Describes various ways to refer to elements of a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.</span></span>  
  
 [<span data-ttu-id="42dce-140">Visual Basic 的限制</span><span class="sxs-lookup"><span data-stu-id="42dce-140">Visual Basic Limitations</span></span>](../../../visual-basic/programming-guide/program-structure/limitations.md)  
 <span data-ttu-id="42dce-141">討論移除已知的編碼限制內[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="42dce-141">Discusses the removal of known coding limits within [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="42dce-142">相關章節</span><span class="sxs-lookup"><span data-stu-id="42dce-142">Related Sections</span></span>  
 [<span data-ttu-id="42dce-143">印刷樣式與程式碼慣例</span><span class="sxs-lookup"><span data-stu-id="42dce-143">Typographic and Code Conventions</span></span>](../../../visual-basic/language-reference/typographic-and-code-conventions.md)  
 <span data-ttu-id="42dce-144">提供標準的程式碼撰寫慣例[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="42dce-144">Provides standard coding conventions for [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
 [<span data-ttu-id="42dce-145">撰寫程式碼</span><span class="sxs-lookup"><span data-stu-id="42dce-145">Writing Code</span></span>](/visualstudio/ide/writing-code-in-the-code-and-text-editor)  
 <span data-ttu-id="42dce-146">描述可讓您更輕鬆地撰寫並管理您的程式碼的功能。</span><span class="sxs-lookup"><span data-stu-id="42dce-146">Describes features that make it easier for you to write and manage your code.</span></span>

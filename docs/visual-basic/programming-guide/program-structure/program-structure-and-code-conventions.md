---
title: "程式結構和程式碼慣例 (Visual Basic) |Microsoft 文件"
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
- coding conventions
- Visual Basic code, coding conventions
- coding conventions, Visual Basic
- programs, structure
- program structure
- naming conventions, Visual Basic
- best practices, coding conventions
- conventions, Visual Basic coding
- Visual Basic code
- programming, Visual Basic coding conventions
ms.assetid: dd9be76f-6944-4e78-ad72-0b6084a3fc13
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: c3a091d64b3c55ad3f1291a635fd499da2dacdc8
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="program-structure-and-code-conventions-visual-basic"></a><span data-ttu-id="12e54-102">程式結構和程式碼慣例 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="12e54-102">Program Structure and Code Conventions (Visual Basic)</span></span>
<span data-ttu-id="12e54-103">本節將介紹一般[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]程式結構，提供簡單的[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]程式，"Hello World"，並討論[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]程式碼慣例。</span><span class="sxs-lookup"><span data-stu-id="12e54-103">This section introduces the typical [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] program structure, provides a simple [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] program, "Hello, World", and discusses [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] code conventions.</span></span> <span data-ttu-id="12e54-104">程式碼慣例是將焦點放不在程式的邏輯，但其實體結構和外觀上的建議。</span><span class="sxs-lookup"><span data-stu-id="12e54-104">Code conventions are suggestions that focus not on a program's logic but on its physical structure and appearance.</span></span> <span data-ttu-id="12e54-105">後面，可讓您的程式碼容易閱讀、 瞭解與維護。</span><span class="sxs-lookup"><span data-stu-id="12e54-105">Following them makes your code easier to read, understand, and maintain.</span></span> <span data-ttu-id="12e54-106">還有其他程式碼慣例可以包括︰</span><span class="sxs-lookup"><span data-stu-id="12e54-106">Code conventions can include, among others:</span></span>  
  
-   <span data-ttu-id="12e54-107">標籤與註解的程式碼的標準化的格式。</span><span class="sxs-lookup"><span data-stu-id="12e54-107">Standardized formats for labeling and commenting code.</span></span>  
  
-   <span data-ttu-id="12e54-108">間距、 格式和縮排程式碼的指導方針。</span><span class="sxs-lookup"><span data-stu-id="12e54-108">Guidelines for spacing, formatting, and indenting code.</span></span>  
  
-   <span data-ttu-id="12e54-109">物件、 變數和程序的命名慣例。</span><span class="sxs-lookup"><span data-stu-id="12e54-109">Naming conventions for objects, variables, and procedures.</span></span>  
  
 <span data-ttu-id="12e54-110">下列主題提供一組程式設計方針[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]計劃以及良好的使用方式的範例。</span><span class="sxs-lookup"><span data-stu-id="12e54-110">The following topics present a set of programming guidelines for [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programs, along with examples of good usage.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="12e54-111">本章節內容</span><span class="sxs-lookup"><span data-stu-id="12e54-111">In This Section</span></span>  
 [<span data-ttu-id="12e54-112">Visual Basic 程式的結構</span><span class="sxs-lookup"><span data-stu-id="12e54-112">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 <span data-ttu-id="12e54-113">提供概觀，構成項目[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]程式。</span><span class="sxs-lookup"><span data-stu-id="12e54-113">Provides an overview of the elements that make up a [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] program.</span></span>  
  
 [<span data-ttu-id="12e54-114">在 Visual Basic 中的 main 程序</span><span class="sxs-lookup"><span data-stu-id="12e54-114">Main Procedure in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/main-procedure.md)  
 <span data-ttu-id="12e54-115">討論可做為開始點和整體控制您的應用程式的程序。</span><span class="sxs-lookup"><span data-stu-id="12e54-115">Discusses the procedure that serves as the starting point and overall control for your application.</span></span>  
  
 [<span data-ttu-id="12e54-116">參考和 Imports 陳述式</span><span class="sxs-lookup"><span data-stu-id="12e54-116">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 <span data-ttu-id="12e54-117">討論如何參考其他組件中的物件。</span><span class="sxs-lookup"><span data-stu-id="12e54-117">Discusses how to reference objects in other assemblies.</span></span>  
  
 [<span data-ttu-id="12e54-118">在 Visual Basic 中的命名空間</span><span class="sxs-lookup"><span data-stu-id="12e54-118">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 <span data-ttu-id="12e54-119">描述如何命名空間組織內的組件的物件。</span><span class="sxs-lookup"><span data-stu-id="12e54-119">Describes how namespaces organize objects within assemblies.</span></span>  
  
 [<span data-ttu-id="12e54-120">Visual Basic 命名慣例</span><span class="sxs-lookup"><span data-stu-id="12e54-120">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 <span data-ttu-id="12e54-121">包含命名程序、 常數、 變數、 引數和物件的一般指導方針。</span><span class="sxs-lookup"><span data-stu-id="12e54-121">Includes general guidelines for naming procedures, constants, variables, arguments, and objects.</span></span>  
  
 [<span data-ttu-id="12e54-122">Visual Basic 編碼慣例</span><span class="sxs-lookup"><span data-stu-id="12e54-122">Visual Basic Coding Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)  
 <span data-ttu-id="12e54-123">檢閱的指導方針來開發這份文件中的範例。</span><span class="sxs-lookup"><span data-stu-id="12e54-123">Reviews the guidelines used in developing the samples in this documentation.</span></span>  
  
 [<span data-ttu-id="12e54-124">條件式編譯</span><span class="sxs-lookup"><span data-stu-id="12e54-124">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 <span data-ttu-id="12e54-125">說明如何選擇性地編譯特定程式碼區塊，而使編譯器忽略其他人。</span><span class="sxs-lookup"><span data-stu-id="12e54-125">Describes how to compile particular blocks of code selectively while directing the compiler to ignore others.</span></span>  
  
 [<span data-ttu-id="12e54-126">如何：在程式碼內中斷和合併陳述式</span><span class="sxs-lookup"><span data-stu-id="12e54-126">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 <span data-ttu-id="12e54-127">示範如何分割成多行的長陳述式和合併在一行的簡短陳述式。</span><span class="sxs-lookup"><span data-stu-id="12e54-127">Shows how to divide long statements into multiple lines and combine short statements on one line.</span></span>  
  
 [<span data-ttu-id="12e54-128">如何：摺疊和隱藏程式碼區段</span><span class="sxs-lookup"><span data-stu-id="12e54-128">How to: Collapse and Hide Sections of Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)  
 <span data-ttu-id="12e54-129">示範如何摺疊和隱藏程式碼中的區段[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]程式碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="12e54-129">Shows how to collapse and hide sections of code in the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] code editor.</span></span>  
  
 [<span data-ttu-id="12e54-130">如何：標記陳述式</span><span class="sxs-lookup"><span data-stu-id="12e54-130">How to: Label Statements</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)  
 <span data-ttu-id="12e54-131">示範如何將標記來識別它的使用陳述式這類的程式碼行`On Error Goto`。</span><span class="sxs-lookup"><span data-stu-id="12e54-131">Shows how to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 [<span data-ttu-id="12e54-132">程式碼中的特殊字元</span><span class="sxs-lookup"><span data-stu-id="12e54-132">Special Characters in Code</span></span>](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 <span data-ttu-id="12e54-133">示範如何以及在何處使用非數字與非字母字元。</span><span class="sxs-lookup"><span data-stu-id="12e54-133">Shows how and where to use non-numeric and non-alphabetic characters.</span></span>  
  
 [<span data-ttu-id="12e54-134">程式碼中的註解</span><span class="sxs-lookup"><span data-stu-id="12e54-134">Comments in Code</span></span>](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)  
 <span data-ttu-id="12e54-135">討論如何將描述性註解加入至您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="12e54-135">Discusses how to add descriptive comments to your code.</span></span>  
  
 [<span data-ttu-id="12e54-136">程式碼中以關鍵字做為項目名稱</span><span class="sxs-lookup"><span data-stu-id="12e54-136">Keywords as Element Names in Code</span></span>](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 <span data-ttu-id="12e54-137">描述如何使用方括號 (`[]`) 來分隔變數名稱，也是[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]關鍵字。</span><span class="sxs-lookup"><span data-stu-id="12e54-137">Describes how to use brackets (`[]`) to delimit variable names that are also [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] keywords.</span></span>  
  
 [<span data-ttu-id="12e54-138">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="12e54-138">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 <span data-ttu-id="12e54-139">描述各種參考的元素[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]程式。</span><span class="sxs-lookup"><span data-stu-id="12e54-139">Describes various ways to refer to elements of a [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] program.</span></span>  
  
 [<span data-ttu-id="12e54-140">Visual Basic 的限制</span><span class="sxs-lookup"><span data-stu-id="12e54-140">Visual Basic Limitations</span></span>](../../../visual-basic/programming-guide/program-structure/limitations.md)  
 <span data-ttu-id="12e54-141">討論已知的程式碼撰寫限制內移除[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="12e54-141">Discusses the removal of known coding limits within [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="12e54-142">相關章節</span><span class="sxs-lookup"><span data-stu-id="12e54-142">Related Sections</span></span>  
 [<span data-ttu-id="12e54-143">印刷樣式與程式碼慣例</span><span class="sxs-lookup"><span data-stu-id="12e54-143">Typographic and Code Conventions</span></span>](../../../visual-basic/language-reference/typographic-and-code-conventions.md)  
 <span data-ttu-id="12e54-144">提供標準的程式碼撰寫慣例[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="12e54-144">Provides standard coding conventions for [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
 [<span data-ttu-id="12e54-145">撰寫程式碼</span><span class="sxs-lookup"><span data-stu-id="12e54-145">Writing Code</span></span>](https://docs.microsoft.com/visualstudio/ide/writing-code-in-the-code-and-text-editor)  
 <span data-ttu-id="12e54-146">描述功能，可讓您更輕鬆地撰寫並管理您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="12e54-146">Describes features that make it easier for you to write and manage your code.</span></span>

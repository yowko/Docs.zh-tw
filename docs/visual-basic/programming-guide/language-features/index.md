---
title: Visual Basic 語言功能
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, elements of
- Visual Basic code
ms.assetid: b0b21730-298c-47e6-9a2f-cc81f628067b
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f7074206baa51259592cca3fdc224d99438791f9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="visual-basic-language-features"></a><span data-ttu-id="1c8f5-102">Visual Basic 語言功能</span><span class="sxs-lookup"><span data-stu-id="1c8f5-102">Visual Basic Language Features</span></span>
<span data-ttu-id="1c8f5-103">下列主題介紹及討論 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] (一種物件導向的程式設計語言) 的基本元件。</span><span class="sxs-lookup"><span data-stu-id="1c8f5-103">The following topics introduce and discuss the essential components of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], an object-oriented programming language.</span></span> <span data-ttu-id="1c8f5-104">使用表單和控制項建立應用程式的使用者介面之後，您必須撰寫程式碼來定義應用程式的行為。</span><span class="sxs-lookup"><span data-stu-id="1c8f5-104">After creating the user interface for your application using forms and controls, you need to write the code that defines the application's behavior.</span></span> <span data-ttu-id="1c8f5-105">和任何新式的程式設計語言一樣，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 支援許多通用的程式設計建構和語言元素。</span><span class="sxs-lookup"><span data-stu-id="1c8f5-105">As with any modern programming language, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] supports a number of common programming constructs and language elements.</span></span>  
  
 <span data-ttu-id="1c8f5-106">如果您曾經使用其他語言進行程式設計，則可能會覺得本節涵蓋的大多數內容似曾相識。</span><span class="sxs-lookup"><span data-stu-id="1c8f5-106">If you have programmed in other languages, much of the material covered in this section might seem familiar.</span></span> <span data-ttu-id="1c8f5-107">雖然大部分的建構類似於其他語言中的建構，但 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 的事件導向本質還是引進了部分些微差異。</span><span class="sxs-lookup"><span data-stu-id="1c8f5-107">While most of the constructs are similar to those in other languages, the event-driven nature of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] introduces some subtle differences.</span></span>  
  
 <span data-ttu-id="1c8f5-108">如果您是程式設計的新手，可將本節的內容當做用來撰寫程式碼的基本建置組塊簡介。</span><span class="sxs-lookup"><span data-stu-id="1c8f5-108">If you are new to programming, the material in this section serves as an introduction to the basic building blocks for writing code.</span></span> <span data-ttu-id="1c8f5-109">一旦您了解基本概念之後，就可以使用 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 來建立功能強大的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1c8f5-109">Once you understand the basics, you can create powerful applications using [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1c8f5-110">本章節內容</span><span class="sxs-lookup"><span data-stu-id="1c8f5-110">In This Section</span></span>  
 [<span data-ttu-id="1c8f5-111">陣列</span><span class="sxs-lookup"><span data-stu-id="1c8f5-111">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 <span data-ttu-id="1c8f5-112">討論如何宣告和使用陣列來保留多個相關聯的值，藉以讓您的程式碼更精簡且功能更強大。</span><span class="sxs-lookup"><span data-stu-id="1c8f5-112">Discusses making your code more compact and powerful by declaring and using arrays, which hold multiple related values.</span></span>  
  
 [<span data-ttu-id="1c8f5-113">集合初始設定式</span><span class="sxs-lookup"><span data-stu-id="1c8f5-113">Collection Initializers</span></span>](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
 <span data-ttu-id="1c8f5-114">說明集合初始設定式，可讓您建立集合，並填入一組初始值。</span><span class="sxs-lookup"><span data-stu-id="1c8f5-114">Describes collection initializers, which enable you to create a collection and populate it with an initial set of values.</span></span>  
  
 [<span data-ttu-id="1c8f5-115">常數和列舉</span><span class="sxs-lookup"><span data-stu-id="1c8f5-115">Constants and Enumerations</span></span>](../../../visual-basic/programming-guide/language-features/constants-enums/index.md)  
 <span data-ttu-id="1c8f5-116">討論儲存不會變動的值以便重複使用，包括相關常數值的集合。</span><span class="sxs-lookup"><span data-stu-id="1c8f5-116">Discusses storing unchanging values for repeated use, including sets of related constant values.</span></span>  
  
 [<span data-ttu-id="1c8f5-117">控制流程</span><span class="sxs-lookup"><span data-stu-id="1c8f5-117">Control Flow</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 <span data-ttu-id="1c8f5-118">示範如何規範程式的執行流程。</span><span class="sxs-lookup"><span data-stu-id="1c8f5-118">Shows how to regulate the flow of your program's execution.</span></span>  
  
 [<span data-ttu-id="1c8f5-119">資料類型</span><span class="sxs-lookup"><span data-stu-id="1c8f5-119">Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 <span data-ttu-id="1c8f5-120">說明程式設計元素可保存的資料種類，以及該資料的儲存方式。</span><span class="sxs-lookup"><span data-stu-id="1c8f5-120">Describes what kinds of data a programming element can hold and how that data is stored.</span></span>  
  
 [<span data-ttu-id="1c8f5-121">宣告項目</span><span class="sxs-lookup"><span data-stu-id="1c8f5-121">Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/index.md)  
 <span data-ttu-id="1c8f5-122">涵蓋您可以宣告的程式設計元素、它們的名稱和特性，以及編譯器如何解析對它們的參考。</span><span class="sxs-lookup"><span data-stu-id="1c8f5-122">Covers programming elements you can declare, their names and characteristics, and how the compiler resolves references to them.</span></span>  
  
 [<span data-ttu-id="1c8f5-123">委派</span><span class="sxs-lookup"><span data-stu-id="1c8f5-123">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 <span data-ttu-id="1c8f5-124">提供委派的簡介，以及在 Visual Basic 中的使用方法。</span><span class="sxs-lookup"><span data-stu-id="1c8f5-124">Provides an introduction to delegates and how they are used in Visual Basic.</span></span>  
  
 [<span data-ttu-id="1c8f5-125">早期和晚期繫結</span><span class="sxs-lookup"><span data-stu-id="1c8f5-125">Early and Late Binding</span></span>](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)  
 <span data-ttu-id="1c8f5-126">說明繫結 (將物件指派給物件變數時，會由編譯器執行)，以及早期繫結和晚期繫結物件之間的差異。</span><span class="sxs-lookup"><span data-stu-id="1c8f5-126">Describes binding, which is performed by the compiler when an object is assigned to an object variable, and the differences between early-bound and late-bound objects.</span></span>  
  
 [<span data-ttu-id="1c8f5-127">錯誤類型</span><span class="sxs-lookup"><span data-stu-id="1c8f5-127">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)  
 <span data-ttu-id="1c8f5-128">提供語法錯誤、執行階段錯誤和邏輯錯誤的概觀。</span><span class="sxs-lookup"><span data-stu-id="1c8f5-128">Provides an overview of syntax errors, run-time errors, and logic errors.</span></span>  
  
 [<span data-ttu-id="1c8f5-129">事件</span><span class="sxs-lookup"><span data-stu-id="1c8f5-129">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)  
 <span data-ttu-id="1c8f5-130">示範如何宣告和使用事件。</span><span class="sxs-lookup"><span data-stu-id="1c8f5-130">Shows how to declare and use events.</span></span>  
  
 [<span data-ttu-id="1c8f5-131">介面</span><span class="sxs-lookup"><span data-stu-id="1c8f5-131">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)  
 <span data-ttu-id="1c8f5-132">說明何謂介面，以及如何在應用程式中使用它們。</span><span class="sxs-lookup"><span data-stu-id="1c8f5-132">Describes what interfaces are and how you can use them in your applications.</span></span>  
  
 [<span data-ttu-id="1c8f5-133">LINQ</span><span class="sxs-lookup"><span data-stu-id="1c8f5-133">LINQ</span></span>](../../../visual-basic/programming-guide/language-features/linq/index.md)  
 <span data-ttu-id="1c8f5-134">提供主題連結來介紹 [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] 功能和程式設計。</span><span class="sxs-lookup"><span data-stu-id="1c8f5-134">Provides links to topics that introduce [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] features and programming.</span></span>  
  
 [<span data-ttu-id="1c8f5-135">物件和類別</span><span class="sxs-lookup"><span data-stu-id="1c8f5-135">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 <span data-ttu-id="1c8f5-136">提供物件和類別的概觀、它們的使用方式、其彼此間的關聯性，以及它們所公開的屬性、方法和事件。</span><span class="sxs-lookup"><span data-stu-id="1c8f5-136">Provides an overview of objects and classes, how they are used, their relationships to each other, and the properties, methods, and events they expose.</span></span>  
  
 [<span data-ttu-id="1c8f5-137">運算子和運算式</span><span class="sxs-lookup"><span data-stu-id="1c8f5-137">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 <span data-ttu-id="1c8f5-138">說明處理保存值元素的核心元素、如何有效地使用它們，以及如何結合它們來產生新值。</span><span class="sxs-lookup"><span data-stu-id="1c8f5-138">Describes the code elements that manipulate value-holding elements, how to use them efficiently, and how to combine them to yield new values.</span></span>  
  
 [<span data-ttu-id="1c8f5-139">程序</span><span class="sxs-lookup"><span data-stu-id="1c8f5-139">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 <span data-ttu-id="1c8f5-140">說明 `Sub`、`Function`、`Property` 及 `Operator` 程序，以及像是遞迴和多載程序等進階主題。</span><span class="sxs-lookup"><span data-stu-id="1c8f5-140">Describes `Sub`, `Function`, `Property`, and `Operator` procedures, as well as advanced topics such as recursive and overloaded procedures.</span></span>  
  
 [<span data-ttu-id="1c8f5-141">陳述式</span><span class="sxs-lookup"><span data-stu-id="1c8f5-141">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 <span data-ttu-id="1c8f5-142">說明宣告和可執行的陳述式。</span><span class="sxs-lookup"><span data-stu-id="1c8f5-142">Describes declaration and executable statements.</span></span>  
  
 [<span data-ttu-id="1c8f5-143">字串</span><span class="sxs-lookup"><span data-stu-id="1c8f5-143">Strings</span></span>](../../../visual-basic/programming-guide/language-features/strings/index.md)  
 <span data-ttu-id="1c8f5-144">提供主題連結來描述有關在 Visual Basic 中使用字串的基本概念。</span><span class="sxs-lookup"><span data-stu-id="1c8f5-144">Provides links to topics that describe the basic concepts about using strings in Visual Basic.</span></span>  
  
 [<span data-ttu-id="1c8f5-145">變數</span><span class="sxs-lookup"><span data-stu-id="1c8f5-145">Variables</span></span>](../../../visual-basic/programming-guide/language-features/variables/index.md)  
 <span data-ttu-id="1c8f5-146">介紹變數，並說明如何在 Visual Basic 中使用它們。</span><span class="sxs-lookup"><span data-stu-id="1c8f5-146">Introduces variables and describes how to use them in Visual Basic.</span></span>  
  
 [<span data-ttu-id="1c8f5-147">XML</span><span class="sxs-lookup"><span data-stu-id="1c8f5-147">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)  
 <span data-ttu-id="1c8f5-148">提供主題連結來說明如何在 Visual Basic 中使用 XML。</span><span class="sxs-lookup"><span data-stu-id="1c8f5-148">Provides links to topics that describe how to use XML in Visual Basic.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1c8f5-149">相關章節</span><span class="sxs-lookup"><span data-stu-id="1c8f5-149">Related Sections</span></span>  
 [<span data-ttu-id="1c8f5-150">集合</span><span class="sxs-lookup"><span data-stu-id="1c8f5-150">Collections</span></span>](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)  
 <span data-ttu-id="1c8f5-151">說明部分由 .NET Framework 提供的集合型別。</span><span class="sxs-lookup"><span data-stu-id="1c8f5-151">Describes some of the types of collections that are provided by the .NET Framework.</span></span> <span data-ttu-id="1c8f5-152">示範如何使用簡單集合及金鑰/值組集合。</span><span class="sxs-lookup"><span data-stu-id="1c8f5-152">Demonstrates how to use simple collections and collections of key/value pairs.</span></span>  
  
 [<span data-ttu-id="1c8f5-153">Visual Basic 語言參考</span><span class="sxs-lookup"><span data-stu-id="1c8f5-153">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)  
 <span data-ttu-id="1c8f5-154">提供 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 程式設計各種層面的參考資訊。</span><span class="sxs-lookup"><span data-stu-id="1c8f5-154">Provides reference information on various aspects of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programming.</span></span>

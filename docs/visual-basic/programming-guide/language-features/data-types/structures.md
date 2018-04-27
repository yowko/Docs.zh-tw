---
title: 結構 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- structures [Visual Basic]
- user-defined data types [Visual Basic], structures
- user-defined types [Visual Basic], about user-defined types
- data types [Visual Basic], user-defined
- user-defined data types [Visual Basic], about user-defined data types
- types [Visual Basic], user-defined
ms.assetid: 55e86462-5e99-4d33-8018-6d097ca491b2
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d1f537b25a405548816ab3d356a18f693a5d0006
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="structures-visual-basic"></a><span data-ttu-id="9c041-102">結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c041-102">Structures (Visual Basic)</span></span>
<span data-ttu-id="9c041-103">A*結構*為一般化的使用者定義型別 (UDT) 由舊版 Visual Basic 的支援。</span><span class="sxs-lookup"><span data-stu-id="9c041-103">A *structure* is a generalization of the user-defined type (UDT) supported by previous versions of Visual Basic.</span></span> <span data-ttu-id="9c041-104">欄位中，除了結構可以公開屬性、 方法和事件。</span><span class="sxs-lookup"><span data-stu-id="9c041-104">In addition to fields, structures can expose properties, methods, and events.</span></span> <span data-ttu-id="9c041-105">結構可以實作一個或多個介面，您可以宣告為每個欄位個別的存取層級。</span><span class="sxs-lookup"><span data-stu-id="9c041-105">A structure can implement one or more interfaces, and you can declare individual access levels for each field.</span></span>  
  
 <span data-ttu-id="9c041-106">您可以結合以建立結構的不同類型的資料項目。</span><span class="sxs-lookup"><span data-stu-id="9c041-106">You can combine data items of different types to create a structure.</span></span> <span data-ttu-id="9c041-107">結構會將一或多個*元素*與彼此、 與結構本身。</span><span class="sxs-lookup"><span data-stu-id="9c041-107">A structure associates one or more *elements* with each other and with the structure itself.</span></span> <span data-ttu-id="9c041-108">當您宣告結構時，它會變成*複合資料類型*，而且您可以宣告該類型的變數。</span><span class="sxs-lookup"><span data-stu-id="9c041-108">When you declare a structure, it becomes a *composite data type*, and you can declare variables of that type.</span></span>  
  
 <span data-ttu-id="9c041-109">當您想相關的資訊片段的單一變數時，結構會很有用。</span><span class="sxs-lookup"><span data-stu-id="9c041-109">Structures are useful when you want a single variable to hold several related pieces of information.</span></span> <span data-ttu-id="9c041-110">比方說，您可以將員工的名稱、 電話分機號碼和薪資放在一起。</span><span class="sxs-lookup"><span data-stu-id="9c041-110">For example, you might want to keep an employee's name, telephone extension, and salary together.</span></span> <span data-ttu-id="9c041-111">您可以使用數個變數，這項資訊，或您無法定義的結構，並將它用於單一員工變數。</span><span class="sxs-lookup"><span data-stu-id="9c041-111">You could use several variables for this information, or you could define a structure and use it for a single employee variable.</span></span> <span data-ttu-id="9c041-112">當您有許多員工，因此變數的許多執行個體時，此結構的優點就顯而易見。</span><span class="sxs-lookup"><span data-stu-id="9c041-112">The advantage of the structure becomes apparent when you have many employees and therefore many instances of the variable.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9c041-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="9c041-113">In This Section</span></span>  
 [<span data-ttu-id="9c041-114">如何：宣告結構</span><span class="sxs-lookup"><span data-stu-id="9c041-114">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 <span data-ttu-id="9c041-115">示範如何宣告結構和元素。</span><span class="sxs-lookup"><span data-stu-id="9c041-115">Shows how to declare a structure and its elements.</span></span>  
  
 [<span data-ttu-id="9c041-116">結構變數</span><span class="sxs-lookup"><span data-stu-id="9c041-116">Structure Variables</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)  
 <span data-ttu-id="9c041-117">涵蓋如何將結構指派給變數，並存取其項目。</span><span class="sxs-lookup"><span data-stu-id="9c041-117">Covers assigning a structure to a variable and accessing its elements.</span></span>  
  
 [<span data-ttu-id="9c041-118">結構和其他程式設計項目</span><span class="sxs-lookup"><span data-stu-id="9c041-118">Structures and Other Programming Elements</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)  
 <span data-ttu-id="9c041-119">摘要說明結構如何與陣列、 物件、 程序，以及彼此互動。</span><span class="sxs-lookup"><span data-stu-id="9c041-119">Summarizes how structures interact with arrays, objects, procedures, and each other.</span></span>  
  
 [<span data-ttu-id="9c041-120">結構和類別</span><span class="sxs-lookup"><span data-stu-id="9c041-120">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 <span data-ttu-id="9c041-121">描述結構和類別之間的差異與相似之處。</span><span class="sxs-lookup"><span data-stu-id="9c041-121">Describes the similarities and differences between structures and classes.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9c041-122">相關章節</span><span class="sxs-lookup"><span data-stu-id="9c041-122">Related Sections</span></span>  
 [<span data-ttu-id="9c041-123">資料類型</span><span class="sxs-lookup"><span data-stu-id="9c041-123">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 <span data-ttu-id="9c041-124">介紹 Visual Basic 資料類型，並說明如何使用它們。</span><span class="sxs-lookup"><span data-stu-id="9c041-124">Introduces the Visual Basic data types and describes how to use them.</span></span>  
  
 [<span data-ttu-id="9c041-125">資料類型</span><span class="sxs-lookup"><span data-stu-id="9c041-125">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 <span data-ttu-id="9c041-126">列出 Visual Basic 所提供的基本資料類型。</span><span class="sxs-lookup"><span data-stu-id="9c041-126">Lists the elementary data types supplied by Visual Basic.</span></span>

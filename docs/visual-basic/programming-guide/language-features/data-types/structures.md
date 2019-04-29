---
title: 結構 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic]
- user-defined data types [Visual Basic], structures
- user-defined types [Visual Basic], about user-defined types
- data types [Visual Basic], user-defined
- user-defined data types [Visual Basic], about user-defined data types
- types [Visual Basic], user-defined
ms.assetid: 55e86462-5e99-4d33-8018-6d097ca491b2
ms.openlocfilehash: ebfc82665bb18d96c83db8f29a6c206a9a71fd7f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663358"
---
# <a name="structures-visual-basic"></a><span data-ttu-id="87b01-102">結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87b01-102">Structures (Visual Basic)</span></span>
<span data-ttu-id="87b01-103">A*結構*為一般化的使用者定義型別 (UDT) 支援舊版的 Visual Basic。</span><span class="sxs-lookup"><span data-stu-id="87b01-103">A *structure* is a generalization of the user-defined type (UDT) supported by previous versions of Visual Basic.</span></span> <span data-ttu-id="87b01-104">除了欄位之外，結構可以公開屬性、 方法和事件。</span><span class="sxs-lookup"><span data-stu-id="87b01-104">In addition to fields, structures can expose properties, methods, and events.</span></span> <span data-ttu-id="87b01-105">結構可以實作一或多個介面，以及您可以宣告個別的存取層級，每個欄位。</span><span class="sxs-lookup"><span data-stu-id="87b01-105">A structure can implement one or more interfaces, and you can declare individual access levels for each field.</span></span>  
  
 <span data-ttu-id="87b01-106">您可以結合以建立結構的不同類型的資料項目。</span><span class="sxs-lookup"><span data-stu-id="87b01-106">You can combine data items of different types to create a structure.</span></span> <span data-ttu-id="87b01-107">結構會將一或多個*項目*彼此及與結構本身。</span><span class="sxs-lookup"><span data-stu-id="87b01-107">A structure associates one or more *elements* with each other and with the structure itself.</span></span> <span data-ttu-id="87b01-108">當您宣告結構時，它會變成*複合資料型別*，而您可以宣告該類型的變數。</span><span class="sxs-lookup"><span data-stu-id="87b01-108">When you declare a structure, it becomes a *composite data type*, and you can declare variables of that type.</span></span>  
  
 <span data-ttu-id="87b01-109">當您想要的數個相關的資訊片段的單一變數時，結構會很有用。</span><span class="sxs-lookup"><span data-stu-id="87b01-109">Structures are useful when you want a single variable to hold several related pieces of information.</span></span> <span data-ttu-id="87b01-110">例如，您可能要保持員工的名稱、 電話分機號碼和薪資。</span><span class="sxs-lookup"><span data-stu-id="87b01-110">For example, you might want to keep an employee's name, telephone extension, and salary together.</span></span> <span data-ttu-id="87b01-111">您可以使用數個變數，這項資訊，或者您可以定義結構，並使用它之單一員工變數。</span><span class="sxs-lookup"><span data-stu-id="87b01-111">You could use several variables for this information, or you could define a structure and use it for a single employee variable.</span></span> <span data-ttu-id="87b01-112">當您有許多員工，且因此變數的許多執行個體時，結構的優點變得顯而易見。</span><span class="sxs-lookup"><span data-stu-id="87b01-112">The advantage of the structure becomes apparent when you have many employees and therefore many instances of the variable.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="87b01-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="87b01-113">In This Section</span></span>  
 [<span data-ttu-id="87b01-114">如何：宣告結構</span><span class="sxs-lookup"><span data-stu-id="87b01-114">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 <span data-ttu-id="87b01-115">示範如何宣告結構和元素。</span><span class="sxs-lookup"><span data-stu-id="87b01-115">Shows how to declare a structure and its elements.</span></span>  
  
 [<span data-ttu-id="87b01-116">結構變數</span><span class="sxs-lookup"><span data-stu-id="87b01-116">Structure Variables</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)  
 <span data-ttu-id="87b01-117">涵蓋如何將結構指派給變數，並存取其項目。</span><span class="sxs-lookup"><span data-stu-id="87b01-117">Covers assigning a structure to a variable and accessing its elements.</span></span>  
  
 [<span data-ttu-id="87b01-118">結構和其他程式設計項目</span><span class="sxs-lookup"><span data-stu-id="87b01-118">Structures and Other Programming Elements</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)  
 <span data-ttu-id="87b01-119">摘要說明結構如何與陣列、 物件、 程序，以及彼此互動。</span><span class="sxs-lookup"><span data-stu-id="87b01-119">Summarizes how structures interact with arrays, objects, procedures, and each other.</span></span>  
  
 [<span data-ttu-id="87b01-120">結構和類別</span><span class="sxs-lookup"><span data-stu-id="87b01-120">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 <span data-ttu-id="87b01-121">描述結構和類別之間的差異與相似之處。</span><span class="sxs-lookup"><span data-stu-id="87b01-121">Describes the similarities and differences between structures and classes.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="87b01-122">相關章節</span><span class="sxs-lookup"><span data-stu-id="87b01-122">Related Sections</span></span>  
 [<span data-ttu-id="87b01-123">資料類型</span><span class="sxs-lookup"><span data-stu-id="87b01-123">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 <span data-ttu-id="87b01-124">介紹 Visual Basic 資料類型，並說明如何使用它們。</span><span class="sxs-lookup"><span data-stu-id="87b01-124">Introduces the Visual Basic data types and describes how to use them.</span></span>  
  
 [<span data-ttu-id="87b01-125">資料類型</span><span class="sxs-lookup"><span data-stu-id="87b01-125">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)  
 <span data-ttu-id="87b01-126">列出 Visual Basic 所提供的基本資料類型。</span><span class="sxs-lookup"><span data-stu-id="87b01-126">Lists the elementary data types supplied by Visual Basic.</span></span>

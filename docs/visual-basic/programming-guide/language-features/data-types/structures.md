---
title: "結構 (Visual Basic) |Microsoft 文件"
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
- structures
- user-defined data types, structures
- user-defined types, about user-defined types
- data types [Visual Basic], user-defined
- user-defined data types, about user-defined data types
- types [Visual Basic], user-defined
ms.assetid: 55e86462-5e99-4d33-8018-6d097ca491b2
caps.latest.revision: 13
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
ms.openlocfilehash: d1ba8671af9ff6d50499149fce6d55b3db78ffe0
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="structures-visual-basic"></a><span data-ttu-id="51e02-102">結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="51e02-102">Structures (Visual Basic)</span></span>
<span data-ttu-id="51e02-103">A*結構*是使用者定義型別 (UDT) 的先前版本所支援之一般化[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="51e02-103">A *structure* is a generalization of the user-defined type (UDT) supported by previous versions of [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span> <span data-ttu-id="51e02-104">除了欄位之外，結構還公開屬性、 方法和事件。</span><span class="sxs-lookup"><span data-stu-id="51e02-104">In addition to fields, structures can expose properties, methods, and events.</span></span> <span data-ttu-id="51e02-105">結構可以實作一個或多個介面，而且您可以宣告每個欄位個別的存取層級。</span><span class="sxs-lookup"><span data-stu-id="51e02-105">A structure can implement one or more interfaces, and you can declare individual access levels for each field.</span></span>  
  
 <span data-ttu-id="51e02-106">您可以結合以建立結構的不同類型的資料項目。</span><span class="sxs-lookup"><span data-stu-id="51e02-106">You can combine data items of different types to create a structure.</span></span> <span data-ttu-id="51e02-107">結構會將一或多個*元素*和與結構本身。</span><span class="sxs-lookup"><span data-stu-id="51e02-107">A structure associates one or more *elements* with each other and with the structure itself.</span></span> <span data-ttu-id="51e02-108">當您宣告結構時，它會變成*複合資料型別*，而且您可以宣告該型別的變數。</span><span class="sxs-lookup"><span data-stu-id="51e02-108">When you declare a structure, it becomes a *composite data type*, and you can declare variables of that type.</span></span>  
  
 <span data-ttu-id="51e02-109">當您想要的單一變數來保存相關的資訊片段，結構會很有用。</span><span class="sxs-lookup"><span data-stu-id="51e02-109">Structures are useful when you want a single variable to hold several related pieces of information.</span></span> <span data-ttu-id="51e02-110">比方說，您可能要將員工的名稱、 電話分機號碼和薪資放在一起。</span><span class="sxs-lookup"><span data-stu-id="51e02-110">For example, you might want to keep an employee's name, telephone extension, and salary together.</span></span> <span data-ttu-id="51e02-111">您可以使用數個變數，這項資訊，或您可以使用單一員工變數而定義的結構。</span><span class="sxs-lookup"><span data-stu-id="51e02-111">You could use several variables for this information, or you could define a structure and use it for a single employee variable.</span></span> <span data-ttu-id="51e02-112">當您有許多員工，且因此變數的多個執行個體時，結構的好處就顯而易見。</span><span class="sxs-lookup"><span data-stu-id="51e02-112">The advantage of the structure becomes apparent when you have many employees and therefore many instances of the variable.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="51e02-113">本章節內容</span><span class="sxs-lookup"><span data-stu-id="51e02-113">In This Section</span></span>  
 [<span data-ttu-id="51e02-114">如何：宣告結構</span><span class="sxs-lookup"><span data-stu-id="51e02-114">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 <span data-ttu-id="51e02-115">示範如何宣告結構和元素。</span><span class="sxs-lookup"><span data-stu-id="51e02-115">Shows how to declare a structure and its elements.</span></span>  
  
 [<span data-ttu-id="51e02-116">結構變數</span><span class="sxs-lookup"><span data-stu-id="51e02-116">Structure Variables</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)  
 <span data-ttu-id="51e02-117">涵蓋如何將結構指派給變數，並存取其項目。</span><span class="sxs-lookup"><span data-stu-id="51e02-117">Covers assigning a structure to a variable and accessing its elements.</span></span>  
  
 [<span data-ttu-id="51e02-118">結構和其他程式設計項目</span><span class="sxs-lookup"><span data-stu-id="51e02-118">Structures and Other Programming Elements</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)  
 <span data-ttu-id="51e02-119">彙總結構如何與陣列、 物件、 程序，以及彼此互動。</span><span class="sxs-lookup"><span data-stu-id="51e02-119">Summarizes how structures interact with arrays, objects, procedures, and each other.</span></span>  
  
 [<span data-ttu-id="51e02-120">結構和類別</span><span class="sxs-lookup"><span data-stu-id="51e02-120">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 <span data-ttu-id="51e02-121">描述結構和類別之間的差異與相似之處。</span><span class="sxs-lookup"><span data-stu-id="51e02-121">Describes the similarities and differences between structures and classes.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="51e02-122">相關章節</span><span class="sxs-lookup"><span data-stu-id="51e02-122">Related Sections</span></span>  
 [<span data-ttu-id="51e02-123">資料類型</span><span class="sxs-lookup"><span data-stu-id="51e02-123">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 <span data-ttu-id="51e02-124">介紹[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]資料型別，並說明如何使用它們。</span><span class="sxs-lookup"><span data-stu-id="51e02-124">Introduces the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] data types and describes how to use them.</span></span>  
  
 [<span data-ttu-id="51e02-125">資料類型</span><span class="sxs-lookup"><span data-stu-id="51e02-125">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 <span data-ttu-id="51e02-126">列出所提供的基本資料型別[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="51e02-126">Lists the elementary data types supplied by [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>

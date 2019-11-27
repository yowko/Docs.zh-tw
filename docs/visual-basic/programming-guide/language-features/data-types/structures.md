---
title: 結構
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic]
- user-defined data types [Visual Basic], structures
- user-defined types [Visual Basic], about user-defined types
- data types [Visual Basic], user-defined
- user-defined data types [Visual Basic], about user-defined data types
- types [Visual Basic], user-defined
ms.assetid: 55e86462-5e99-4d33-8018-6d097ca491b2
ms.openlocfilehash: b5f1f8d6d783c6612fdb2bd2058b61a5a46024cc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350766"
---
# <a name="structures-visual-basic"></a><span data-ttu-id="e2483-102">結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2483-102">Structures (Visual Basic)</span></span>
<span data-ttu-id="e2483-103">「*結構*」（structure）是舊版 Visual Basic 支援的使用者定義型別（UDT）的一般化。</span><span class="sxs-lookup"><span data-stu-id="e2483-103">A *structure* is a generalization of the user-defined type (UDT) supported by previous versions of Visual Basic.</span></span> <span data-ttu-id="e2483-104">除了欄位之外，結構也可以公開屬性、方法和事件。</span><span class="sxs-lookup"><span data-stu-id="e2483-104">In addition to fields, structures can expose properties, methods, and events.</span></span> <span data-ttu-id="e2483-105">結構可以執行一或多個介面，而且您可以為每個欄位宣告個別的存取層級。</span><span class="sxs-lookup"><span data-stu-id="e2483-105">A structure can implement one or more interfaces, and you can declare individual access levels for each field.</span></span>  
  
 <span data-ttu-id="e2483-106">您可以結合不同類型的資料項目來建立結構。</span><span class="sxs-lookup"><span data-stu-id="e2483-106">You can combine data items of different types to create a structure.</span></span> <span data-ttu-id="e2483-107">結構會將一或多個專案與*彼此以及結構*本身產生關聯。</span><span class="sxs-lookup"><span data-stu-id="e2483-107">A structure associates one or more *elements* with each other and with the structure itself.</span></span> <span data-ttu-id="e2483-108">當您宣告結構時，它會成為*複合資料型別*，而您可以宣告該類型的變數。</span><span class="sxs-lookup"><span data-stu-id="e2483-108">When you declare a structure, it becomes a *composite data type*, and you can declare variables of that type.</span></span>  
  
 <span data-ttu-id="e2483-109">當您想要讓單一變數保存數個相關的資訊時，結構會很有用。</span><span class="sxs-lookup"><span data-stu-id="e2483-109">Structures are useful when you want a single variable to hold several related pieces of information.</span></span> <span data-ttu-id="e2483-110">例如，您可能想要將員工的名稱、電話分機和薪資保持在一起。</span><span class="sxs-lookup"><span data-stu-id="e2483-110">For example, you might want to keep an employee's name, telephone extension, and salary together.</span></span> <span data-ttu-id="e2483-111">您可以使用數個變數來取得這項資訊，或者您可以定義結構並將它用於單一員工變數。</span><span class="sxs-lookup"><span data-stu-id="e2483-111">You could use several variables for this information, or you could define a structure and use it for a single employee variable.</span></span> <span data-ttu-id="e2483-112">當您有許多員工，因此有許多不同的變數實例時，結構的優勢就會變得很明顯。</span><span class="sxs-lookup"><span data-stu-id="e2483-112">The advantage of the structure becomes apparent when you have many employees and therefore many instances of the variable.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e2483-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="e2483-113">In This Section</span></span>  
 [<span data-ttu-id="e2483-114">如何：宣告結構</span><span class="sxs-lookup"><span data-stu-id="e2483-114">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 <span data-ttu-id="e2483-115">顯示如何宣告結構及其元素。</span><span class="sxs-lookup"><span data-stu-id="e2483-115">Shows how to declare a structure and its elements.</span></span>  
  
 [<span data-ttu-id="e2483-116">結構變數</span><span class="sxs-lookup"><span data-stu-id="e2483-116">Structure Variables</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)  
 <span data-ttu-id="e2483-117">涵蓋將結構指派給變數，並存取其元素。</span><span class="sxs-lookup"><span data-stu-id="e2483-117">Covers assigning a structure to a variable and accessing its elements.</span></span>  
  
 [<span data-ttu-id="e2483-118">結構和其他程式設計項目</span><span class="sxs-lookup"><span data-stu-id="e2483-118">Structures and Other Programming Elements</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)  
 <span data-ttu-id="e2483-119">摘要說明結構與陣列、物件、程式等的互動方式。</span><span class="sxs-lookup"><span data-stu-id="e2483-119">Summarizes how structures interact with arrays, objects, procedures, and each other.</span></span>  
  
 [<span data-ttu-id="e2483-120">結構和類別</span><span class="sxs-lookup"><span data-stu-id="e2483-120">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 <span data-ttu-id="e2483-121">描述結構與類別之間的相似性和差異。</span><span class="sxs-lookup"><span data-stu-id="e2483-121">Describes the similarities and differences between structures and classes.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e2483-122">相關章節</span><span class="sxs-lookup"><span data-stu-id="e2483-122">Related Sections</span></span>  
 [<span data-ttu-id="e2483-123">資料類型</span><span class="sxs-lookup"><span data-stu-id="e2483-123">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 <span data-ttu-id="e2483-124">介紹 Visual Basic 的資料類型，並說明如何使用它們。</span><span class="sxs-lookup"><span data-stu-id="e2483-124">Introduces the Visual Basic data types and describes how to use them.</span></span>  
  
 [<span data-ttu-id="e2483-125">資料類型</span><span class="sxs-lookup"><span data-stu-id="e2483-125">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)  
 <span data-ttu-id="e2483-126">列出 Visual Basic 所提供的基本資料類型。</span><span class="sxs-lookup"><span data-stu-id="e2483-126">Lists the elementary data types supplied by Visual Basic.</span></span>

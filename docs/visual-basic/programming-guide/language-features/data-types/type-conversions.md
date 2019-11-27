---
title: 類型轉換
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [Visual Basic], type
- data types [Visual Basic], changing
- variables [Visual Basic], changing data type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- changing data types [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 1cdacd21-ba31-4b62-b5be-395e41eeaa17
ms.openlocfilehash: fbf0c9877cf9a9b4364c8c058c61e847ad7bf049
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348714"
---
# <a name="type-conversions-in-visual-basic"></a><span data-ttu-id="587a8-102">Visual Basic 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="587a8-102">Type Conversions in Visual Basic</span></span>
<span data-ttu-id="587a8-103">將某個資料類型的值變更為另一個類型的程式稱為「*轉換*」。</span><span class="sxs-lookup"><span data-stu-id="587a8-103">The process of changing a value from one data type to another type is called *conversion*.</span></span> <span data-ttu-id="587a8-104">轉換是*擴展*或*縮小*，視相關類型的資料容量而定。</span><span class="sxs-lookup"><span data-stu-id="587a8-104">Conversions are either *widening* or *narrowing*, depending on the data capacities of the types involved.</span></span> <span data-ttu-id="587a8-105">根據原始程式碼中的語法，它們也是*隱含*或*明確*的。</span><span class="sxs-lookup"><span data-stu-id="587a8-105">They are also *implicit* or *explicit*, depending on the syntax in the source code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="587a8-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="587a8-106">In This Section</span></span>  
 [<span data-ttu-id="587a8-107">擴展和縮小轉換</span><span class="sxs-lookup"><span data-stu-id="587a8-107">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 <span data-ttu-id="587a8-108">說明依據目的地類型是否可以保存資料而分類的轉換。</span><span class="sxs-lookup"><span data-stu-id="587a8-108">Explains conversions classified by whether the destination type can hold the data.</span></span>  
  
 [<span data-ttu-id="587a8-109">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="587a8-109">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 <span data-ttu-id="587a8-110">討論 Visual Basic 是否自動執行分類的轉換。</span><span class="sxs-lookup"><span data-stu-id="587a8-110">Discusses conversions classified by whether Visual Basic performs them automatically.</span></span>  
  
 [<span data-ttu-id="587a8-111">字串與其他類型之間的轉換</span><span class="sxs-lookup"><span data-stu-id="587a8-111">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 <span data-ttu-id="587a8-112">說明如何在字串和數值、`Boolean`或日期/時間值之間轉換。</span><span class="sxs-lookup"><span data-stu-id="587a8-112">Illustrates converting between strings and numeric, `Boolean`, or date/time values.</span></span>  
  
 [<span data-ttu-id="587a8-113">如何：在 Visual Basic 中將物件轉換為另一種類型</span><span class="sxs-lookup"><span data-stu-id="587a8-113">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 <span data-ttu-id="587a8-114">說明如何將 `Object` 變數轉換成其他任何資料類型。</span><span class="sxs-lookup"><span data-stu-id="587a8-114">Shows how to convert an `Object` variable to any other data type.</span></span>  
  
 [<span data-ttu-id="587a8-115">陣列轉換</span><span class="sxs-lookup"><span data-stu-id="587a8-115">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 <span data-ttu-id="587a8-116">逐步引導您完成在不同資料類型的陣列之間轉換的程式。</span><span class="sxs-lookup"><span data-stu-id="587a8-116">Steps you through the process of converting between arrays of different data types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="587a8-117">相關章節</span><span class="sxs-lookup"><span data-stu-id="587a8-117">Related Sections</span></span>  
 [<span data-ttu-id="587a8-118">資料類型</span><span class="sxs-lookup"><span data-stu-id="587a8-118">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 <span data-ttu-id="587a8-119">介紹 Visual Basic 的資料類型，並說明如何使用它們。</span><span class="sxs-lookup"><span data-stu-id="587a8-119">Introduces the Visual Basic data types and describes how to use them.</span></span>  
  
 [<span data-ttu-id="587a8-120">資料類型</span><span class="sxs-lookup"><span data-stu-id="587a8-120">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)  
 <span data-ttu-id="587a8-121">列出 Visual Basic 所提供的基本資料類型。</span><span class="sxs-lookup"><span data-stu-id="587a8-121">Lists the elementary data types supplied by Visual Basic.</span></span>  
  
 [<span data-ttu-id="587a8-122">資料類型的疑難排解</span><span class="sxs-lookup"><span data-stu-id="587a8-122">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 <span data-ttu-id="587a8-123">討論使用資料類型時可能會發生的一些常見問題。</span><span class="sxs-lookup"><span data-stu-id="587a8-123">Discusses some common problems that can arise when working with data types.</span></span>

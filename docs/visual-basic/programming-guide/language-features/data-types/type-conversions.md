---
title: Visual Basic 中的類型轉換
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
ms.openlocfilehash: 026b2a250abfac0782feb0946bc50a94f504f7ed
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44084464"
---
# <a name="type-conversions-in-visual-basic"></a><span data-ttu-id="f12f5-102">Visual Basic 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="f12f5-102">Type Conversions in Visual Basic</span></span>
<span data-ttu-id="f12f5-103">值從一種資料類型變更為另一種類型的程序稱為*轉換*。</span><span class="sxs-lookup"><span data-stu-id="f12f5-103">The process of changing a value from one data type to another type is called *conversion*.</span></span> <span data-ttu-id="f12f5-104">轉換為*widening*或是*縮小*，取決於相關類型的資料容量。</span><span class="sxs-lookup"><span data-stu-id="f12f5-104">Conversions are either *widening* or *narrowing*, depending on the data capacities of the types involved.</span></span> <span data-ttu-id="f12f5-105">它們也是*隱含*或是*明確*，取決於在原始程式碼中的語法。</span><span class="sxs-lookup"><span data-stu-id="f12f5-105">They are also *implicit* or *explicit*, depending on the syntax in the source code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f12f5-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="f12f5-106">In This Section</span></span>  
 [<span data-ttu-id="f12f5-107">擴展和縮小轉換</span><span class="sxs-lookup"><span data-stu-id="f12f5-107">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 <span data-ttu-id="f12f5-108">說明轉換的目的型別是否可以存放資料分類。</span><span class="sxs-lookup"><span data-stu-id="f12f5-108">Explains conversions classified by whether the destination type can hold the data.</span></span>  
  
 [<span data-ttu-id="f12f5-109">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="f12f5-109">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 <span data-ttu-id="f12f5-110">討論分類是否 Visual Basic 它們會自動執行的轉換。</span><span class="sxs-lookup"><span data-stu-id="f12f5-110">Discusses conversions classified by whether Visual Basic performs them automatically.</span></span>  
  
 [<span data-ttu-id="f12f5-111">字串與其他類型之間的轉換</span><span class="sxs-lookup"><span data-stu-id="f12f5-111">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 <span data-ttu-id="f12f5-112">說明轉換字串和數字，介於`Boolean`，或日期/時間值。</span><span class="sxs-lookup"><span data-stu-id="f12f5-112">Illustrates converting between strings and numeric, `Boolean`, or date/time values.</span></span>  
  
 [<span data-ttu-id="f12f5-113">如何： 將物件轉換成 Visual Basic 中的另一個類型</span><span class="sxs-lookup"><span data-stu-id="f12f5-113">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 <span data-ttu-id="f12f5-114">示範如何轉換`Object`變數設為任何其他資料類型。</span><span class="sxs-lookup"><span data-stu-id="f12f5-114">Shows how to convert an `Object` variable to any other data type.</span></span>  
  
 [<span data-ttu-id="f12f5-115">陣列轉換</span><span class="sxs-lookup"><span data-stu-id="f12f5-115">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 <span data-ttu-id="f12f5-116">逐步執行不同的資料類型的陣列之間轉換的程序。</span><span class="sxs-lookup"><span data-stu-id="f12f5-116">Steps you through the process of converting between arrays of different data types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f12f5-117">相關章節</span><span class="sxs-lookup"><span data-stu-id="f12f5-117">Related Sections</span></span>  
 [<span data-ttu-id="f12f5-118">資料類型</span><span class="sxs-lookup"><span data-stu-id="f12f5-118">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 <span data-ttu-id="f12f5-119">介紹 Visual Basic 資料類型，並說明如何使用它們。</span><span class="sxs-lookup"><span data-stu-id="f12f5-119">Introduces the Visual Basic data types and describes how to use them.</span></span>  
  
 [<span data-ttu-id="f12f5-120">資料類型</span><span class="sxs-lookup"><span data-stu-id="f12f5-120">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)  
 <span data-ttu-id="f12f5-121">列出 Visual Basic 所提供的基本資料類型。</span><span class="sxs-lookup"><span data-stu-id="f12f5-121">Lists the elementary data types supplied by Visual Basic.</span></span>  
  
 [<span data-ttu-id="f12f5-122">資料類型的疑難排解</span><span class="sxs-lookup"><span data-stu-id="f12f5-122">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 <span data-ttu-id="f12f5-123">討論使用資料型別時可能發生的一些常見問題。</span><span class="sxs-lookup"><span data-stu-id="f12f5-123">Discusses some common problems that can arise when working with data types.</span></span>

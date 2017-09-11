---
title: "在 Visual Basic 型別轉換 |Microsoft 文件"
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
- conversions, type
- data types [Visual Basic], changing
- variables [Visual Basic], changing data type
- type conversion
- conversions, data type
- changing data types
- data type conversion
ms.assetid: 1cdacd21-ba31-4b62-b5be-395e41eeaa17
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
ms.openlocfilehash: 61606572dd1f10dc5df4ed4baec02f230a23c8d6
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="type-conversions-in-visual-basic"></a><span data-ttu-id="f37d3-102">Visual Basic 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="f37d3-102">Type Conversions in Visual Basic</span></span>
<span data-ttu-id="f37d3-103">將值從一種資料類型變更為其他類型的程序稱為*轉換*。</span><span class="sxs-lookup"><span data-stu-id="f37d3-103">The process of changing a value from one data type to another type is called *conversion*.</span></span> <span data-ttu-id="f37d3-104">轉換為*擴展*或*縮小*，取決於相關型別的資料容量。</span><span class="sxs-lookup"><span data-stu-id="f37d3-104">Conversions are either *widening* or *narrowing*, depending on the data capacities of the types involved.</span></span> <span data-ttu-id="f37d3-105">它們也是*隱含*或*明確*，取決於在原始程式碼中的語法。</span><span class="sxs-lookup"><span data-stu-id="f37d3-105">They are also *implicit* or *explicit*, depending on the syntax in the source code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f37d3-106">本章節內容</span><span class="sxs-lookup"><span data-stu-id="f37d3-106">In This Section</span></span>  
 [<span data-ttu-id="f37d3-107">擴展和縮小轉換</span><span class="sxs-lookup"><span data-stu-id="f37d3-107">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 <span data-ttu-id="f37d3-108">說明根據目的型別是否可以保存資料來分類轉換。</span><span class="sxs-lookup"><span data-stu-id="f37d3-108">Explains conversions classified by whether the destination type can hold the data.</span></span>  
  
 [<span data-ttu-id="f37d3-109">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="f37d3-109">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 <span data-ttu-id="f37d3-110">討論轉換分類是否[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]自動執行它們。</span><span class="sxs-lookup"><span data-stu-id="f37d3-110">Discusses conversions classified by whether [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] performs them automatically.</span></span>  
  
 [<span data-ttu-id="f37d3-111">字串與其他類型之間的轉換</span><span class="sxs-lookup"><span data-stu-id="f37d3-111">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 <span data-ttu-id="f37d3-112">說明如何轉換字串和數字、 `Boolean`，或日期/時間值。</span><span class="sxs-lookup"><span data-stu-id="f37d3-112">Illustrates converting between strings and numeric, `Boolean`, or date/time values.</span></span>  
  
 [<span data-ttu-id="f37d3-113">如何︰ 將物件轉換成 Visual Basic 中的另一個型別</span><span class="sxs-lookup"><span data-stu-id="f37d3-113">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 <span data-ttu-id="f37d3-114">示範如何將轉換`Object`變數設為任何其他資料類型。</span><span class="sxs-lookup"><span data-stu-id="f37d3-114">Shows how to convert an `Object` variable to any other data type.</span></span>  
  
 [<span data-ttu-id="f37d3-115">陣列轉換</span><span class="sxs-lookup"><span data-stu-id="f37d3-115">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 <span data-ttu-id="f37d3-116">逐步解說的不同資料型別的陣列之間進行轉換程序。</span><span class="sxs-lookup"><span data-stu-id="f37d3-116">Steps you through the process of converting between arrays of different data types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f37d3-117">相關章節</span><span class="sxs-lookup"><span data-stu-id="f37d3-117">Related Sections</span></span>  
 [<span data-ttu-id="f37d3-118">資料類型</span><span class="sxs-lookup"><span data-stu-id="f37d3-118">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 <span data-ttu-id="f37d3-119">介紹[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]資料型別，並說明如何使用它們。</span><span class="sxs-lookup"><span data-stu-id="f37d3-119">Introduces the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] data types and describes how to use them.</span></span>  
  
 [<span data-ttu-id="f37d3-120">資料類型</span><span class="sxs-lookup"><span data-stu-id="f37d3-120">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 <span data-ttu-id="f37d3-121">列出所提供的基本資料型別[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f37d3-121">Lists the elementary data types supplied by [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
 [<span data-ttu-id="f37d3-122">資料類型的疑難排解</span><span class="sxs-lookup"><span data-stu-id="f37d3-122">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 <span data-ttu-id="f37d3-123">討論資料型別時可能發生的一些常見問題。</span><span class="sxs-lookup"><span data-stu-id="f37d3-123">Discusses some common problems that can arise when working with data types.</span></span>

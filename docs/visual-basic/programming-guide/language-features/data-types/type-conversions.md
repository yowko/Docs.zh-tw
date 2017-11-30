---
title: "Visual Basic 中的類型轉換"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- conversions [Visual Basic], type
- data types [Visual Basic], changing
- variables [Visual Basic], changing data type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- changing data types [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 1cdacd21-ba31-4b62-b5be-395e41eeaa17
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b46d813b4fcadd975d87b235e9f3350a365949fa
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="type-conversions-in-visual-basic"></a><span data-ttu-id="4e46f-102">Visual Basic 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="4e46f-102">Type Conversions in Visual Basic</span></span>
<span data-ttu-id="4e46f-103">將值從一種資料類型變更為其他類型的程序稱為*轉換*。</span><span class="sxs-lookup"><span data-stu-id="4e46f-103">The process of changing a value from one data type to another type is called *conversion*.</span></span> <span data-ttu-id="4e46f-104">轉換為*擴展*或*縮小*，取決於相關類型的資料容量。</span><span class="sxs-lookup"><span data-stu-id="4e46f-104">Conversions are either *widening* or *narrowing*, depending on the data capacities of the types involved.</span></span> <span data-ttu-id="4e46f-105">它們也是*隱含*或*明確*，取決於在原始程式碼中的語法。</span><span class="sxs-lookup"><span data-stu-id="4e46f-105">They are also *implicit* or *explicit*, depending on the syntax in the source code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4e46f-106">本章節內容</span><span class="sxs-lookup"><span data-stu-id="4e46f-106">In This Section</span></span>  
 [<span data-ttu-id="4e46f-107">擴展和縮小轉換</span><span class="sxs-lookup"><span data-stu-id="4e46f-107">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 <span data-ttu-id="4e46f-108">說明項目分類的目的型別是否可以保存資料的轉換。</span><span class="sxs-lookup"><span data-stu-id="4e46f-108">Explains conversions classified by whether the destination type can hold the data.</span></span>  
  
 [<span data-ttu-id="4e46f-109">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="4e46f-109">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 <span data-ttu-id="4e46f-110">討論分類是否由轉換[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]自動執行它們。</span><span class="sxs-lookup"><span data-stu-id="4e46f-110">Discusses conversions classified by whether [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] performs them automatically.</span></span>  
  
 [<span data-ttu-id="4e46f-111">字串與其他類型之間的轉換</span><span class="sxs-lookup"><span data-stu-id="4e46f-111">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 <span data-ttu-id="4e46f-112">說明如何轉換字串與數字之間`Boolean`，或日期/時間值。</span><span class="sxs-lookup"><span data-stu-id="4e46f-112">Illustrates converting between strings and numeric, `Boolean`, or date/time values.</span></span>  
  
 [<span data-ttu-id="4e46f-113">如何： 將物件轉換成 Visual Basic 中的另一個類型</span><span class="sxs-lookup"><span data-stu-id="4e46f-113">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 <span data-ttu-id="4e46f-114">示範如何將轉換`Object`變數設為任何其他資料類型。</span><span class="sxs-lookup"><span data-stu-id="4e46f-114">Shows how to convert an `Object` variable to any other data type.</span></span>  
  
 [<span data-ttu-id="4e46f-115">陣列轉換</span><span class="sxs-lookup"><span data-stu-id="4e46f-115">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 <span data-ttu-id="4e46f-116">逐步執行不同的資料類型的陣列間的轉換程序。</span><span class="sxs-lookup"><span data-stu-id="4e46f-116">Steps you through the process of converting between arrays of different data types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4e46f-117">相關章節</span><span class="sxs-lookup"><span data-stu-id="4e46f-117">Related Sections</span></span>  
 [<span data-ttu-id="4e46f-118">資料類型</span><span class="sxs-lookup"><span data-stu-id="4e46f-118">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 <span data-ttu-id="4e46f-119">導入了[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]資料類型，並說明如何使用它們。</span><span class="sxs-lookup"><span data-stu-id="4e46f-119">Introduces the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] data types and describes how to use them.</span></span>  
  
 [<span data-ttu-id="4e46f-120">資料類型</span><span class="sxs-lookup"><span data-stu-id="4e46f-120">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 <span data-ttu-id="4e46f-121">列出所提供的基本資料型別[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4e46f-121">Lists the elementary data types supplied by [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
 [<span data-ttu-id="4e46f-122">資料類型的疑難排解</span><span class="sxs-lookup"><span data-stu-id="4e46f-122">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 <span data-ttu-id="4e46f-123">討論使用資料型別時可能發生的一些常見問題。</span><span class="sxs-lookup"><span data-stu-id="4e46f-123">Discusses some common problems that can arise when working with data types.</span></span>

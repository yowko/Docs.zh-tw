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
ms.openlocfilehash: ee8700ea757cee9c20e2598de029f54ae33a7114
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91090153"
---
# <a name="type-conversions-in-visual-basic"></a><span data-ttu-id="ecfa1-102">Visual Basic 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="ecfa1-102">Type Conversions in Visual Basic</span></span>

<span data-ttu-id="ecfa1-103">將某個資料類型的值變更為另一個類型的程式稱為 *轉換*。</span><span class="sxs-lookup"><span data-stu-id="ecfa1-103">The process of changing a value from one data type to another type is called *conversion*.</span></span> <span data-ttu-id="ecfa1-104">轉換可以 *擴展* 或 *縮小*，視所涉及之類型的資料容量而定。</span><span class="sxs-lookup"><span data-stu-id="ecfa1-104">Conversions are either *widening* or *narrowing*, depending on the data capacities of the types involved.</span></span> <span data-ttu-id="ecfa1-105">它們也是 *隱含* 或 *明確*的，視原始程式碼中的語法而定。</span><span class="sxs-lookup"><span data-stu-id="ecfa1-105">They are also *implicit* or *explicit*, depending on the syntax in the source code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ecfa1-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="ecfa1-106">In This Section</span></span>  

 [<span data-ttu-id="ecfa1-107">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="ecfa1-107">Widening and Narrowing Conversions</span></span>](widening-and-narrowing-conversions.md)  
 <span data-ttu-id="ecfa1-108">說明依據目的地類型是否可以保存資料分類的轉換。</span><span class="sxs-lookup"><span data-stu-id="ecfa1-108">Explains conversions classified by whether the destination type can hold the data.</span></span>  
  
 [<span data-ttu-id="ecfa1-109">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="ecfa1-109">Implicit and Explicit Conversions</span></span>](implicit-and-explicit-conversions.md)  
 <span data-ttu-id="ecfa1-110">討論 Visual Basic 是否自動執行分類的轉換。</span><span class="sxs-lookup"><span data-stu-id="ecfa1-110">Discusses conversions classified by whether Visual Basic performs them automatically.</span></span>  
  
 [<span data-ttu-id="ecfa1-111">字串與其他類型之間的轉換</span><span class="sxs-lookup"><span data-stu-id="ecfa1-111">Conversions Between Strings and Other Types</span></span>](conversions-between-strings-and-other-types.md)  
 <span data-ttu-id="ecfa1-112">說明如何在字串與數值、 `Boolean` 或日期/時間值之間進行轉換。</span><span class="sxs-lookup"><span data-stu-id="ecfa1-112">Illustrates converting between strings and numeric, `Boolean`, or date/time values.</span></span>  
  
 [<span data-ttu-id="ecfa1-113">如何：在 Visual Basic 中將物件轉換成其他類型</span><span class="sxs-lookup"><span data-stu-id="ecfa1-113">How to: Convert an Object to Another Type in Visual Basic</span></span>](how-to-convert-an-object-to-another-type.md)  
 <span data-ttu-id="ecfa1-114">顯示如何將變數轉換 `Object` 成任何其他資料類型。</span><span class="sxs-lookup"><span data-stu-id="ecfa1-114">Shows how to convert an `Object` variable to any other data type.</span></span>  
  
 [<span data-ttu-id="ecfa1-115">陣列轉換</span><span class="sxs-lookup"><span data-stu-id="ecfa1-115">Array Conversions</span></span>](array-conversions.md)  
 <span data-ttu-id="ecfa1-116">逐步引導您完成在不同資料類型的陣列之間轉換的程式。</span><span class="sxs-lookup"><span data-stu-id="ecfa1-116">Steps you through the process of converting between arrays of different data types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ecfa1-117">相關章節</span><span class="sxs-lookup"><span data-stu-id="ecfa1-117">Related Sections</span></span>  

 [<span data-ttu-id="ecfa1-118">Data types (資料類型)</span><span class="sxs-lookup"><span data-stu-id="ecfa1-118">Data Types</span></span>](index.md)  
 <span data-ttu-id="ecfa1-119">介紹 Visual Basic 資料類型，並描述其使用方式。</span><span class="sxs-lookup"><span data-stu-id="ecfa1-119">Introduces the Visual Basic data types and describes how to use them.</span></span>  
  
 [<span data-ttu-id="ecfa1-120">Data types (資料類型)</span><span class="sxs-lookup"><span data-stu-id="ecfa1-120">Data Types</span></span>](../../../language-reference/data-types/index.md)  
 <span data-ttu-id="ecfa1-121">列出 Visual Basic 所提供的基本資料類型。</span><span class="sxs-lookup"><span data-stu-id="ecfa1-121">Lists the elementary data types supplied by Visual Basic.</span></span>  
  
 [<span data-ttu-id="ecfa1-122">疑難排解資料類型的問題</span><span class="sxs-lookup"><span data-stu-id="ecfa1-122">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)  
 <span data-ttu-id="ecfa1-123">討論使用資料類型時可能發生的一些常見問題。</span><span class="sxs-lookup"><span data-stu-id="ecfa1-123">Discusses some common problems that can arise when working with data types.</span></span>

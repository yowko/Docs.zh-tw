---
title: 陣列轉換
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], converting type
- type conversion [Visual Basic], arrays
- conversions [Visual Basic], type
- arrays [Visual Basic], data types
- conversions [Visual Basic], data type
- object arrays [Visual Basic], converting type
- data type conversion [Visual Basic], array conversions
- conversions [Visual Basic], array types
- object arrays
ms.assetid: fceff7d2-a1b7-44c7-b9aa-8bd831d8a444
ms.openlocfilehash: 375c75c954f3be535272d674d9b786cad46b1a01
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077185"
---
# <a name="array-conversions-visual-basic"></a><span data-ttu-id="6666b-102">陣列轉換 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6666b-102">Array Conversions (Visual Basic)</span></span>

<span data-ttu-id="6666b-103">如果您符合下列條件，您可以將陣列類型轉換成不同的陣列類型：</span><span class="sxs-lookup"><span data-stu-id="6666b-103">You can convert an array type to a different array type provided you meet the following conditions:</span></span>  
  
- <span data-ttu-id="6666b-104">**相等的順位。**</span><span class="sxs-lookup"><span data-stu-id="6666b-104">**Equal Rank.**</span></span> <span data-ttu-id="6666b-105">這兩個數組的等級必須相同，也就是它們必須具有相同的維度數目。</span><span class="sxs-lookup"><span data-stu-id="6666b-105">The ranks of the two arrays must be the same, that is, they must have the same number of dimensions.</span></span> <span data-ttu-id="6666b-106">不過，個別維度的長度不一定要相同。</span><span class="sxs-lookup"><span data-stu-id="6666b-106">However, the lengths of the respective dimensions do not need to be the same.</span></span>  
  
- <span data-ttu-id="6666b-107">**元素資料類型。**</span><span class="sxs-lookup"><span data-stu-id="6666b-107">**Element Data Type.**</span></span> <span data-ttu-id="6666b-108">這兩個數組的專案資料類型必須是參考型別。</span><span class="sxs-lookup"><span data-stu-id="6666b-108">The data types of the elements of both arrays must be reference types.</span></span> <span data-ttu-id="6666b-109">您無法將陣列轉換成 `Integer` `Long` 陣列，甚至 `Object` 是陣列，因為至少有一個實值型別參與。</span><span class="sxs-lookup"><span data-stu-id="6666b-109">You cannot convert an `Integer` array to a `Long` array, or even to an `Object` array, because at least one value type is involved.</span></span> <span data-ttu-id="6666b-110">如需詳細資訊，請參閱 [Value Types and Reference Types](value-types-and-reference-types.md)。</span><span class="sxs-lookup"><span data-stu-id="6666b-110">For more information, see [Value Types and Reference Types](value-types-and-reference-types.md).</span></span>  
  
- <span data-ttu-id="6666b-111">**自由 兌換。**</span><span class="sxs-lookup"><span data-stu-id="6666b-111">**Convertibility.**</span></span> <span data-ttu-id="6666b-112">轉換（擴大或縮小）必須能夠在兩個數組的元素類型之間進行。</span><span class="sxs-lookup"><span data-stu-id="6666b-112">A conversion, either widening or narrowing, must be possible between the element types of the two arrays.</span></span> <span data-ttu-id="6666b-113">失敗這項需求的範例是在 `String` 陣列和衍生自的類別陣列之間嘗試轉換 <xref:System.Attribute?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="6666b-113">An example that fails this requirement is an attempted conversion between a `String` array and an array of a class derived from <xref:System.Attribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6666b-114">這兩種類型沒有任何共同的類型，而且它們之間不會有任何種類的轉換。</span><span class="sxs-lookup"><span data-stu-id="6666b-114">These two types have nothing in common, and no conversion of any kind exists between them.</span></span>  
  
 <span data-ttu-id="6666b-115">將某個陣列類型轉換成另一個陣列類型時，會根據個別元素的轉換是擴展或縮小而進行擴展或縮小。</span><span class="sxs-lookup"><span data-stu-id="6666b-115">A conversion of one array type to another is widening or narrowing depending on whether the conversion of the respective elements is widening or narrowing.</span></span> <span data-ttu-id="6666b-116">如需詳細資訊，請參閱 [Widening and Narrowing Conversions](widening-and-narrowing-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="6666b-116">For more information, see [Widening and Narrowing Conversions](widening-and-narrowing-conversions.md).</span></span>  
  
## <a name="conversion-to-an-object-array"></a><span data-ttu-id="6666b-117">轉換成物件陣列</span><span class="sxs-lookup"><span data-stu-id="6666b-117">Conversion to an Object Array</span></span>  

 <span data-ttu-id="6666b-118">當您宣告 `Object` 陣列但未將它初始化時，它的專案型別會 `Object` 維持未初始化的狀態。</span><span class="sxs-lookup"><span data-stu-id="6666b-118">When you declare an `Object` array without initializing it, its element type is `Object` as long as it remains uninitialized.</span></span> <span data-ttu-id="6666b-119">當您將它設定為特定類別的陣列時，它會採用該類別的型別。</span><span class="sxs-lookup"><span data-stu-id="6666b-119">When you set it to an array of a specific class, it takes on the type of that class.</span></span> <span data-ttu-id="6666b-120">不過，其基礎類型仍然是 `Object` ，而且您可以接著將它設定為不相關類別的另一個陣列。</span><span class="sxs-lookup"><span data-stu-id="6666b-120">However, its underlying type is still `Object`, and you can subsequently set it to another array of an unrelated class.</span></span> <span data-ttu-id="6666b-121">由於所有類別都是衍生自 `Object` ，因此您可以將陣列的元素類型從任何類別變更為其他任何類別。</span><span class="sxs-lookup"><span data-stu-id="6666b-121">Since all classes derive from `Object`, you can change the array's element type from any class to any other class.</span></span>  
  
 <span data-ttu-id="6666b-122">在下列範例中，類型與之間不會有任何轉換 `student` `String` ，但兩者都是衍生自 `Object` ，因此所有指派都是有效的。</span><span class="sxs-lookup"><span data-stu-id="6666b-122">In the following example, no conversion exists between types `student` and `String`, but both derive from `Object`, so all assignments are valid.</span></span>  
  
```vb  
' Assume student has already been defined as a class.  
Dim testArray() As Object  
' testArray is still an Object array at this point.  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
testArray = New student(3) {}  
' testArray is now of type student().  
testArray = names  
' testArray is now a String array.  
```  
  
### <a name="underlying-type-of-an-array"></a><span data-ttu-id="6666b-123">陣列的基礎類型</span><span class="sxs-lookup"><span data-stu-id="6666b-123">Underlying Type of an Array</span></span>  

 <span data-ttu-id="6666b-124">如果您原先宣告具有特定類別的陣列，其基礎元素類型就是該類別。</span><span class="sxs-lookup"><span data-stu-id="6666b-124">If you originally declare an array with a specific class, its underlying element type is that class.</span></span> <span data-ttu-id="6666b-125">如果您之後將它設定為另一個類別的陣列，則這兩個類別之間必須有轉換。</span><span class="sxs-lookup"><span data-stu-id="6666b-125">If you subsequently set it to an array of another class, there must be a conversion between the two classes.</span></span>  
  
 <span data-ttu-id="6666b-126">在下列範例中， `students` 是 `student` 陣列。</span><span class="sxs-lookup"><span data-stu-id="6666b-126">In the following example, `students` is a `student` array.</span></span> <span data-ttu-id="6666b-127">由於和之間沒有任何轉換存在 `String` `student` ，最後一個語句會失敗。</span><span class="sxs-lookup"><span data-stu-id="6666b-127">Since no conversion exists between `String` and `student`, the last statement fails.</span></span>  
  
```vb  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a><span data-ttu-id="6666b-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6666b-128">See also</span></span>

- [<span data-ttu-id="6666b-129">Data types (資料類型)</span><span class="sxs-lookup"><span data-stu-id="6666b-129">Data Types</span></span>](index.md)
- [<span data-ttu-id="6666b-130">Visual Basic 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="6666b-130">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="6666b-131">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="6666b-131">Implicit and Explicit Conversions</span></span>](implicit-and-explicit-conversions.md)
- [<span data-ttu-id="6666b-132">字串與其他類型之間的轉換</span><span class="sxs-lookup"><span data-stu-id="6666b-132">Conversions Between Strings and Other Types</span></span>](conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="6666b-133">如何：在 Visual Basic 中將物件轉換成其他類型</span><span class="sxs-lookup"><span data-stu-id="6666b-133">How to: Convert an Object to Another Type in Visual Basic</span></span>](how-to-convert-an-object-to-another-type.md)
- [<span data-ttu-id="6666b-134">Data types (資料類型)</span><span class="sxs-lookup"><span data-stu-id="6666b-134">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="6666b-135">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="6666b-135">Type Conversion Functions</span></span>](../../../language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="6666b-136">陣列</span><span class="sxs-lookup"><span data-stu-id="6666b-136">Arrays</span></span>](../arrays/index.md)

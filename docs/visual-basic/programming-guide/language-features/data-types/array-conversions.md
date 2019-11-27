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
ms.openlocfilehash: 622ebe8a77f2dfbeb35e0408be48622d93d409c6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345854"
---
# <a name="array-conversions-visual-basic"></a><span data-ttu-id="6ca18-102">陣列轉換 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ca18-102">Array Conversions (Visual Basic)</span></span>
<span data-ttu-id="6ca18-103">您可以將陣列類型轉換成不同的陣列類型，前提是您符合下列條件：</span><span class="sxs-lookup"><span data-stu-id="6ca18-103">You can convert an array type to a different array type provided you meet the following conditions:</span></span>  
  
- <span data-ttu-id="6ca18-104">**相等順位。**</span><span class="sxs-lookup"><span data-stu-id="6ca18-104">**Equal Rank.**</span></span> <span data-ttu-id="6ca18-105">這兩個數組的次序必須相同，也就是說，它們必須有相同數目的維度。</span><span class="sxs-lookup"><span data-stu-id="6ca18-105">The ranks of the two arrays must be the same, that is, they must have the same number of dimensions.</span></span> <span data-ttu-id="6ca18-106">不過，個別維度的長度不需要相同。</span><span class="sxs-lookup"><span data-stu-id="6ca18-106">However, the lengths of the respective dimensions do not need to be the same.</span></span>  
  
- <span data-ttu-id="6ca18-107">**元素資料類型。**</span><span class="sxs-lookup"><span data-stu-id="6ca18-107">**Element Data Type.**</span></span> <span data-ttu-id="6ca18-108">這兩個數組之元素的資料類型必須是參考型別。</span><span class="sxs-lookup"><span data-stu-id="6ca18-108">The data types of the elements of both arrays must be reference types.</span></span> <span data-ttu-id="6ca18-109">您無法將 `Integer` 陣列轉換成 `Long` 陣列，甚至是 `Object` 陣列，因為至少有一個數值型別涉及。</span><span class="sxs-lookup"><span data-stu-id="6ca18-109">You cannot convert an `Integer` array to a `Long` array, or even to an `Object` array, because at least one value type is involved.</span></span> <span data-ttu-id="6ca18-110">如需詳細資訊，請參閱 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)。</span><span class="sxs-lookup"><span data-stu-id="6ca18-110">For more information, see [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span></span>  
  
- <span data-ttu-id="6ca18-111">**可轉換性.**</span><span class="sxs-lookup"><span data-stu-id="6ca18-111">**Convertibility.**</span></span> <span data-ttu-id="6ca18-112">這兩個數組的元素類型之間必須有轉換，也就是擴展或縮小。</span><span class="sxs-lookup"><span data-stu-id="6ca18-112">A conversion, either widening or narrowing, must be possible between the element types of the two arrays.</span></span> <span data-ttu-id="6ca18-113">失敗這項需求的範例是嘗試在 `String` 陣列與衍生自 <xref:System.Attribute?displayProperty=nameWithType>的類別陣列之間進行轉換。</span><span class="sxs-lookup"><span data-stu-id="6ca18-113">An example that fails this requirement is an attempted conversion between a `String` array and an array of a class derived from <xref:System.Attribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6ca18-114">這兩種類型都不會有任何作用，而且它們之間不會有任何類型的轉換。</span><span class="sxs-lookup"><span data-stu-id="6ca18-114">These two types have nothing in common, and no conversion of any kind exists between them.</span></span>  
  
 <span data-ttu-id="6ca18-115">將一個陣列型別轉換成另一個，是根據個別元素的轉換是擴展或縮小而定。</span><span class="sxs-lookup"><span data-stu-id="6ca18-115">A conversion of one array type to another is widening or narrowing depending on whether the conversion of the respective elements is widening or narrowing.</span></span> <span data-ttu-id="6ca18-116">如需詳細資訊，請參閱 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="6ca18-116">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
## <a name="conversion-to-an-object-array"></a><span data-ttu-id="6ca18-117">轉換成物件陣列</span><span class="sxs-lookup"><span data-stu-id="6ca18-117">Conversion to an Object Array</span></span>  
 <span data-ttu-id="6ca18-118">當您宣告 `Object` 陣列而不將它初始化時，只要它保持未初始化，它的元素類型就會 `Object`。</span><span class="sxs-lookup"><span data-stu-id="6ca18-118">When you declare an `Object` array without initializing it, its element type is `Object` as long as it remains uninitialized.</span></span> <span data-ttu-id="6ca18-119">當您將它設定為特定類別的陣列時，它會採用該類別的類型。</span><span class="sxs-lookup"><span data-stu-id="6ca18-119">When you set it to an array of a specific class, it takes on the type of that class.</span></span> <span data-ttu-id="6ca18-120">不過，它的基礎類型仍然 `Object`，您可以接著將它設定為不相關類別的另一個陣列。</span><span class="sxs-lookup"><span data-stu-id="6ca18-120">However, its underlying type is still `Object`, and you can subsequently set it to another array of an unrelated class.</span></span> <span data-ttu-id="6ca18-121">由於所有類別都是衍生自 `Object`，因此您可以將陣列的元素類型從任何類別變更為任何其他類別。</span><span class="sxs-lookup"><span data-stu-id="6ca18-121">Since all classes derive from `Object`, you can change the array's element type from any class to any other class.</span></span>  
  
 <span data-ttu-id="6ca18-122">在下列範例中，類型 `student` 和 `String`之間不存在任何轉換，但兩者都是衍生自 `Object`，因此所有指派都是有效的。</span><span class="sxs-lookup"><span data-stu-id="6ca18-122">In the following example, no conversion exists between types `student` and `String`, but both derive from `Object`, so all assignments are valid.</span></span>  
  
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
  
### <a name="underlying-type-of-an-array"></a><span data-ttu-id="6ca18-123">陣列的基礎類型</span><span class="sxs-lookup"><span data-stu-id="6ca18-123">Underlying Type of an Array</span></span>  
 <span data-ttu-id="6ca18-124">如果您最初宣告具有特定類別的陣列，其基礎元素類型就是該類別。</span><span class="sxs-lookup"><span data-stu-id="6ca18-124">If you originally declare an array with a specific class, its underlying element type is that class.</span></span> <span data-ttu-id="6ca18-125">如果您接著將它設定為另一個類別的陣列，則這兩個類別之間必須有轉換。</span><span class="sxs-lookup"><span data-stu-id="6ca18-125">If you subsequently set it to an array of another class, there must be a conversion between the two classes.</span></span>  
  
 <span data-ttu-id="6ca18-126">在下列範例中，`students` 是 `student` 陣列。</span><span class="sxs-lookup"><span data-stu-id="6ca18-126">In the following example, `students` is a `student` array.</span></span> <span data-ttu-id="6ca18-127">因為 `String` 與 `student`之間沒有任何轉換存在，所以最後一個語句會失敗。</span><span class="sxs-lookup"><span data-stu-id="6ca18-127">Since no conversion exists between `String` and `student`, the last statement fails.</span></span>  
  
```vb  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a><span data-ttu-id="6ca18-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="6ca18-128">See also</span></span>

- [<span data-ttu-id="6ca18-129">資料類型</span><span class="sxs-lookup"><span data-stu-id="6ca18-129">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="6ca18-130">Visual Basic 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="6ca18-130">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="6ca18-131">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="6ca18-131">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="6ca18-132">字串與其他類型之間的轉換</span><span class="sxs-lookup"><span data-stu-id="6ca18-132">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="6ca18-133">如何：在 Visual Basic 中將物件轉換為另一種類型</span><span class="sxs-lookup"><span data-stu-id="6ca18-133">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [<span data-ttu-id="6ca18-134">資料類型</span><span class="sxs-lookup"><span data-stu-id="6ca18-134">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="6ca18-135">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="6ca18-135">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="6ca18-136">陣列</span><span class="sxs-lookup"><span data-stu-id="6ca18-136">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)

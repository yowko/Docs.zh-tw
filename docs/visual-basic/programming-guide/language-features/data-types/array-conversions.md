---
title: 陣列轉換 (Visual Basic)
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
ms.openlocfilehash: 88002e2c099ed9503beddb190d243aadcc1087fc
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58830197"
---
# <a name="array-conversions-visual-basic"></a><span data-ttu-id="0f5de-102">陣列轉換 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f5de-102">Array Conversions (Visual Basic)</span></span>
<span data-ttu-id="0f5de-103">您可以將陣列型別轉換成不同的陣列型別，提供符合下列條件：</span><span class="sxs-lookup"><span data-stu-id="0f5de-103">You can convert an array type to a different array type provided you meet the following conditions:</span></span>  
  
-   <span data-ttu-id="0f5de-104">**相等的順位。**</span><span class="sxs-lookup"><span data-stu-id="0f5de-104">**Equal Rank.**</span></span> <span data-ttu-id="0f5de-105">兩個陣列的陣序規範必須相同，也就是它們必須具有相同的維度數目。</span><span class="sxs-lookup"><span data-stu-id="0f5de-105">The ranks of the two arrays must be the same, that is, they must have the same number of dimensions.</span></span> <span data-ttu-id="0f5de-106">不過，個別的維度的長度不需要相同。</span><span class="sxs-lookup"><span data-stu-id="0f5de-106">However, the lengths of the respective dimensions do not need to be the same.</span></span>  
  
-   <span data-ttu-id="0f5de-107">**項目資料型別。**</span><span class="sxs-lookup"><span data-stu-id="0f5de-107">**Element Data Type.**</span></span> <span data-ttu-id="0f5de-108">兩個陣列元素的資料類型必須是參考型別。</span><span class="sxs-lookup"><span data-stu-id="0f5de-108">The data types of the elements of both arrays must be reference types.</span></span> <span data-ttu-id="0f5de-109">您無法轉換`Integer`陣列`Long`陣列、 或甚至`Object`陣列，因為牽涉到至少一個實值型別。</span><span class="sxs-lookup"><span data-stu-id="0f5de-109">You cannot convert an `Integer` array to a `Long` array, or even to an `Object` array, because at least one value type is involved.</span></span> <span data-ttu-id="0f5de-110">如需詳細資訊，請參閱 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)。</span><span class="sxs-lookup"><span data-stu-id="0f5de-110">For more information, see [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span></span>  
  
-   <span data-ttu-id="0f5de-111">**可轉換性。**</span><span class="sxs-lookup"><span data-stu-id="0f5de-111">**Convertibility.**</span></span> <span data-ttu-id="0f5de-112">轉換，以擴大或縮小，必須能夠在兩個陣列項目類型之間。</span><span class="sxs-lookup"><span data-stu-id="0f5de-112">A conversion, either widening or narrowing, must be possible between the element types of the two arrays.</span></span> <span data-ttu-id="0f5de-113">舉例來說，未通過這項需求是嘗試之間的轉換`String`陣列和陣列的類別衍生自<xref:System.Attribute?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="0f5de-113">An example that fails this requirement is an attempted conversion between a `String` array and an array of a class derived from <xref:System.Attribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0f5de-114">這兩種類型沒有任何共通點，並沒有任何類型的轉換之間存在。</span><span class="sxs-lookup"><span data-stu-id="0f5de-114">These two types have nothing in common, and no conversion of any kind exists between them.</span></span>  
  
 <span data-ttu-id="0f5de-115">擴展或縮小取決於個別的項目轉換是否會擴大或縮小到另一個陣列類型的轉換。</span><span class="sxs-lookup"><span data-stu-id="0f5de-115">A conversion of one array type to another is widening or narrowing depending on whether the conversion of the respective elements is widening or narrowing.</span></span> <span data-ttu-id="0f5de-116">如需詳細資訊，請參閱 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="0f5de-116">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
## <a name="conversion-to-an-object-array"></a><span data-ttu-id="0f5de-117">轉換成物件陣列</span><span class="sxs-lookup"><span data-stu-id="0f5de-117">Conversion to an Object Array</span></span>  
 <span data-ttu-id="0f5de-118">當您宣告`Object`但不初始化，其項目類型的陣列是`Object`，只要它會保持未初始化。</span><span class="sxs-lookup"><span data-stu-id="0f5de-118">When you declare an `Object` array without initializing it, its element type is `Object` as long as it remains uninitialized.</span></span> <span data-ttu-id="0f5de-119">當您設定特定類別的陣列時，它會在該類別的型別。</span><span class="sxs-lookup"><span data-stu-id="0f5de-119">When you set it to an array of a specific class, it takes on the type of that class.</span></span> <span data-ttu-id="0f5de-120">不過，其基礎類型仍`Object`，以及您可以接著將它設定為不相關的類別的另一個陣列。</span><span class="sxs-lookup"><span data-stu-id="0f5de-120">However, its underlying type is still `Object`, and you can subsequently set it to another array of an unrelated class.</span></span> <span data-ttu-id="0f5de-121">因為所有的類別衍生自`Object`，您可以從任何類別變更陣列的項目類型，與任何其他類別。</span><span class="sxs-lookup"><span data-stu-id="0f5de-121">Since all classes derive from `Object`, you can change the array's element type from any class to any other class.</span></span>  
  
 <span data-ttu-id="0f5de-122">在下列範例中，沒有任何轉換存在型別之間`student`並`String`，但都是衍生自`Object`，因此所有指派都都有效。</span><span class="sxs-lookup"><span data-stu-id="0f5de-122">In the following example, no conversion exists between types `student` and `String`, but both derive from `Object`, so all assignments are valid.</span></span>  
  
```  
' Assume student has already been defined as a class.  
Dim testArray() As Object  
' testArray is still an Object array at this point.  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
testArray = New student(3) {}  
' testArray is now of type student().  
testArray = names  
' testArray is now a String array.  
```  
  
### <a name="underlying-type-of-an-array"></a><span data-ttu-id="0f5de-123">陣列的基礎類型</span><span class="sxs-lookup"><span data-stu-id="0f5de-123">Underlying Type of an Array</span></span>  
 <span data-ttu-id="0f5de-124">如果您原本宣告具有特定類別的陣列，其基礎的項目類型會是該類別。</span><span class="sxs-lookup"><span data-stu-id="0f5de-124">If you originally declare an array with a specific class, its underlying element type is that class.</span></span> <span data-ttu-id="0f5de-125">如果您接著將它設定為另一個類別的陣列，必須有兩個類別之間的轉換。</span><span class="sxs-lookup"><span data-stu-id="0f5de-125">If you subsequently set it to an array of another class, there must be a conversion between the two classes.</span></span>  
  
 <span data-ttu-id="0f5de-126">在下列範例中，`students`是`student`陣列。</span><span class="sxs-lookup"><span data-stu-id="0f5de-126">In the following example, `students` is a `student` array.</span></span> <span data-ttu-id="0f5de-127">因為沒有任何轉換存在之間`String`和`student`，最後一個陳述式會失敗。</span><span class="sxs-lookup"><span data-stu-id="0f5de-127">Since no conversion exists between `String` and `student`, the last statement fails.</span></span>  
  
```  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a><span data-ttu-id="0f5de-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f5de-128">See also</span></span>

- [<span data-ttu-id="0f5de-129">資料類型</span><span class="sxs-lookup"><span data-stu-id="0f5de-129">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="0f5de-130">在 Visual Basic 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="0f5de-130">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="0f5de-131">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="0f5de-131">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="0f5de-132">字串與其他類型之間的轉換</span><span class="sxs-lookup"><span data-stu-id="0f5de-132">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="0f5de-133">如何：將物件轉換成 Visual Basic 中的另一個類型</span><span class="sxs-lookup"><span data-stu-id="0f5de-133">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [<span data-ttu-id="0f5de-134">資料類型</span><span class="sxs-lookup"><span data-stu-id="0f5de-134">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="0f5de-135">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="0f5de-135">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="0f5de-136">陣列</span><span class="sxs-lookup"><span data-stu-id="0f5de-136">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)

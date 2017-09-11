---
title: "在 Visual Basic 中的基本概念的字串 |Microsoft 文件"
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
- strings [Visual Basic], Like operator
- strings [Visual Basic], Visual Basic
- strings [Visual Basic], regular expressions
ms.assetid: 5674418d-f00d-4f72-9f98-d15897793350
caps.latest.revision: 14
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
ms.openlocfilehash: 98c2707ef8aabc77951b21cfe9f4edcd3a88c863
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="string-basics-in-visual-basic"></a><span data-ttu-id="fa33e-102">Visual Basic 中的字串基礎</span><span class="sxs-lookup"><span data-stu-id="fa33e-102">String Basics in Visual Basic</span></span>
<span data-ttu-id="fa33e-103">`String` 資料類型代表一系列字元 (每個依序代表 `Char` 資料類型的一個執行個體)。</span><span class="sxs-lookup"><span data-stu-id="fa33e-103">The `String` data type represents a series of characters (each representing in turn an instance of the `Char` data type).</span></span> <span data-ttu-id="fa33e-104">本主題介紹 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 中字串的基本概念。</span><span class="sxs-lookup"><span data-stu-id="fa33e-104">This topic introduces the basic concepts of strings in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
## <a name="string-variables"></a><span data-ttu-id="fa33e-105">字串變數</span><span class="sxs-lookup"><span data-stu-id="fa33e-105">String Variables</span></span>  
 <span data-ttu-id="fa33e-106">可將代表字元數列的常值指派給字串的執行個體。</span><span class="sxs-lookup"><span data-stu-id="fa33e-106">An instance of a string can be assigned a literal value that represents a series of characters.</span></span> <span data-ttu-id="fa33e-107">例如: </span><span class="sxs-lookup"><span data-stu-id="fa33e-107">For example:</span></span>  
  
 <span data-ttu-id="fa33e-108">[!code-vb[VbVbalrStrings #&63;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="fa33e-108">[!code-vb[VbVbalrStrings#63](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_1.vb)]</span></span>  
  
 <span data-ttu-id="fa33e-109">`String` 變數也可以接受評估為字串的任何運算式。</span><span class="sxs-lookup"><span data-stu-id="fa33e-109">A `String` variable can also accept any expression that evaluates to a string.</span></span> <span data-ttu-id="fa33e-110">範例如下所示：</span><span class="sxs-lookup"><span data-stu-id="fa33e-110">Examples are shown below:</span></span>  
  
 <span data-ttu-id="fa33e-111">[!code-vb[VbVbalrStrings #&64;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="fa33e-111">[!code-vb[VbVbalrStrings#64](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_2.vb)]</span></span>  
  
 <span data-ttu-id="fa33e-112">指派給 `String` 變數的任何常值必須括在引號 ("") 內。</span><span class="sxs-lookup"><span data-stu-id="fa33e-112">Any literal that is assigned to a `String` variable must be enclosed in quotation marks ("").</span></span> <span data-ttu-id="fa33e-113">這表示無法以引號表示字串內的引號。</span><span class="sxs-lookup"><span data-stu-id="fa33e-113">This means that a quotation mark within a string cannot be represented by a quotation mark.</span></span> <span data-ttu-id="fa33e-114">例如，下列程式碼會導致編譯器錯誤：</span><span class="sxs-lookup"><span data-stu-id="fa33e-114">For example, the following code causes a compiler error:</span></span>  
  
 <span data-ttu-id="fa33e-115">[!code-vb[VbVbalrStrings #&65;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="fa33e-115">[!code-vb[VbVbalrStrings#65](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_3.vb)]</span></span>  
  
 <span data-ttu-id="fa33e-116">此程式碼會造成錯誤，因為編譯器會終止第二個引號後的字串，並將字串的其餘部分解譯為程式碼。</span><span class="sxs-lookup"><span data-stu-id="fa33e-116">This code causes an error because the compiler terminates the string after the second quotation mark, and the remainder of the string is interpreted as code.</span></span> <span data-ttu-id="fa33e-117">為解決此問題，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 會將字串常值中的兩個引號解譯為字串中的一個引號。</span><span class="sxs-lookup"><span data-stu-id="fa33e-117">To solve this problem, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] interprets two quotation marks in a string literal as one quotation mark in the string.</span></span> <span data-ttu-id="fa33e-118">下列範例示範在字串中包含引號的正確方式：</span><span class="sxs-lookup"><span data-stu-id="fa33e-118">The following example demonstrates the correct way to include a quotation mark in a string:</span></span>  
  
 <span data-ttu-id="fa33e-119">[!code-vb[VbVbalrStrings #&66;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="fa33e-119">[!code-vb[VbVbalrStrings#66](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_4.vb)]</span></span>  
  
 <span data-ttu-id="fa33e-120">在上述範例中，`Look` 文字前面的兩個引號會成為字串中的一個引號。</span><span class="sxs-lookup"><span data-stu-id="fa33e-120">In the preceding example, the two quotation marks preceding the word `Look` become one quotation mark in the string.</span></span> <span data-ttu-id="fa33e-121">一行結尾處的三個引號表示字串和字串結束字元的一個引號。</span><span class="sxs-lookup"><span data-stu-id="fa33e-121">The three quotation marks at the end of the line represent one quotation mark in the string and the string termination character.</span></span>  
  
 <span data-ttu-id="fa33e-122">字串常值可以包含多行：</span><span class="sxs-lookup"><span data-stu-id="fa33e-122">String literals can contain multiple lines:</span></span>  
  
```vb  
Dim x = "hello  
world"  
  
```  
  
 <span data-ttu-id="fa33e-123">產生的字串包含用於字串常值 (vbcr、vbcrlf 等) 的新行字元序列。</span><span class="sxs-lookup"><span data-stu-id="fa33e-123">The resulting string contains newline sequences that you used in your string literal (vbcr, vbcrlf, etc.).</span></span>  <span data-ttu-id="fa33e-124">您不再需要使用舊的因應措施：</span><span class="sxs-lookup"><span data-stu-id="fa33e-124">You no longer need to use the old workaround:</span></span>  
  
```vb  
Dim x = <xml><![CDATA[Hello  
World]]></xml>.Value  
  
```  
  
## <a name="characters-in-strings"></a><span data-ttu-id="fa33e-125">字串中的字元</span><span class="sxs-lookup"><span data-stu-id="fa33e-125">Characters in Strings</span></span>  
 <span data-ttu-id="fa33e-126">字串可以視為 `Char` 值序列，且 `String` 類型具有內建函式，可讓您在字串上執行許多操作 (類似於陣列所允許的操作)。</span><span class="sxs-lookup"><span data-stu-id="fa33e-126">A string can be thought of as a series of `Char` values, and the `String` type has built-in functions that allow you to perform many manipulations on a string that resemble the manipulations allowed by arrays.</span></span> <span data-ttu-id="fa33e-127">如 [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] 中的所有陣列，這些都是以零起始的陣列。</span><span class="sxs-lookup"><span data-stu-id="fa33e-127">Like all array in [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)], these are zero-based arrays.</span></span> <span data-ttu-id="fa33e-128">您可以透過 `Chars` 屬性參考字串中的特殊字元 ，讓您能夠依字元在字串中的出現位置存取該字元。</span><span class="sxs-lookup"><span data-stu-id="fa33e-128">You may refer to a specific character in a string through the `Chars` property, which provides a way to access a character by the position in which it appears in the string.</span></span> <span data-ttu-id="fa33e-129">例如: </span><span class="sxs-lookup"><span data-stu-id="fa33e-129">For example:</span></span>  
  
 <span data-ttu-id="fa33e-130">[!code-vb[VbVbalrStrings #&67;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="fa33e-130">[!code-vb[VbVbalrStrings#67](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_5.vb)]</span></span>  
  
 <span data-ttu-id="fa33e-131">在上述範例中，字串的 `Chars` 屬性會傳回字串中的第四個字元，也就是 `D`，並將其指派給 `myChar`。</span><span class="sxs-lookup"><span data-stu-id="fa33e-131">In the above example, the `Chars` property of the string returns the fourth character in the string, which is `D`, and assigns it to `myChar`.</span></span> <span data-ttu-id="fa33e-132">您也可以透過 `Length` 屬性取得特定字串的長度。</span><span class="sxs-lookup"><span data-stu-id="fa33e-132">You can also get the length of a particular string through the `Length` property.</span></span> <span data-ttu-id="fa33e-133">如果您需要在字串上執行多個陣列類型操作，您可以使用字串的 `ToCharArray` 函式將它轉換為 `Char` 執行個體陣列。</span><span class="sxs-lookup"><span data-stu-id="fa33e-133">If you need to perform multiple array-type manipulations on a string, you can convert it to an array of `Char` instances using the `ToCharArray` function of the string.</span></span> <span data-ttu-id="fa33e-134">例如: </span><span class="sxs-lookup"><span data-stu-id="fa33e-134">For example:</span></span>  
  
 <span data-ttu-id="fa33e-135">[!code-vb[VbVbalrStrings #&68;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="fa33e-135">[!code-vb[VbVbalrStrings#68](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_6.vb)]</span></span>  
  
 <span data-ttu-id="fa33e-136">變數 `myArray` 現在包含 `Char` 值的陣列，每個都代表 `myString` 的一個字元。</span><span class="sxs-lookup"><span data-stu-id="fa33e-136">The variable `myArray` now contains an array of `Char` values, each representing a character from `myString`.</span></span>  
  
## <a name="the-immutability-of-strings"></a><span data-ttu-id="fa33e-137">字串的不變性</span><span class="sxs-lookup"><span data-stu-id="fa33e-137">The Immutability of Strings</span></span>  
 <span data-ttu-id="fa33e-138">字串是*變*，的也就是說，其值無法變更一次建立。</span><span class="sxs-lookup"><span data-stu-id="fa33e-138">A string is *immutable*, which means its value cannot be changed once it has been created.</span></span> <span data-ttu-id="fa33e-139">不過，這不會讓您將多個值指派給一個字串變數。</span><span class="sxs-lookup"><span data-stu-id="fa33e-139">However, this does not prevent you from assigning more than one value to a string variable.</span></span> <span data-ttu-id="fa33e-140">參考下列範例：</span><span class="sxs-lookup"><span data-stu-id="fa33e-140">Consider the following example:</span></span>  
  
 <span data-ttu-id="fa33e-141">[!code-vb[VbVbalrStrings #&69;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="fa33e-141">[!code-vb[VbVbalrStrings#69](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_7.vb)]</span></span>  
  
 <span data-ttu-id="fa33e-142">在這裡會建立字串變數、指定值，然後變更其值。</span><span class="sxs-lookup"><span data-stu-id="fa33e-142">Here, a string variable is created, given a value, and then its value is changed.</span></span>  
  
 <span data-ttu-id="fa33e-143">更具體來說，在第一行中，會建立類型 `String` 的執行個體並提供值 `This string is immutable`。</span><span class="sxs-lookup"><span data-stu-id="fa33e-143">More specifically, in the first line, an instance of type `String` is created and given the value `This string is immutable`.</span></span> <span data-ttu-id="fa33e-144">在此範例的第二行，建立新執行個體並指定值 `Or is it?`，且字串變數會捨棄其對第一個執行個體的參考，並儲存新執行個體的參考。</span><span class="sxs-lookup"><span data-stu-id="fa33e-144">In the second line of the example, a new instance is created and given the value `Or is it?`, and the string variable discards its reference to the first instance and stores a reference to the new instance.</span></span>  
  
 <span data-ttu-id="fa33e-145">不同於其他內建資料類型，`String` 是參考類型。</span><span class="sxs-lookup"><span data-stu-id="fa33e-145">Unlike other intrinsic data types, `String` is a reference type.</span></span> <span data-ttu-id="fa33e-146">將參考類型的變數做為引數傳遞給函式或副程式時，會傳遞儲存資料的記憶體位址的參考，而不是字串的實際值。</span><span class="sxs-lookup"><span data-stu-id="fa33e-146">When a variable of reference type is passed as an argument to a function or subroutine, a reference to the memory address where the data is stored is passed instead of the actual value of the string.</span></span> <span data-ttu-id="fa33e-147">因此在前一個範例中，變數的名稱維持不變，但是它指向 `String` 類別的全新和不同的執行個體，其中包含新值。</span><span class="sxs-lookup"><span data-stu-id="fa33e-147">So in the previous example, the name of the variable remains the same, but it points to a new and different instance of the `String` class, which holds the new value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa33e-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa33e-148">See Also</span></span>  
 <span data-ttu-id="fa33e-149">[在 Visual Basic 中的字串簡介](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md) </span><span class="sxs-lookup"><span data-stu-id="fa33e-149">[Introduction to Strings in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md) </span></span>  
<span data-ttu-id="fa33e-150"> [字串資料類型](../../../../visual-basic/language-reference/data-types/string-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="fa33e-150"> [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md) </span></span>  
<span data-ttu-id="fa33e-151"> [Char 資料類型](../../../../visual-basic/language-reference/data-types/char-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="fa33e-151"> [Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md) </span></span>  
<span data-ttu-id="fa33e-152"> [基本字串作業](http://msdn.microsoft.com/library/8133d357-90b5-4b62-9927-43323d99b6b6)</span><span class="sxs-lookup"><span data-stu-id="fa33e-152"> [Basic String Operations](http://msdn.microsoft.com/library/8133d357-90b5-4b62-9927-43323d99b6b6)</span></span>

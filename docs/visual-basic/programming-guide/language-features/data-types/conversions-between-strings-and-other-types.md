---
title: "字串和其他類型 (Visual Basic) 之間的轉換 |Microsoft 文件"
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
- data type conversion, string
- conversions, type
- string conversion
- conversions, data type
- type conversion, string
- regional options
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
caps.latest.revision: 16
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
ms.openlocfilehash: 34eb32cb6e640d681db6853aaa164d84acca7e4f
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a><span data-ttu-id="bf9d6-102">字串與其他類型之間的轉換 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf9d6-102">Conversions Between Strings and Other Types (Visual Basic)</span></span>
<span data-ttu-id="bf9d6-103">您可以將轉換的數字、 `Boolean`，或日期/時間值`String`。</span><span class="sxs-lookup"><span data-stu-id="bf9d6-103">You can convert a numeric, `Boolean`, or date/time value to a `String`.</span></span> <span data-ttu-id="bf9d6-104">您也可以反向轉換，從字串值為數值， `Boolean`，或`Date`— 提供字串的內容可以解譯為目的地資料類型的有效值。</span><span class="sxs-lookup"><span data-stu-id="bf9d6-104">You can also convert in the reverse direction — from a string value to numeric, `Boolean`, or `Date` — provided the contents of the string can be interpreted as a valid value of the destination data type.</span></span> <span data-ttu-id="bf9d6-105">如果它們不會發生執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="bf9d6-105">If they cannot, a run-time error occurs.</span></span>  
  
 <span data-ttu-id="bf9d6-106">所有這些指派任一方向的轉換會縮小轉換。</span><span class="sxs-lookup"><span data-stu-id="bf9d6-106">The conversions for all these assignments, in either direction, are narrowing conversions.</span></span> <span data-ttu-id="bf9d6-107">You should use the type conversion keywords (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`, and `CType`).</span><span class="sxs-lookup"><span data-stu-id="bf9d6-107">You should use the type conversion keywords (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`, and `CType`).</span></span> <span data-ttu-id="bf9d6-108"><xref:Microsoft.VisualBasic.Strings.Format%2A>和<xref:Microsoft.VisualBasic.Conversion.Val%2A>函式可讓您進一步控制字串和數字之間的轉換。</xref:Microsoft.VisualBasic.Conversion.Val%2A> </xref:Microsoft.VisualBasic.Strings.Format%2A></span><span class="sxs-lookup"><span data-stu-id="bf9d6-108">The <xref:Microsoft.VisualBasic.Strings.Format%2A> and <xref:Microsoft.VisualBasic.Conversion.Val%2A> functions give you additional control over conversions between strings and numbers.</span></span>  
  
 <span data-ttu-id="bf9d6-109">如果您已經定義的類別或結構，您可以定義型別之間的轉換運算子`String`和類別或結構的類型。</span><span class="sxs-lookup"><span data-stu-id="bf9d6-109">If you have defined a class or structure, you can define type conversion operators between `String` and the type of your class or structure.</span></span> <span data-ttu-id="bf9d6-110">如需詳細資訊，請參閱[How to︰ 定義轉換運算子](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="bf9d6-110">For more information, see [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="conversion-of-numbers-to-strings"></a><span data-ttu-id="bf9d6-111">數字轉換為字串</span><span class="sxs-lookup"><span data-stu-id="bf9d6-111">Conversion of Numbers to Strings</span></span>  
 <span data-ttu-id="bf9d6-112">您可以使用`Format`函式，將數字轉換為格式化字串，其中可以包括不僅適當的數字，但也格式符號，例如貨幣符號 (例如`$`)，千位分隔符號或*數字群組符號*(例如`,`)，以及小數分隔符號 (例如`.`)。</span><span class="sxs-lookup"><span data-stu-id="bf9d6-112">You can use the `Format` function to convert a number to a formatted string, which can include not only the appropriate digits but also formatting symbols such as a currency sign (such as `$`), thousands separators or *digit grouping symbols* (such as `,`), and a decimal separator (such as `.`).</span></span> <span data-ttu-id="bf9d6-113">`Format`會自動使用適當的符號，根據**地區選項**Windows 控制台中**控制台**。</span><span class="sxs-lookup"><span data-stu-id="bf9d6-113">`Format` automatically uses the appropriate symbols according to the **Regional Options** settings specified in the Windows **Control Panel**.</span></span>  
  
 <span data-ttu-id="bf9d6-114">請注意，串連 (`&`) 運算子可以將數字轉換成字串以隱含方式，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="bf9d6-114">Note that the concatenation (`&`) operator can convert a number to a string implicitly, as the following example shows.</span></span>  
  
```  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a><span data-ttu-id="bf9d6-115">字串轉換成數字</span><span class="sxs-lookup"><span data-stu-id="bf9d6-115">Conversion of Strings to Numbers</span></span>  
 <span data-ttu-id="bf9d6-116">您可以使用`Val`函式來明確地將字串中的數字轉換為數值。</span><span class="sxs-lookup"><span data-stu-id="bf9d6-116">You can use the `Val` function to explicitly convert the digits in a string to a number.</span></span> <span data-ttu-id="bf9d6-117">`Val`讀取字串，直到遇到數字、 空格、 索引標籤、 換行字元或句號以外的字元。</span><span class="sxs-lookup"><span data-stu-id="bf9d6-117">`Val` reads the string until it encounters a character other than a digit, space, tab, line feed, or period.</span></span> <span data-ttu-id="bf9d6-118">序列 「 i O 」 和 「 i H"改變基底的數字系統，並終止掃描。</span><span class="sxs-lookup"><span data-stu-id="bf9d6-118">The sequences "&O" and "&H" alter the base of the number system and terminate the scanning.</span></span> <span data-ttu-id="bf9d6-119">在停止讀取，`Val`將所有適當的字元轉換為數值。</span><span class="sxs-lookup"><span data-stu-id="bf9d6-119">Until it stops reading, `Val` converts all appropriate characters to a numeric value.</span></span> <span data-ttu-id="bf9d6-120">例如，下列陳述式會傳回值`141.825`。</span><span class="sxs-lookup"><span data-stu-id="bf9d6-120">For example, the following statement returns the value `141.825`.</span></span>  
  
 `Val("   14   1.825 miles")`  
  
 <span data-ttu-id="bf9d6-121">當[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]將轉換的數字值的字串，它會使用**地區選項**Windows 控制台中**控制台**來解譯千分位分隔符號，十進位分隔符號和貨幣符號。</span><span class="sxs-lookup"><span data-stu-id="bf9d6-121">When [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] converts a string to a numeric value, it uses the **Regional Options** settings specified in the Windows **Control Panel** to interpret the thousands separator, decimal separator, and currency symbol.</span></span> <span data-ttu-id="bf9d6-122">這表示，轉換可能成功但不是其他設定一個。</span><span class="sxs-lookup"><span data-stu-id="bf9d6-122">This means that a conversion might succeed under one setting but not another.</span></span> <span data-ttu-id="bf9d6-123">例如，`"$14.20"`是可接受的英文 （美國） 地區設定，但不是在法文地區設定。</span><span class="sxs-lookup"><span data-stu-id="bf9d6-123">For example, `"$14.20"` is acceptable in the English (United States) locale but not in any French locale.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf9d6-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf9d6-124">See Also</span></span>  
 <span data-ttu-id="bf9d6-125">[在 Visual Basic 中的型別轉換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="bf9d6-125">[Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span></span>  
<span data-ttu-id="bf9d6-126"> [擴展和縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="bf9d6-126"> [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) </span></span>  
<span data-ttu-id="bf9d6-127"> [隱含和明確轉換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="bf9d6-127"> [Implicit and Explicit Conversions](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) </span></span>  
<span data-ttu-id="bf9d6-128"> [如何︰ 將物件轉換成 Visual Basic 中的另一個型別](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md) </span><span class="sxs-lookup"><span data-stu-id="bf9d6-128"> [How to: Convert an Object to Another Type in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md) </span></span>  
<span data-ttu-id="bf9d6-129"> [陣列轉換](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="bf9d6-129"> [Array Conversions](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md) </span></span>  
<span data-ttu-id="bf9d6-130"> [資料型別](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="bf9d6-130"> [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="bf9d6-131"> [類型轉換函式](../../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span><span class="sxs-lookup"><span data-stu-id="bf9d6-131"> [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span></span>  
<span data-ttu-id="bf9d6-132"> [以 .NET Framework 為基礎的國際應用程式簡介](https://docs.microsoft.com/visualstudio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)</span><span class="sxs-lookup"><span data-stu-id="bf9d6-132"> [Introduction to International Applications Based on the .NET Framework](https://docs.microsoft.com/visualstudio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)</span></span>

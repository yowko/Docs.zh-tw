---
title: 字串與其他類型之間的轉換 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- data type conversion [Visual Basic], string
- conversions [Visual Basic], type
- string conversion [Visual Basic]
- conversions [Visual Basic], data type
- type conversion [Visual Basic], string
- regional options
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
ms.openlocfilehash: 38acd9056f9517e6d8b62691cdeb1a2960bec800
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "42998706"
---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a><span data-ttu-id="db2d9-102">字串與其他類型之間的轉換 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="db2d9-102">Conversions Between Strings and Other Types (Visual Basic)</span></span>
<span data-ttu-id="db2d9-103">您可以將轉換數字`Boolean`，或日期/時間值`String`。</span><span class="sxs-lookup"><span data-stu-id="db2d9-103">You can convert a numeric, `Boolean`, or date/time value to a `String`.</span></span> <span data-ttu-id="db2d9-104">您也可以反向轉換，從數值字串值`Boolean`，或`Date`— 提供字串的內容可以解譯為有效的值的目的地資料類型。</span><span class="sxs-lookup"><span data-stu-id="db2d9-104">You can also convert in the reverse direction — from a string value to numeric, `Boolean`, or `Date` — provided the contents of the string can be interpreted as a valid value of the destination data type.</span></span> <span data-ttu-id="db2d9-105">如果它們無法在執行階段錯誤發生。</span><span class="sxs-lookup"><span data-stu-id="db2d9-105">If they cannot, a run-time error occurs.</span></span>  
  
 <span data-ttu-id="db2d9-106">所有這些指派，任一方向的轉換縮小轉換。</span><span class="sxs-lookup"><span data-stu-id="db2d9-106">The conversions for all these assignments, in either direction, are narrowing conversions.</span></span> <span data-ttu-id="db2d9-107">您應該使用類型轉換關鍵字 (`CBool`， `CByte`， `CDate`， `CDbl`， `CDec`， `CInt`， `CLng`， `CSByte`， `CShort`， `CSng`， `CStr`，`CUInt`， `CULng`， `CUShort`，和`CType`)。</span><span class="sxs-lookup"><span data-stu-id="db2d9-107">You should use the type conversion keywords (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`, and `CType`).</span></span> <span data-ttu-id="db2d9-108"><xref:Microsoft.VisualBasic.Strings.Format%2A>和<xref:Microsoft.VisualBasic.Conversion.Val%2A>函式可讓您進一步控制字串和數字之間的轉換。</span><span class="sxs-lookup"><span data-stu-id="db2d9-108">The <xref:Microsoft.VisualBasic.Strings.Format%2A> and <xref:Microsoft.VisualBasic.Conversion.Val%2A> functions give you additional control over conversions between strings and numbers.</span></span>  
  
 <span data-ttu-id="db2d9-109">如果您已定義類別或結構，您可以定義之間的型別轉換運算子`String`和您的類別或結構的類型。</span><span class="sxs-lookup"><span data-stu-id="db2d9-109">If you have defined a class or structure, you can define type conversion operators between `String` and the type of your class or structure.</span></span> <span data-ttu-id="db2d9-110">如需詳細資訊，請參閱 <<c0> [ 如何： 定義轉換運算子](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="db2d9-110">For more information, see [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="conversion-of-numbers-to-strings"></a><span data-ttu-id="db2d9-111">數字轉換為字串</span><span class="sxs-lookup"><span data-stu-id="db2d9-111">Conversion of Numbers to Strings</span></span>  
 <span data-ttu-id="db2d9-112">您可以使用`Format`函式，將數字轉換為格式化的字串，其中可以包括不僅適當的數字，但也格式化符號，例如貨幣符號 (例如`$`)，千分位分隔符號或*數字分位符號*(例如`,`)，以及小數分隔符號 (例如`.`)。</span><span class="sxs-lookup"><span data-stu-id="db2d9-112">You can use the `Format` function to convert a number to a formatted string, which can include not only the appropriate digits but also formatting symbols such as a currency sign (such as `$`), thousands separators or *digit grouping symbols* (such as `,`), and a decimal separator (such as `.`).</span></span> <span data-ttu-id="db2d9-113">`Format` 會自動使用適當的符號，根據**地區選項**Windows 控制台中**控制台**。</span><span class="sxs-lookup"><span data-stu-id="db2d9-113">`Format` automatically uses the appropriate symbols according to the **Regional Options** settings specified in the Windows **Control Panel**.</span></span>  
  
 <span data-ttu-id="db2d9-114">請注意，串連 (`&`) 運算子可以將數字轉換成字串以隱含方式，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="db2d9-114">Note that the concatenation (`&`) operator can convert a number to a string implicitly, as the following example shows.</span></span>  
  
```  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a><span data-ttu-id="db2d9-115">字串轉換成數字</span><span class="sxs-lookup"><span data-stu-id="db2d9-115">Conversion of Strings to Numbers</span></span>  
 <span data-ttu-id="db2d9-116">您可以使用`Val`函式來明確地轉換為數字的字串中的數字。</span><span class="sxs-lookup"><span data-stu-id="db2d9-116">You can use the `Val` function to explicitly convert the digits in a string to a number.</span></span> <span data-ttu-id="db2d9-117">`Val` 讀取的字串，直到遇到數字、 空格、 索引標籤、 換行字元或句號以外的字元。</span><span class="sxs-lookup"><span data-stu-id="db2d9-117">`Val` reads the string until it encounters a character other than a digit, space, tab, line feed, or period.</span></span> <span data-ttu-id="db2d9-118">序列"& O"和"& H"alter 基底的數字系統，並終止掃描。</span><span class="sxs-lookup"><span data-stu-id="db2d9-118">The sequences "&O" and "&H" alter the base of the number system and terminate the scanning.</span></span> <span data-ttu-id="db2d9-119">它會停止讀取，直到`Val`將所有適當的字元轉換為數值。</span><span class="sxs-lookup"><span data-stu-id="db2d9-119">Until it stops reading, `Val` converts all appropriate characters to a numeric value.</span></span> <span data-ttu-id="db2d9-120">例如，下列陳述式會傳回值`141.825`。</span><span class="sxs-lookup"><span data-stu-id="db2d9-120">For example, the following statement returns the value `141.825`.</span></span>  
  
 `Val("   14   1.825 miles")`  
  
 <span data-ttu-id="db2d9-121">當 Visual Basic 會將字串轉換為數字值時，它會使用**地區選項**指定在 Windows 中設定**控制台**解譯千分位分隔符號，十進位分隔符號，並貨幣符號。</span><span class="sxs-lookup"><span data-stu-id="db2d9-121">When Visual Basic converts a string to a numeric value, it uses the **Regional Options** settings specified in the Windows **Control Panel** to interpret the thousands separator, decimal separator, and currency symbol.</span></span> <span data-ttu-id="db2d9-122">這表示，轉換可能成功下其中一個設定。</span><span class="sxs-lookup"><span data-stu-id="db2d9-122">This means that a conversion might succeed under one setting but not another.</span></span> <span data-ttu-id="db2d9-123">比方說，`"$14.20"`是可接受在英文 （美國） 地區設定，但不是在法文地區設定。</span><span class="sxs-lookup"><span data-stu-id="db2d9-123">For example, `"$14.20"` is acceptable in the English (United States) locale but not in any French locale.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db2d9-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db2d9-124">See Also</span></span>  
 [<span data-ttu-id="db2d9-125">在 Visual Basic 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="db2d9-125">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="db2d9-126">擴展和縮小轉換</span><span class="sxs-lookup"><span data-stu-id="db2d9-126">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="db2d9-127">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="db2d9-127">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="db2d9-128">如何： 將物件轉換成 Visual Basic 中的另一個類型</span><span class="sxs-lookup"><span data-stu-id="db2d9-128">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [<span data-ttu-id="db2d9-129">陣列轉換</span><span class="sxs-lookup"><span data-stu-id="db2d9-129">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 [<span data-ttu-id="db2d9-130">資料類型</span><span class="sxs-lookup"><span data-stu-id="db2d9-130">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="db2d9-131">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="db2d9-131">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="db2d9-132">以 .NET Framework 為基礎的國際應用程式簡介</span><span class="sxs-lookup"><span data-stu-id="db2d9-132">Introduction to International Applications Based on the .NET Framework</span></span>](/visualstudio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)

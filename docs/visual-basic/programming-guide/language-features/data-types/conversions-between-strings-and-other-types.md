---
title: 字串與其他類型之間的轉換
ms.date: 07/20/2015
helpviewer_keywords:
- data type conversion [Visual Basic], string
- conversions [Visual Basic], type
- string conversion [Visual Basic]
- conversions [Visual Basic], data type
- type conversion [Visual Basic], string
- regional options
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
ms.openlocfilehash: 823931f7d6beb8218e8b99d4a8d45716b7214304
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077146"
---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a><span data-ttu-id="764e5-102">字串與其他類型之間的轉換 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="764e5-102">Conversions Between Strings and Other Types (Visual Basic)</span></span>

<span data-ttu-id="764e5-103">您可以將數值、 `Boolean` 或日期/時間值轉換成 `String` 。</span><span class="sxs-lookup"><span data-stu-id="764e5-103">You can convert a numeric, `Boolean`, or date/time value to a `String`.</span></span> <span data-ttu-id="764e5-104">您也可以反向轉換（從字串值到數值、 `Boolean` 或 `Date` ），前提是字串的內容可以解讀為目的地資料類型的有效值。</span><span class="sxs-lookup"><span data-stu-id="764e5-104">You can also convert in the reverse direction — from a string value to numeric, `Boolean`, or `Date` — provided the contents of the string can be interpreted as a valid value of the destination data type.</span></span> <span data-ttu-id="764e5-105">如果不是，就會發生執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="764e5-105">If they cannot, a run-time error occurs.</span></span>  
  
 <span data-ttu-id="764e5-106">上述所有指派的轉換都是縮小轉換。</span><span class="sxs-lookup"><span data-stu-id="764e5-106">The conversions for all these assignments, in either direction, are narrowing conversions.</span></span> <span data-ttu-id="764e5-107">您應該使用類型轉換關鍵字 (、、、、、、、、、、、、、 `CBool` `CByte` `CDate` `CDbl` `CDec` `CInt` `CLng` `CSByte` `CShort` `CSng` `CStr` `CUInt` `CULng` `CUShort` 和 `CType`) 。</span><span class="sxs-lookup"><span data-stu-id="764e5-107">You should use the type conversion keywords (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`, and `CType`).</span></span> <span data-ttu-id="764e5-108">和函式 <xref:Microsoft.VisualBasic.Strings.Format%2A> <xref:Microsoft.VisualBasic.Conversion.Val%2A> 可讓您進一步控制字元串與數位之間的轉換。</span><span class="sxs-lookup"><span data-stu-id="764e5-108">The <xref:Microsoft.VisualBasic.Strings.Format%2A> and <xref:Microsoft.VisualBasic.Conversion.Val%2A> functions give you additional control over conversions between strings and numbers.</span></span>  
  
 <span data-ttu-id="764e5-109">如果您已定義類別或結構，則可以在 `String` 和類別或結構的類型之間定義型別轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="764e5-109">If you have defined a class or structure, you can define type conversion operators between `String` and the type of your class or structure.</span></span> <span data-ttu-id="764e5-110">如需詳細資訊，請參閱 [How to: Define a Conversion Operator](../procedures/how-to-define-a-conversion-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="764e5-110">For more information, see [How to: Define a Conversion Operator](../procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="conversion-of-numbers-to-strings"></a><span data-ttu-id="764e5-111">將數位轉換成字串</span><span class="sxs-lookup"><span data-stu-id="764e5-111">Conversion of Numbers to Strings</span></span>  

 <span data-ttu-id="764e5-112">您可以使用函式 `Format` ，將數位轉換成格式化的字串，其中不僅可以包含適當的數位，還可以將符號格式化，例如貨幣符號 (例如 `$`) 、千位分隔符號或 *數位群組符號* (例如 `,`) 和小數分隔符號 (例如 `.`) 。</span><span class="sxs-lookup"><span data-stu-id="764e5-112">You can use the `Format` function to convert a number to a formatted string, which can include not only the appropriate digits but also formatting symbols such as a currency sign (such as `$`), thousands separators or *digit grouping symbols* (such as `,`), and a decimal separator (such as `.`).</span></span> <span data-ttu-id="764e5-113">`Format`會根據 Windows**主控台**中指定的**地區選項**設定，自動使用適當的符號。</span><span class="sxs-lookup"><span data-stu-id="764e5-113">`Format` automatically uses the appropriate symbols according to the **Regional Options** settings specified in the Windows **Control Panel**.</span></span>  
  
 <span data-ttu-id="764e5-114">請注意，串連 (`&`) 運算子可以隱含地將數位轉換成字串，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="764e5-114">Note that the concatenation (`&`) operator can convert a number to a string implicitly, as the following example shows.</span></span>  
  
```vb  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a><span data-ttu-id="764e5-115">將字串轉換為數字</span><span class="sxs-lookup"><span data-stu-id="764e5-115">Conversion of Strings to Numbers</span></span>  

 <span data-ttu-id="764e5-116">您可以使用 `Val` 函數，將字串中的數位明確轉換為數字。</span><span class="sxs-lookup"><span data-stu-id="764e5-116">You can use the `Val` function to explicitly convert the digits in a string to a number.</span></span> <span data-ttu-id="764e5-117">`Val` 讀取字串，直到它遇到數位、空格、定位字元、換行字元或句號以外的字元為止。</span><span class="sxs-lookup"><span data-stu-id="764e5-117">`Val` reads the string until it encounters a character other than a digit, space, tab, line feed, or period.</span></span> <span data-ttu-id="764e5-118">序列 "&O" 和 "&H" 改變數字系統的基底，並結束掃描。</span><span class="sxs-lookup"><span data-stu-id="764e5-118">The sequences "&O" and "&H" alter the base of the number system and terminate the scanning.</span></span> <span data-ttu-id="764e5-119">在停止讀取之前，會 `Val` 將所有適當的字元轉換成數值。</span><span class="sxs-lookup"><span data-stu-id="764e5-119">Until it stops reading, `Val` converts all appropriate characters to a numeric value.</span></span> <span data-ttu-id="764e5-120">例如，下列語句會傳回值 `141.825` 。</span><span class="sxs-lookup"><span data-stu-id="764e5-120">For example, the following statement returns the value `141.825`.</span></span>  
  
 `Val("   14   1.825 miles")`  
  
 <span data-ttu-id="764e5-121">當 Visual Basic 將字串轉換成數值時，它會使用 Windows**主控台**中指定的**地區選項**設定來解讀千位分隔符號、小數分隔符號和貨幣符號。</span><span class="sxs-lookup"><span data-stu-id="764e5-121">When Visual Basic converts a string to a numeric value, it uses the **Regional Options** settings specified in the Windows **Control Panel** to interpret the thousands separator, decimal separator, and currency symbol.</span></span> <span data-ttu-id="764e5-122">這表示轉換可能會在某個設定下成功，但不能在另一個設定下成功。</span><span class="sxs-lookup"><span data-stu-id="764e5-122">This means that a conversion might succeed under one setting but not another.</span></span> <span data-ttu-id="764e5-123">例如， `"$14.20"` 英文 (美國) 地區設定可接受，但在任何法文地區設定中則不接受。</span><span class="sxs-lookup"><span data-stu-id="764e5-123">For example, `"$14.20"` is acceptable in the English (United States) locale but not in any French locale.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="764e5-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="764e5-124">See also</span></span>

- [<span data-ttu-id="764e5-125">Visual Basic 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="764e5-125">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="764e5-126">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="764e5-126">Widening and Narrowing Conversions</span></span>](widening-and-narrowing-conversions.md)
- [<span data-ttu-id="764e5-127">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="764e5-127">Implicit and Explicit Conversions</span></span>](implicit-and-explicit-conversions.md)
- [<span data-ttu-id="764e5-128">如何：在 Visual Basic 中將物件轉換成其他類型</span><span class="sxs-lookup"><span data-stu-id="764e5-128">How to: Convert an Object to Another Type in Visual Basic</span></span>](how-to-convert-an-object-to-another-type.md)
- [<span data-ttu-id="764e5-129">陣列轉換</span><span class="sxs-lookup"><span data-stu-id="764e5-129">Array Conversions</span></span>](array-conversions.md)
- [<span data-ttu-id="764e5-130">Data types (資料類型)</span><span class="sxs-lookup"><span data-stu-id="764e5-130">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="764e5-131">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="764e5-131">Type Conversion Functions</span></span>](../../../language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="764e5-132">開發全球化和當地語系化應用程式</span><span class="sxs-lookup"><span data-stu-id="764e5-132">Develop globalized and localized apps</span></span>](/visualstudio/ide/globalizing-and-localizing-applications)

---
title: Char 資料類型 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Char
helpviewer_keywords:
- literal type characters [Visual Basic], C
- Char data type
- C literal type character [Visual Basic]
- data types [Visual Basic], assigning
- Char data type [Visual Basic], character literals
ms.assetid: cd7547a9-7855-4e8e-b216-35d74a362657
ms.openlocfilehash: ca40e6c8dcba3da29bdb68b29c91c852e477f8f7
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512783"
---
# <a name="char-data-type-visual-basic"></a><span data-ttu-id="d2d6b-102">Char 資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2d6b-102">Char Data Type (Visual Basic)</span></span>

<span data-ttu-id="d2d6b-103">保留不帶正負號的16位 (2 位元組) 程式碼點, 範圍介於0到65535之間。</span><span class="sxs-lookup"><span data-stu-id="d2d6b-103">Holds unsigned 16-bit (2-byte) code points ranging in value from 0 through 65535.</span></span> <span data-ttu-id="d2d6b-104">每個程式*代碼點*或字元碼都代表一個 Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="d2d6b-104">Each *code point*, or character code, represents a single Unicode character.</span></span>

## <a name="remarks"></a><span data-ttu-id="d2d6b-105">備註</span><span class="sxs-lookup"><span data-stu-id="d2d6b-105">Remarks</span></span>

<span data-ttu-id="d2d6b-106">當您只需要保存單一字元, 而且不需要的`String`額外負荷時, 請使用資料類型。`Char`</span><span class="sxs-lookup"><span data-stu-id="d2d6b-106">Use the `Char` data type when you need to hold only a single character and do not need the overhead of `String`.</span></span> <span data-ttu-id="d2d6b-107">在某些情況下, 您`Char()`可以使用`Char`元素陣列來保存多個字元。</span><span class="sxs-lookup"><span data-stu-id="d2d6b-107">In some cases you can use `Char()`, an array of `Char` elements, to hold multiple characters.</span></span>

<span data-ttu-id="d2d6b-108">的預設值`Char`是程式碼點為0的字元。</span><span class="sxs-lookup"><span data-stu-id="d2d6b-108">The default value of `Char` is the character with a code point of 0.</span></span>

## <a name="unicode-characters"></a><span data-ttu-id="d2d6b-109">Unicode 字元</span><span class="sxs-lookup"><span data-stu-id="d2d6b-109">Unicode Characters</span></span>

<span data-ttu-id="d2d6b-110">Unicode 的第一個128程式碼點 (0 – 127) 對應到標準美式鍵盤上的字母和符號。</span><span class="sxs-lookup"><span data-stu-id="d2d6b-110">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="d2d6b-111">這些前128個程式碼點與 ASCII 字元集所定義的相同。</span><span class="sxs-lookup"><span data-stu-id="d2d6b-111">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="d2d6b-112">第二個128程式碼片段 (128 – 255) 代表特殊字元, 例如以拉丁為基礎的字母、重音、貨幣符號和分數。</span><span class="sxs-lookup"><span data-stu-id="d2d6b-112">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="d2d6b-113">Unicode 會針對各種不同的符號使用其餘的程式碼點 (256-65535), 包括全球文字字元、變音符號和數學和技術符號。</span><span class="sxs-lookup"><span data-stu-id="d2d6b-113">Unicode uses the remaining code points (256-65535) for a wide variety of symbols, including worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>

<span data-ttu-id="d2d6b-114">您可以在<xref:System.Char.IsDigit%2A> `Char`變數上使用<xref:System.Char.IsPunctuation%2A>和之類的方法來判斷其 Unicode 分類。</span><span class="sxs-lookup"><span data-stu-id="d2d6b-114">You can use methods like <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on a `Char` variable to determine its Unicode classification.</span></span>

## <a name="type-conversions"></a><span data-ttu-id="d2d6b-115">類型轉換</span><span class="sxs-lookup"><span data-stu-id="d2d6b-115">Type Conversions</span></span>

<span data-ttu-id="d2d6b-116">Visual Basic 不會直接在和`Char`數數值型別之間進行轉換。</span><span class="sxs-lookup"><span data-stu-id="d2d6b-116">Visual Basic does not convert directly between `Char` and the numeric types.</span></span> <span data-ttu-id="d2d6b-117">您可以使用<xref:Microsoft.VisualBasic.Strings.Asc%2A>或<xref:Microsoft.VisualBasic.Strings.AscW%2A>函`Char` 式`Integer` , 將值轉換為代表其程式碼點的。</span><span class="sxs-lookup"><span data-stu-id="d2d6b-117">You can use the <xref:Microsoft.VisualBasic.Strings.Asc%2A> or <xref:Microsoft.VisualBasic.Strings.AscW%2A> function to convert a `Char` value to an `Integer` that represents its code point.</span></span> <span data-ttu-id="d2d6b-118">您可以使用<xref:Microsoft.VisualBasic.Strings.Chr%2A>或<xref:Microsoft.VisualBasic.Strings.ChrW%2A>函數`Integer` ,`Char`將值轉換成具有該程式碼點的。</span><span class="sxs-lookup"><span data-stu-id="d2d6b-118">You can use the <xref:Microsoft.VisualBasic.Strings.Chr%2A> or <xref:Microsoft.VisualBasic.Strings.ChrW%2A> function to convert an `Integer` value to a `Char` that has that code point.</span></span>

<span data-ttu-id="d2d6b-119">如果類型檢查參數 ([Option Strict 語句](../../../visual-basic/language-reference/statements/option-strict-statement.md)) 是 on, 您就必須將常數值型別字元附加至單一字元字串常值, 以將它識別`Char`為資料類型。</span><span class="sxs-lookup"><span data-stu-id="d2d6b-119">If the type checking switch ([Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)) is on, you must append the literal type character to a single-character string literal to identify it as the `Char` data type.</span></span> <span data-ttu-id="d2d6b-120">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="d2d6b-120">The following example illustrates this.</span></span>

```vb
Option Strict On
Dim charVar As Char
' The following statement attempts to convert a String literal to Char.
' Because Option Strict is On, it generates a compiler error.
charVar = "Z"
' The following statement succeeds because it specifies a Char literal.
charVar = "Z"C
```

## <a name="programming-tips"></a><span data-ttu-id="d2d6b-121">程式設計提示</span><span class="sxs-lookup"><span data-stu-id="d2d6b-121">Programming Tips</span></span>

- <span data-ttu-id="d2d6b-122">**負數。**</span><span class="sxs-lookup"><span data-stu-id="d2d6b-122">**Negative Numbers.**</span></span> <span data-ttu-id="d2d6b-123">`Char`是不帶正負號的類型, 而且不能代表負值。</span><span class="sxs-lookup"><span data-stu-id="d2d6b-123">`Char` is an unsigned type and cannot represent a negative value.</span></span> <span data-ttu-id="d2d6b-124">在任何情況下, 您都不`Char`應該使用來保存數值。</span><span class="sxs-lookup"><span data-stu-id="d2d6b-124">In any case, you should not use `Char` to hold numeric values.</span></span>

- <span data-ttu-id="d2d6b-125">**Interop 考慮。**</span><span class="sxs-lookup"><span data-stu-id="d2d6b-125">**Interop Considerations.**</span></span> <span data-ttu-id="d2d6b-126">如果您使用不是針對 .NET Framework 所撰寫的元件 (例如 Automation 或 COM 物件) 來進行介面, 請記住, 在其他環境中, 字元類型具有不同的資料寬度 (8 位)。</span><span class="sxs-lookup"><span data-stu-id="d2d6b-126">If you interface with components not written for the .NET Framework, for example Automation or COM objects, remember that character types have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="d2d6b-127">如果您將8位引數傳遞至這類元件, 請在新`Byte`的`Char` Visual Basic 程式碼中將它宣告為而不是。</span><span class="sxs-lookup"><span data-stu-id="d2d6b-127">If you pass an 8-bit argument to such a component, declare it as `Byte` instead of `Char` in your new Visual Basic code.</span></span>

- <span data-ttu-id="d2d6b-128">**加寬.**</span><span class="sxs-lookup"><span data-stu-id="d2d6b-128">**Widening.**</span></span> <span data-ttu-id="d2d6b-129">資料類型會擴大為`String`。 `Char`</span><span class="sxs-lookup"><span data-stu-id="d2d6b-129">The `Char` data type widens to `String`.</span></span> <span data-ttu-id="d2d6b-130">這表示您可以將`Char`轉換`String`成<xref:System.OverflowException?displayProperty=nameWithType> , 而且不會遇到錯誤。</span><span class="sxs-lookup"><span data-stu-id="d2d6b-130">This means you can convert `Char` to `String` and will not encounter a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="d2d6b-131">**輸入字元。**</span><span class="sxs-lookup"><span data-stu-id="d2d6b-131">**Type Characters.**</span></span> <span data-ttu-id="d2d6b-132">將常數值型別字元`C`附加至單一字元字串常值, 會強制其`Char`成為資料類型。</span><span class="sxs-lookup"><span data-stu-id="d2d6b-132">Appending the literal type character `C` to a single-character string literal forces it to the `Char` data type.</span></span> <span data-ttu-id="d2d6b-133">`Char`沒有識別項型別字元。</span><span class="sxs-lookup"><span data-stu-id="d2d6b-133">`Char` has no identifier type character.</span></span>

- <span data-ttu-id="d2d6b-134">**架構類型。**</span><span class="sxs-lookup"><span data-stu-id="d2d6b-134">**Framework Type.**</span></span> <span data-ttu-id="d2d6b-135">在 .NET Framework 中對應的類型為 <xref:System.Char?displayProperty=nameWithType> 結構。</span><span class="sxs-lookup"><span data-stu-id="d2d6b-135">The corresponding type in the .NET Framework is the <xref:System.Char?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="d2d6b-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2d6b-136">See also</span></span>

- <xref:System.Char?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [<span data-ttu-id="d2d6b-137">資料類型</span><span class="sxs-lookup"><span data-stu-id="d2d6b-137">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="d2d6b-138">String 資料類型</span><span class="sxs-lookup"><span data-stu-id="d2d6b-138">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)
- [<span data-ttu-id="d2d6b-139">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="d2d6b-139">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="d2d6b-140">轉換摘要</span><span class="sxs-lookup"><span data-stu-id="d2d6b-140">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="d2d6b-141">如何：呼叫使用不帶正負號類型的 Windows 函式</span><span class="sxs-lookup"><span data-stu-id="d2d6b-141">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="d2d6b-142">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="d2d6b-142">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

---
title: Byte 資料類型
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
ms.openlocfilehash: 97acd1bc2ff29bac6588216b9ee4a4f187078815
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374313"
---
# <a name="byte-data-type-visual-basic"></a><span data-ttu-id="467bb-102">Byte 資料類型（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="467bb-102">Byte data type (Visual Basic)</span></span>

<span data-ttu-id="467bb-103">保存不帶正負號的8位（1個位元組）整數，其值介於0到255之間。</span><span class="sxs-lookup"><span data-stu-id="467bb-103">Holds unsigned 8-bit (1-byte) integers that range in value from 0 through 255.</span></span>

## <a name="remarks"></a><span data-ttu-id="467bb-104">備註</span><span class="sxs-lookup"><span data-stu-id="467bb-104">Remarks</span></span>

<span data-ttu-id="467bb-105">使用 `Byte` 資料類型來包含二進位資料。</span><span class="sxs-lookup"><span data-stu-id="467bb-105">Use the `Byte` data type to contain binary data.</span></span>  
  
<span data-ttu-id="467bb-106">`Byte` 的預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="467bb-106">The default value of `Byte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="467bb-107">常值指派</span><span class="sxs-lookup"><span data-stu-id="467bb-107">Literal assignments</span></span>

<span data-ttu-id="467bb-108">您可以藉 `Byte` 由指派十進位常值、十六進位常值、八進位常值，或二進位常值（從 Visual Basic 2017）來宣告和初始化變數。</span><span class="sxs-lookup"><span data-stu-id="467bb-108">You can declare and initialize a `Byte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="467bb-109">如果整數常值超出的範圍 `Byte` （亦即，如果小於 <xref:System.Byte.MinValue?displayProperty=nameWithType> 或大於 <xref:System.Byte.MaxValue?displayProperty=nameWithType> ），就會發生編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="467bb-109">If the integral literal is outside the range of a `Byte` (that is, if it is less than <xref:System.Byte.MinValue?displayProperty=nameWithType> or greater than <xref:System.Byte.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="467bb-110">在下列範例中，等於201的整數（以十進位、十六進位和二進位常值表示）會從[整數](integer-data-type.md)隱含地轉換為 `byte` 值。</span><span class="sxs-lookup"><span data-stu-id="467bb-110">In the following example, integers equal to 201 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `byte` values.</span></span>

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> <span data-ttu-id="467bb-111">您可以使用前置詞 `&h` 或 `&H` 來表示十六進位常值、前置詞 `&b` 或表示 `&B` 二進位常值，以及前置詞 `&o` 或 `&O` 來表示八進位常值。</span><span class="sxs-lookup"><span data-stu-id="467bb-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="467bb-112">十進位常值沒有前置詞。</span><span class="sxs-lookup"><span data-stu-id="467bb-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="467bb-113">從 Visual Basic 2017 開始，您也可以使用底線字元 `_` 做為數位分隔符號來增強可讀性，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="467bb-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

<span data-ttu-id="467bb-114">從 Visual Basic 15.5 開始，您也可以使用底線字元（ `_` ）做為前置詞和十六進位、二進位或八進位數位之間的前置分隔符號。</span><span class="sxs-lookup"><span data-stu-id="467bb-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="467bb-115">例如：</span><span class="sxs-lookup"><span data-stu-id="467bb-115">For example:</span></span>

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a><span data-ttu-id="467bb-116">程式設計提示</span><span class="sxs-lookup"><span data-stu-id="467bb-116">Programming tips</span></span>

- <span data-ttu-id="467bb-117">**負數。**</span><span class="sxs-lookup"><span data-stu-id="467bb-117">**Negative Numbers.**</span></span> <span data-ttu-id="467bb-118">因為 `Byte` 是不帶正負號的類型，所以不能代表負數。</span><span class="sxs-lookup"><span data-stu-id="467bb-118">Because `Byte` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="467bb-119">如果您 `-` 在評估為類型的運算式上使用一元減號（）運算子 `Byte` ，Visual Basic 會將運算式轉換為 `Short` first。</span><span class="sxs-lookup"><span data-stu-id="467bb-119">If you use the unary minus (`-`) operator on an expression that evaluates to type `Byte`, Visual Basic converts the expression to `Short` first.</span></span>
  
- <span data-ttu-id="467bb-120">**格式轉換。**</span><span class="sxs-lookup"><span data-stu-id="467bb-120">**Format Conversions.**</span></span> <span data-ttu-id="467bb-121">當 Visual Basic 讀取或寫入檔案時，或當它呼叫 Dll、方法和屬性時，可以在資料格式之間自動轉換。</span><span class="sxs-lookup"><span data-stu-id="467bb-121">When Visual Basic reads or writes files, or when it calls DLLs, methods, and properties, it can automatically convert between data formats.</span></span> <span data-ttu-id="467bb-122">儲存在變數和陣列中的二進位資料 `Byte` 會在這類格式轉換期間保留。</span><span class="sxs-lookup"><span data-stu-id="467bb-122">Binary data stored in `Byte` variables and arrays is preserved during such format conversions.</span></span> <span data-ttu-id="467bb-123">您不應該將 `String` 變數用於二進位資料，因為在 ANSI 和 Unicode 格式之間轉換時，其內容可能會損毀。</span><span class="sxs-lookup"><span data-stu-id="467bb-123">You should not use a `String` variable for binary data, because its contents can be corrupted during conversion between ANSI and Unicode formats.</span></span>

- <span data-ttu-id="467bb-124">**加寬.**</span><span class="sxs-lookup"><span data-stu-id="467bb-124">**Widening.**</span></span> <span data-ttu-id="467bb-125">`Byte`資料類型會擴大為 `Short` 、 `UShort` 、 `Integer` 、 `UInteger` 、 `Long` 、、、 `ULong` `Decimal` `Single` 或 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="467bb-125">The `Byte` data type widens to `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="467bb-126">這表示您可以轉換 `Byte` 成這些類型的任何一種，而不會遇到 <xref:System.OverflowException?displayProperty=nameWithType> 錯誤。</span><span class="sxs-lookup"><span data-stu-id="467bb-126">This means you can convert `Byte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>
  
- <span data-ttu-id="467bb-127">**輸入字元。**</span><span class="sxs-lookup"><span data-stu-id="467bb-127">**Type Characters.**</span></span> <span data-ttu-id="467bb-128">`Byte`沒有常數值型別字元或識別項型別字元。</span><span class="sxs-lookup"><span data-stu-id="467bb-128">`Byte` has no literal type character or identifier type character.</span></span>

- <span data-ttu-id="467bb-129">**架構類型：**</span><span class="sxs-lookup"><span data-stu-id="467bb-129">**Framework Type.**</span></span> <span data-ttu-id="467bb-130">在 .NET Framework 中對應的類型為 <xref:System.Byte?displayProperty=nameWithType> 結構。</span><span class="sxs-lookup"><span data-stu-id="467bb-130">The corresponding type in the .NET Framework is the <xref:System.Byte?displayProperty=nameWithType> structure.</span></span>

## <a name="example"></a><span data-ttu-id="467bb-131">範例</span><span class="sxs-lookup"><span data-stu-id="467bb-131">Example</span></span>

 <span data-ttu-id="467bb-132">在下列範例中， `b` 是一個 `Byte` 變數。</span><span class="sxs-lookup"><span data-stu-id="467bb-132">In the following example, `b` is a `Byte` variable.</span></span> <span data-ttu-id="467bb-133">語句會示範變數的範圍，以及對其進行位移位運算子的應用。</span><span class="sxs-lookup"><span data-stu-id="467bb-133">The statements demonstrate the range of the variable and the application of bit-shift operators to it.</span></span>

 [!code-vb[VbVbalrDataTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#16)]  

## <a name="see-also"></a><span data-ttu-id="467bb-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="467bb-134">See also</span></span>

- <xref:System.Byte?displayProperty=nameWithType>
- [<span data-ttu-id="467bb-135">資料類型</span><span class="sxs-lookup"><span data-stu-id="467bb-135">Data Types</span></span>](index.md)
- [<span data-ttu-id="467bb-136">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="467bb-136">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="467bb-137">轉換摘要</span><span class="sxs-lookup"><span data-stu-id="467bb-137">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="467bb-138">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="467bb-138">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)

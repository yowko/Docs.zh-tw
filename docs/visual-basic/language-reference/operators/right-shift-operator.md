---
title: '>> 運算子'
ms.date: 07/20/2015
f1_keywords:
- vb.>>
helpviewer_keywords:
- operator>>
- '>> operator [Visual Basic]'
- bit shift operators [Visual Basic]
- operator >>
- right shift operators [Visual Basic]
ms.assetid: 054dc6a6-47d9-47ef-82da-cfa2b59fbf8f
ms.openlocfilehash: 00f43bc9bae6d550ed175906777ac273fc8e9a23
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873338"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="b5b10-102">>> 運算子 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="b5b10-102">>> Operator (Visual Basic)</span></span>

<span data-ttu-id="b5b10-103">在位模式上執行算術右移位。</span><span class="sxs-lookup"><span data-stu-id="b5b10-103">Performs an arithmetic right shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5b10-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="b5b10-104">Syntax</span></span>  
  
```vb  
result = pattern >> amount  
```  
  
## <a name="parts"></a><span data-ttu-id="b5b10-105">組件</span><span class="sxs-lookup"><span data-stu-id="b5b10-105">Parts</span></span>  

 `result`  
 <span data-ttu-id="b5b10-106">必要。</span><span class="sxs-lookup"><span data-stu-id="b5b10-106">Required.</span></span> <span data-ttu-id="b5b10-107">整數數值。</span><span class="sxs-lookup"><span data-stu-id="b5b10-107">Integral numeric value.</span></span> <span data-ttu-id="b5b10-108">位元模式移位的結果。</span><span class="sxs-lookup"><span data-stu-id="b5b10-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="b5b10-109">資料型別與 `pattern` 的型別相同。</span><span class="sxs-lookup"><span data-stu-id="b5b10-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="b5b10-110">必要。</span><span class="sxs-lookup"><span data-stu-id="b5b10-110">Required.</span></span> <span data-ttu-id="b5b10-111">整數值運算式。</span><span class="sxs-lookup"><span data-stu-id="b5b10-111">Integral numeric expression.</span></span> <span data-ttu-id="b5b10-112">要移位的位元模式。</span><span class="sxs-lookup"><span data-stu-id="b5b10-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="b5b10-113">資料型別必須是整數類資料型別 (Integral Type) (`SByte`、`Byte`、`Short`、`UShort`、`Integer`、`UInteger`、`Long` 或 `ULong`)。</span><span class="sxs-lookup"><span data-stu-id="b5b10-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="b5b10-114">必要。</span><span class="sxs-lookup"><span data-stu-id="b5b10-114">Required.</span></span> <span data-ttu-id="b5b10-115">數值運算式。</span><span class="sxs-lookup"><span data-stu-id="b5b10-115">Numeric expression.</span></span> <span data-ttu-id="b5b10-116">位元模式移位的位元數。</span><span class="sxs-lookup"><span data-stu-id="b5b10-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="b5b10-117">資料型別必須是 `Integer` 或擴展至 `Integer`。</span><span class="sxs-lookup"><span data-stu-id="b5b10-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5b10-118">備註</span><span class="sxs-lookup"><span data-stu-id="b5b10-118">Remarks</span></span>  

 <span data-ttu-id="b5b10-119">算術移位不是迴圈的，這表示不會在另一端重新出現從結果的一端移出的位。</span><span class="sxs-lookup"><span data-stu-id="b5b10-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="b5b10-120">在算術右移位中，會捨棄超出最右邊位位置的位，並將最左邊的 (符號) 位傳播到左側空出的位位置。</span><span class="sxs-lookup"><span data-stu-id="b5b10-120">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost (sign) bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="b5b10-121">這表示，如果的 `pattern` 值為負值，空出的位置會設定為1，否則會設為零。</span><span class="sxs-lookup"><span data-stu-id="b5b10-121">This means that if `pattern` has a negative value, the vacated positions are set to one; otherwise they are set to zero.</span></span>  
  
 <span data-ttu-id="b5b10-122">請注意，資料類型 `Byte` 、 `UShort` 、 `UInteger` 和未 `ULong` 簽署，因此沒有要傳播的符號位。</span><span class="sxs-lookup"><span data-stu-id="b5b10-122">Note that the data types `Byte`, `UShort`, `UInteger`, and `ULong` are unsigned, so there is no sign bit to propagate.</span></span> <span data-ttu-id="b5b10-123">如果 `pattern` 是任何不帶正負號的類型，空出的位置一律會設定為零。</span><span class="sxs-lookup"><span data-stu-id="b5b10-123">If `pattern` is of any unsigned type, the vacated positions are always set to zero.</span></span>  
  
 <span data-ttu-id="b5b10-124">為了防止超過結果所能保存的位數，Visual Basic 會以 `amount` 對應至資料類型的大小遮罩來遮罩的值 `pattern` 。</span><span class="sxs-lookup"><span data-stu-id="b5b10-124">To prevent shifting by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask corresponding to the data type of `pattern`.</span></span> <span data-ttu-id="b5b10-125">這些值的二進位和都是用於移位量。</span><span class="sxs-lookup"><span data-stu-id="b5b10-125">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="b5b10-126">大小遮罩如下所示：</span><span class="sxs-lookup"><span data-stu-id="b5b10-126">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="b5b10-127">的資料類型 `pattern`</span><span class="sxs-lookup"><span data-stu-id="b5b10-127">Data type of `pattern`</span></span>|<span data-ttu-id="b5b10-128">大小遮罩 (decimal) </span><span class="sxs-lookup"><span data-stu-id="b5b10-128">Size mask (decimal)</span></span>|<span data-ttu-id="b5b10-129">大小遮罩 (十六進位) </span><span class="sxs-lookup"><span data-stu-id="b5b10-129">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="b5b10-130">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="b5b10-130">`SByte`, `Byte`</span></span>|<span data-ttu-id="b5b10-131">7</span><span class="sxs-lookup"><span data-stu-id="b5b10-131">7</span></span>|<span data-ttu-id="b5b10-132">&H00000007</span><span class="sxs-lookup"><span data-stu-id="b5b10-132">&H00000007</span></span>|  
|<span data-ttu-id="b5b10-133">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="b5b10-133">`Short`, `UShort`</span></span>|<span data-ttu-id="b5b10-134">15</span><span class="sxs-lookup"><span data-stu-id="b5b10-134">15</span></span>|<span data-ttu-id="b5b10-135">&H0000000F</span><span class="sxs-lookup"><span data-stu-id="b5b10-135">&H0000000F</span></span>|  
|<span data-ttu-id="b5b10-136">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="b5b10-136">`Integer`, `UInteger`</span></span>|<span data-ttu-id="b5b10-137">31</span><span class="sxs-lookup"><span data-stu-id="b5b10-137">31</span></span>|<span data-ttu-id="b5b10-138">&H0000001F</span><span class="sxs-lookup"><span data-stu-id="b5b10-138">&H0000001F</span></span>|  
|<span data-ttu-id="b5b10-139">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="b5b10-139">`Long`, `ULong`</span></span>|<span data-ttu-id="b5b10-140">63</span><span class="sxs-lookup"><span data-stu-id="b5b10-140">63</span></span>|<span data-ttu-id="b5b10-141">&H0000003F</span><span class="sxs-lookup"><span data-stu-id="b5b10-141">&H0000003F</span></span>|  
  
 <span data-ttu-id="b5b10-142">如果 `amount` 是零，的值 `result` 就會與的值相同 `pattern` 。</span><span class="sxs-lookup"><span data-stu-id="b5b10-142">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="b5b10-143">如果 `amount` 是負數，則會被視為不帶正負號的值，並以適當的大小遮罩進行遮罩。</span><span class="sxs-lookup"><span data-stu-id="b5b10-143">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="b5b10-144">算術移位絕不會產生溢位例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b5b10-144">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="b5b10-145">多載化</span><span class="sxs-lookup"><span data-stu-id="b5b10-145">Overloading</span></span>  

 <span data-ttu-id="b5b10-146">可以多載 `>>` 運算子*overloaded*，這表示當運算元具有該類別或結構的型別時，類別或結構可以重新定義其行為。</span><span class="sxs-lookup"><span data-stu-id="b5b10-146">The `>>` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="b5b10-147">如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="b5b10-147">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="b5b10-148">如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="b5b10-148">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5b10-149">範例</span><span class="sxs-lookup"><span data-stu-id="b5b10-149">Example</span></span>  

 <span data-ttu-id="b5b10-150">下列範例會使用 `>>` 運算子，在整數值上執行算術右移位。</span><span class="sxs-lookup"><span data-stu-id="b5b10-150">The following example uses the `>>` operator to perform arithmetic right shifts on integral values.</span></span> <span data-ttu-id="b5b10-151">結果一律具有與要移位的運算式相同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="b5b10-151">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#14)]  
  
 <span data-ttu-id="b5b10-152">上述範例的結果如下所示：</span><span class="sxs-lookup"><span data-stu-id="b5b10-152">The results of the preceding example are as follows:</span></span>  
  
- <span data-ttu-id="b5b10-153">`result1` 為 2560 (0000 1010 0000 0000) 。</span><span class="sxs-lookup"><span data-stu-id="b5b10-153">`result1` is 2560 (0000 1010 0000 0000).</span></span>  
  
- <span data-ttu-id="b5b10-154">`result2` 為 160 (0000 0000 1010 0000) 。</span><span class="sxs-lookup"><span data-stu-id="b5b10-154">`result2` is 160 (0000 0000 1010 0000).</span></span>  
  
- <span data-ttu-id="b5b10-155">`result3` 是 2 (0000 0000 0000 0010) 。</span><span class="sxs-lookup"><span data-stu-id="b5b10-155">`result3` is 2 (0000 0000 0000 0010).</span></span>  
  
- <span data-ttu-id="b5b10-156">`result4` 為 640 (0000 0010 1000 0000) 。</span><span class="sxs-lookup"><span data-stu-id="b5b10-156">`result4` is 640 (0000 0010 1000 0000).</span></span>  
  
- <span data-ttu-id="b5b10-157">`result5` 為 0 (將15個位置向右) 移位。</span><span class="sxs-lookup"><span data-stu-id="b5b10-157">`result5` is 0 (shifted 15 places to the right).</span></span>  
  
 <span data-ttu-id="b5b10-158">的移位數量 `result4` 會計算為18和15，等於2。</span><span class="sxs-lookup"><span data-stu-id="b5b10-158">The shift amount for `result4` is calculated as 18 AND 15, which equals 2.</span></span>  
  
 <span data-ttu-id="b5b10-159">下列範例顯示負數值的算術移位。</span><span class="sxs-lookup"><span data-stu-id="b5b10-159">The following example shows arithmetic shifts on a negative value.</span></span>  
  
 [!code-vb[VbVbalrOperators#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#55)]  
  
 <span data-ttu-id="b5b10-160">上述範例的結果如下所示：</span><span class="sxs-lookup"><span data-stu-id="b5b10-160">The results of the preceding example are as follows:</span></span>  
  
- <span data-ttu-id="b5b10-161">`negresult1` 是-512 (1111 1110 0000 0000) 。</span><span class="sxs-lookup"><span data-stu-id="b5b10-161">`negresult1` is -512 (1111 1110 0000 0000).</span></span>  
  
- <span data-ttu-id="b5b10-162">`negresult2` 為-1 (會將符號位傳播) 。</span><span class="sxs-lookup"><span data-stu-id="b5b10-162">`negresult2` is -1 (the sign bit is propagated).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5b10-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b5b10-163">See also</span></span>

- [<span data-ttu-id="b5b10-164">位元移位運算子</span><span class="sxs-lookup"><span data-stu-id="b5b10-164">Bit Shift Operators</span></span>](bit-shift-operators.md)
- [<span data-ttu-id="b5b10-165">指派運算子</span><span class="sxs-lookup"><span data-stu-id="b5b10-165">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="b5b10-166">>>= 運算子</span><span class="sxs-lookup"><span data-stu-id="b5b10-166">>>= Operator</span></span>](right-shift-assignment-operator.md)
- [<span data-ttu-id="b5b10-167">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="b5b10-167">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="b5b10-168">依功能列出運算子</span><span class="sxs-lookup"><span data-stu-id="b5b10-168">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="b5b10-169">Visual Basic 的算術運算子</span><span class="sxs-lookup"><span data-stu-id="b5b10-169">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)

---
title: << 運算子
ms.date: 07/20/2015
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
ms.openlocfilehash: 77bf26d4e6bb068f9130deed5eb1ecbaee62afce
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866786"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="e5111-102">\<\< 運算子 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="e5111-102">\<\< Operator (Visual Basic)</span></span>

<span data-ttu-id="e5111-103">在位模式上執行算術左移位。</span><span class="sxs-lookup"><span data-stu-id="e5111-103">Performs an arithmetic left shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5111-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="e5111-104">Syntax</span></span>  
  
```vb  
result = pattern << amount  
```  
  
## <a name="parts"></a><span data-ttu-id="e5111-105">組件</span><span class="sxs-lookup"><span data-stu-id="e5111-105">Parts</span></span>  

 `result`  
 <span data-ttu-id="e5111-106">必要。</span><span class="sxs-lookup"><span data-stu-id="e5111-106">Required.</span></span> <span data-ttu-id="e5111-107">整數數值。</span><span class="sxs-lookup"><span data-stu-id="e5111-107">Integral numeric value.</span></span> <span data-ttu-id="e5111-108">位元模式移位的結果。</span><span class="sxs-lookup"><span data-stu-id="e5111-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="e5111-109">資料型別與 `pattern` 的型別相同。</span><span class="sxs-lookup"><span data-stu-id="e5111-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="e5111-110">必要。</span><span class="sxs-lookup"><span data-stu-id="e5111-110">Required.</span></span> <span data-ttu-id="e5111-111">整數值運算式。</span><span class="sxs-lookup"><span data-stu-id="e5111-111">Integral numeric expression.</span></span> <span data-ttu-id="e5111-112">要移位的位元模式。</span><span class="sxs-lookup"><span data-stu-id="e5111-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="e5111-113">資料型別必須是整數類資料型別 (Integral Type) (`SByte`、`Byte`、`Short`、`UShort`、`Integer`、`UInteger`、`Long` 或 `ULong`)。</span><span class="sxs-lookup"><span data-stu-id="e5111-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="e5111-114">必要。</span><span class="sxs-lookup"><span data-stu-id="e5111-114">Required.</span></span> <span data-ttu-id="e5111-115">數值運算式。</span><span class="sxs-lookup"><span data-stu-id="e5111-115">Numeric expression.</span></span> <span data-ttu-id="e5111-116">位元模式移位的位元數。</span><span class="sxs-lookup"><span data-stu-id="e5111-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="e5111-117">資料型別必須是 `Integer` 或擴展至 `Integer`。</span><span class="sxs-lookup"><span data-stu-id="e5111-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5111-118">備註</span><span class="sxs-lookup"><span data-stu-id="e5111-118">Remarks</span></span>  

 <span data-ttu-id="e5111-119">算術移位不是迴圈的，這表示不會在另一端重新出現從結果的一端移出的位。</span><span class="sxs-lookup"><span data-stu-id="e5111-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="e5111-120">在算術左移位中，會捨棄超出結果資料類型範圍的位，而且右邊的位位置會設定為零。</span><span class="sxs-lookup"><span data-stu-id="e5111-120">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
 <span data-ttu-id="e5111-121">為了防止超過結果所能保存的比對位數，Visual Basic 會以 `amount` 對應至資料類型的大小遮罩來遮罩的值 `pattern` 。</span><span class="sxs-lookup"><span data-stu-id="e5111-121">To prevent a shift by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask that corresponds to the data type of `pattern`.</span></span> <span data-ttu-id="e5111-122">這些值的二進位和都是用於移位量。</span><span class="sxs-lookup"><span data-stu-id="e5111-122">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="e5111-123">大小遮罩如下所示：</span><span class="sxs-lookup"><span data-stu-id="e5111-123">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="e5111-124">的資料類型 `pattern`</span><span class="sxs-lookup"><span data-stu-id="e5111-124">Data type of `pattern`</span></span>|<span data-ttu-id="e5111-125">大小遮罩 (decimal) </span><span class="sxs-lookup"><span data-stu-id="e5111-125">Size mask (decimal)</span></span>|<span data-ttu-id="e5111-126">大小遮罩 (十六進位) </span><span class="sxs-lookup"><span data-stu-id="e5111-126">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="e5111-127">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="e5111-127">`SByte`, `Byte`</span></span>|<span data-ttu-id="e5111-128">7</span><span class="sxs-lookup"><span data-stu-id="e5111-128">7</span></span>|<span data-ttu-id="e5111-129">&H00000007</span><span class="sxs-lookup"><span data-stu-id="e5111-129">&H00000007</span></span>|  
|<span data-ttu-id="e5111-130">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="e5111-130">`Short`, `UShort`</span></span>|<span data-ttu-id="e5111-131">15</span><span class="sxs-lookup"><span data-stu-id="e5111-131">15</span></span>|<span data-ttu-id="e5111-132">&H0000000F</span><span class="sxs-lookup"><span data-stu-id="e5111-132">&H0000000F</span></span>|  
|<span data-ttu-id="e5111-133">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="e5111-133">`Integer`, `UInteger`</span></span>|<span data-ttu-id="e5111-134">31</span><span class="sxs-lookup"><span data-stu-id="e5111-134">31</span></span>|<span data-ttu-id="e5111-135">&H0000001F</span><span class="sxs-lookup"><span data-stu-id="e5111-135">&H0000001F</span></span>|  
|<span data-ttu-id="e5111-136">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="e5111-136">`Long`, `ULong`</span></span>|<span data-ttu-id="e5111-137">63</span><span class="sxs-lookup"><span data-stu-id="e5111-137">63</span></span>|<span data-ttu-id="e5111-138">&H0000003F</span><span class="sxs-lookup"><span data-stu-id="e5111-138">&H0000003F</span></span>|  
  
 <span data-ttu-id="e5111-139">如果 `amount` 是零，的值 `result` 就會與的值相同 `pattern` 。</span><span class="sxs-lookup"><span data-stu-id="e5111-139">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="e5111-140">如果 `amount` 是負數，則會被視為不帶正負號的值，並以適當的大小遮罩進行遮罩。</span><span class="sxs-lookup"><span data-stu-id="e5111-140">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="e5111-141">算術移位絕不會產生溢位例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e5111-141">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e5111-142">可以多載 `<<` 運算子*overloaded*，這表示當運算元具有該類別或結構的型別時，類別或結構可以重新定義其行為。</span><span class="sxs-lookup"><span data-stu-id="e5111-142">The `<<` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="e5111-143">如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="e5111-143">If your code uses this operator on such a class or structure, be sure that you understand its redefined behavior.</span></span> <span data-ttu-id="e5111-144">如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="e5111-144">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5111-145">範例</span><span class="sxs-lookup"><span data-stu-id="e5111-145">Example</span></span>  

 <span data-ttu-id="e5111-146">下列範例會使用 `<<` 運算子，在整數值上執行算術左移位。</span><span class="sxs-lookup"><span data-stu-id="e5111-146">The following example uses the `<<` operator to perform arithmetic left shifts on integral values.</span></span> <span data-ttu-id="e5111-147">結果一律具有與要移位的運算式相同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="e5111-147">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#12)]  
  
 <span data-ttu-id="e5111-148">上述範例的結果如下所示：</span><span class="sxs-lookup"><span data-stu-id="e5111-148">The results of the previous example are as follows:</span></span>  
  
- <span data-ttu-id="e5111-149">`result1` 為 192 (0000 0000 1100 0000) 。</span><span class="sxs-lookup"><span data-stu-id="e5111-149">`result1` is 192 (0000 0000 1100 0000).</span></span>  
  
- <span data-ttu-id="e5111-150">`result2` 為 3072 (0000 1100 0000 0000) 。</span><span class="sxs-lookup"><span data-stu-id="e5111-150">`result2` is 3072 (0000 1100 0000 0000).</span></span>  
  
- <span data-ttu-id="e5111-151">`result3` 是-32768 (1000 0000 0000 0000) 。</span><span class="sxs-lookup"><span data-stu-id="e5111-151">`result3` is -32768 (1000 0000 0000 0000).</span></span>  
  
- <span data-ttu-id="e5111-152">`result4` 為 384 (0000 0001 1000 0000) 。</span><span class="sxs-lookup"><span data-stu-id="e5111-152">`result4` is 384 (0000 0001 1000 0000).</span></span>  
  
- <span data-ttu-id="e5111-153">`result5` 為 0 (將15個位置向左) 移位。</span><span class="sxs-lookup"><span data-stu-id="e5111-153">`result5` is 0 (shifted 15 places to the left).</span></span>  
  
 <span data-ttu-id="e5111-154">的移位數量 `result4` 會計算為17和15，等於1。</span><span class="sxs-lookup"><span data-stu-id="e5111-154">The shift amount for `result4` is calculated as 17 AND 15, which equals 1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5111-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5111-155">See also</span></span>

- [<span data-ttu-id="e5111-156">位元移位運算子</span><span class="sxs-lookup"><span data-stu-id="e5111-156">Bit Shift Operators</span></span>](bit-shift-operators.md)
- [<span data-ttu-id="e5111-157">指派運算子</span><span class="sxs-lookup"><span data-stu-id="e5111-157">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="e5111-158"><<= 運算子</span><span class="sxs-lookup"><span data-stu-id="e5111-158"><<= Operator</span></span>](left-shift-assignment-operator.md)
- [<span data-ttu-id="e5111-159">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="e5111-159">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="e5111-160">依功能列出運算子</span><span class="sxs-lookup"><span data-stu-id="e5111-160">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="e5111-161">Visual Basic 的算術運算子</span><span class="sxs-lookup"><span data-stu-id="e5111-161">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)

---
title: HOW TO：十六進位字串轉換為數字 (Visual Basic)
ms.date: 01/31/2018
helpviewer_keywords:
- numbers [Visual Basic], hexadecimals
- hexadecimals [Visual Basic], decimals
- examples [Visual Basic], string conversion
- decimals [Visual Basic], hexadecimals
- string conversion [Visual Basic], hexadecimal to numbers
ms.assetid: 76675807-eadb-4c08-bd50-e6c6ff4b8ced
ms.openlocfilehash: 76acee8913df35d4d071017078b38a3c474c3357
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54633804"
---
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a><span data-ttu-id="c0bd2-102">HOW TO：十六進位字串轉換為數字 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c0bd2-102">How to: Convert Hexadecimal Strings to Numbers (Visual Basic)</span></span>
<span data-ttu-id="c0bd2-103">此範例會將十六進位字串轉換成整數使用<xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="c0bd2-103">This example converts a hexadecimal string to an integer using the <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="to-convert-a-hexadecimal-string-to-a-number"></a><span data-ttu-id="c0bd2-104">若要為十六進位字串轉換為數字</span><span class="sxs-lookup"><span data-stu-id="c0bd2-104">To convert a hexadecimal string to a number</span></span>  
  
-   <span data-ttu-id="c0bd2-105">使用<xref:System.Convert.ToInt32(System.String,System.Int32)>方法，以轉換數字表示成整數的基底為 16。</span><span class="sxs-lookup"><span data-stu-id="c0bd2-105">Use the <xref:System.Convert.ToInt32(System.String,System.Int32)> method to convert the number expressed in base-16 to an integer.</span></span>  
  
     <span data-ttu-id="c0bd2-106">第一個引數<xref:System.Convert.ToInt32(System.String,System.Int32)>方法是要轉換的字串。</span><span class="sxs-lookup"><span data-stu-id="c0bd2-106">The first argument of the <xref:System.Convert.ToInt32(System.String,System.Int32)> method is the string to convert.</span></span> <span data-ttu-id="c0bd2-107">第二個引數描述中，表示的數字基底十六進位為基底 16。</span><span class="sxs-lookup"><span data-stu-id="c0bd2-107">The second argument describes what base the number is expressed in; hexadecimal is base 16.</span></span>  
  
     [!code-vb[HexConversion](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-hexadecimal-strings-to-numbers_1.vb)]  

- <span data-ttu-id="c0bd2-108">請注意十六進位字串具有下列限制：</span><span class="sxs-lookup"><span data-stu-id="c0bd2-108">Note that the hexadecimal string has the following restrictions:</span></span>

   - <span data-ttu-id="c0bd2-109">它不能包含`&h`前置詞。</span><span class="sxs-lookup"><span data-stu-id="c0bd2-109">It cannot include the `&h` prefix.</span></span>
   - <span data-ttu-id="c0bd2-110">它不能包含`_`千位分隔符號。</span><span class="sxs-lookup"><span data-stu-id="c0bd2-110">It cannot include the `_` digit separator.</span></span>

   <span data-ttu-id="c0bd2-111">前置詞或數字分隔符號是否存在，呼叫<xref:System.Convert.ToInt32(System.String,System.Int32)>方法會擲回<xref:System.FormatException>。</span><span class="sxs-lookup"><span data-stu-id="c0bd2-111">If the prefix or a digit separator is present, the call to the <xref:System.Convert.ToInt32(System.String,System.Int32)> method throws a <xref:System.FormatException>.</span></span>

## <a name="see-also"></a><span data-ttu-id="c0bd2-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0bd2-112">See also</span></span>
- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>

---
title: 如何：將十六進位字串轉換為數字
ms.date: 01/31/2018
helpviewer_keywords:
- numbers [Visual Basic], hexadecimals
- hexadecimals [Visual Basic], decimals
- examples [Visual Basic], string conversion
- decimals [Visual Basic], hexadecimals
- string conversion [Visual Basic], hexadecimal to numbers
ms.assetid: 76675807-eadb-4c08-bd50-e6c6ff4b8ced
ms.openlocfilehash: f0a97a0c212a64bfa4db4606ee526b666f07877a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347165"
---
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a><span data-ttu-id="c3fd3-102">如何：將十六進位字串轉換為數字 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3fd3-102">How to: Convert Hexadecimal Strings to Numbers (Visual Basic)</span></span>

<span data-ttu-id="c3fd3-103">這個範例會使用 <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> 方法，將十六進位字串轉換為整數。</span><span class="sxs-lookup"><span data-stu-id="c3fd3-103">This example converts a hexadecimal string to an integer using the <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> method.</span></span>

## <a name="to-convert-a-hexadecimal-string-to-a-number"></a><span data-ttu-id="c3fd3-104">將十六進位字串轉換成數位</span><span class="sxs-lookup"><span data-stu-id="c3fd3-104">To convert a hexadecimal string to a number</span></span>

- <span data-ttu-id="c3fd3-105">使用 <xref:System.Convert.ToInt32(System.String,System.Int32)> 方法，將以 base-16 表示的數位轉換成整數。</span><span class="sxs-lookup"><span data-stu-id="c3fd3-105">Use the <xref:System.Convert.ToInt32(System.String,System.Int32)> method to convert the number expressed in base-16 to an integer.</span></span>

  <span data-ttu-id="c3fd3-106"><xref:System.Convert.ToInt32(System.String,System.Int32)> 方法的第一個引數是要轉換的字串。</span><span class="sxs-lookup"><span data-stu-id="c3fd3-106">The first argument of the <xref:System.Convert.ToInt32(System.String,System.Int32)> method is the string to convert.</span></span> <span data-ttu-id="c3fd3-107">第二個引數描述以數位表示的基底。十六進位是基底16。</span><span class="sxs-lookup"><span data-stu-id="c3fd3-107">The second argument describes what base the number is expressed in; hexadecimal is base 16.</span></span>

  [!code-vb[VbVbalrStrings#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#62)]

- <span data-ttu-id="c3fd3-108">請注意，十六進位字串具有下列限制：</span><span class="sxs-lookup"><span data-stu-id="c3fd3-108">Note that the hexadecimal string has the following restrictions:</span></span>

  - <span data-ttu-id="c3fd3-109">它不能包含 `&h` 前置詞。</span><span class="sxs-lookup"><span data-stu-id="c3fd3-109">It cannot include the `&h` prefix.</span></span>
  - <span data-ttu-id="c3fd3-110">它不能包含 `_` 數位分隔符號。</span><span class="sxs-lookup"><span data-stu-id="c3fd3-110">It cannot include the `_` digit separator.</span></span>

  <span data-ttu-id="c3fd3-111">如果有前置詞或數位分隔符號，則呼叫 <xref:System.Convert.ToInt32(System.String,System.Int32)> 方法會擲回 <xref:System.FormatException>。</span><span class="sxs-lookup"><span data-stu-id="c3fd3-111">If the prefix or a digit separator is present, the call to the <xref:System.Convert.ToInt32(System.String,System.Int32)> method throws a <xref:System.FormatException>.</span></span>

## <a name="see-also"></a><span data-ttu-id="c3fd3-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="c3fd3-112">See also</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>

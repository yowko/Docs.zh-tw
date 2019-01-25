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
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a>HOW TO：十六進位字串轉換為數字 (Visual Basic)
此範例會將十六進位字串轉換成整數使用<xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>方法。  
  
## <a name="to-convert-a-hexadecimal-string-to-a-number"></a>若要為十六進位字串轉換為數字  
  
-   使用<xref:System.Convert.ToInt32(System.String,System.Int32)>方法，以轉換數字表示成整數的基底為 16。  
  
     第一個引數<xref:System.Convert.ToInt32(System.String,System.Int32)>方法是要轉換的字串。 第二個引數描述中，表示的數字基底十六進位為基底 16。  
  
     [!code-vb[HexConversion](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-hexadecimal-strings-to-numbers_1.vb)]  

- 請注意十六進位字串具有下列限制：

   - 它不能包含`&h`前置詞。
   - 它不能包含`_`千位分隔符號。

   前置詞或數字分隔符號是否存在，呼叫<xref:System.Convert.ToInt32(System.String,System.Int32)>方法會擲回<xref:System.FormatException>。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>

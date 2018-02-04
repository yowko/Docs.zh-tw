---
title: "如何：將十六進位字串轉換為數字 (Visual Basic)"
ms.custom: 
ms.date: 01/31/2018
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- numbers [Visual Basic], hexadecimals
- hexadecimals [Visual Basic], decimals
- examples [Visual Basic], string conversion
- decimals [Visual Basic], hexadecimals
- string conversion [Visual Basic], hexadecimal to numbers
ms.assetid: 76675807-eadb-4c08-bd50-e6c6ff4b8ced
author: petrusha
ms.author: ronpet
ms.manager: wpickett
ms.openlocfilehash: c35ac615e3f87710f934a1cf66e6546625298bd0
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2018
---
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a>如何：將十六進位字串轉換為數字 (Visual Basic)
這個範例會將十六進位字串轉換成整數使用<xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>方法。  
  
## <a name="to-convert-a-hexadecimal-string-to-a-number"></a>若要將十六進位字串轉換為數字  
  
-   使用<xref:System.Convert.ToInt32(System.String,System.Int32)>方法，將轉換的數字表示為整數的基底為 16。  
  
     第一個引數<xref:System.Convert.ToInt32(System.String,System.Int32)>方法是要轉換的字串。 第二個引數描述哪些; 表示的數字的基底十六進位為基底 16。  
  
     [!code-vb[HexConversion](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-hexadecimal-strings-to-numbers_1.vb)]  

- 請注意十六進位字串具有下列限制：

   - 它不能包含`&h`前置詞。
   - 它不能包含`_`千位分隔符號。

   前置詞或數字分隔符號是否存在，呼叫<xref:System.Convert.ToInt32(System.String,System.Int32)>方法會擲回<xref:System.FormatException>。

## <a name="see-also"></a>請參閱  
 <xref:Microsoft.VisualBasic.Conversion.Hex%2A>  
 <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>

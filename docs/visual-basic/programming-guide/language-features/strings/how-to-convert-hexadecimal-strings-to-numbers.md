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
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a>如何：將十六進位字串轉換為數字 (Visual Basic)

這個範例會使用 <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> 方法，將十六進位字串轉換為整數。

## <a name="to-convert-a-hexadecimal-string-to-a-number"></a>將十六進位字串轉換成數位

- 使用 <xref:System.Convert.ToInt32(System.String,System.Int32)> 方法，將以 base-16 表示的數位轉換成整數。

  <xref:System.Convert.ToInt32(System.String,System.Int32)> 方法的第一個引數是要轉換的字串。 第二個引數描述以數位表示的基底。十六進位是基底16。

  [!code-vb[VbVbalrStrings#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#62)]

- 請注意，十六進位字串具有下列限制：

  - 它不能包含 `&h` 前置詞。
  - 它不能包含 `_` 數位分隔符號。

  如果有前置詞或數位分隔符號，則呼叫 <xref:System.Convert.ToInt32(System.String,System.Int32)> 方法會擲回 <xref:System.FormatException>。

## <a name="see-also"></a>請參閱

- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>

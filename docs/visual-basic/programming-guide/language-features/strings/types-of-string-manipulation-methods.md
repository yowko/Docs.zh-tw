---
title: 字串操作方法的類型
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
ms.openlocfilehash: c44f02880858b8a9fc1f0e70c3226623d05baa3a
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072466"
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a>Visual Basic 中字串管理方法的類型

有幾種不同的方式可以分析和操作您的字串。 某些方法是 Visual Basic 語言的一部分，而其他方法則是類別中的固有部分 `String` 。  
  
## <a name="visual-basic-language-and-the-net-framework"></a>Visual Basic 語言和 .NET Framework  

 Visual Basic 方法會當做語言的固有函式使用。 您可以使用它們，而不需要在程式碼中限定。 下列範例顯示 Visual Basic 字串操作命令的一般用法：  
  
 [!code-vb[VbVbalrStrings#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#44)]  
  
 在此範例中，此函式會 `Mid` 在上執行直接操作 `aString` ，並將值指派給 `bString` 。  
  
 如需 Visual Basic 字串操作方法的清單，請參閱 [字串操作摘要](../../../language-reference/keywords/string-manipulation-summary.md)。  
  
### <a name="shared-methods-and-instance-methods"></a>共用方法與實例方法  

 您也可以使用類別的方法來操作字串 `String` 。 中有兩種類型的方法 `String` ： *共用* 方法和 *實例* 方法。  
  
#### <a name="shared-methods"></a>共用方法  

 共用方法是源自類別本身的方法，不 `String` 需要該類別的實例就能運作。 您可以使用類別的名稱來限定這些方法 (`String`) ，而不是類別的實例 `String` 。 例如：  
  
 [!code-vb[VbVbalrStrings#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#45)]  
  
 在上述範例中， <xref:System.String.Copy%2A?displayProperty=nameWithType> 方法是靜態方法，它會在其所指定的運算式上運作，並將產生的值指派給 `bString` 。  
  
#### <a name="instance-methods"></a>實例方法  

 相反地，實例方法是來自特定的實例， `String` 而且必須使用實例名稱來限定。 例如：  
  
 [!code-vb[VbVbalrStrings#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#46)]  
  
 在此範例中， <xref:System.String.Substring%2A?displayProperty=nameWithType> 方法是 (實例的方法 `String` ，也就是 `aString`) 。 它會對執行運算 `aString` ，並將該值指派給 `bString` 。  
  
 如需詳細資訊，請參閱類別的檔 <xref:System.String> 。  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的字串簡介](introduction-to-strings.md)

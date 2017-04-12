---
title: "字元資料類型 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- data types [Visual Basic], character
- String data type, character data types
- character data types [Visual Basic]
- Char data type, character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7ce600fe188c94593e4c07e37883ca11f90d9ae5
ms.lasthandoff: 03/13/2017

---
# <a name="character-data-types-visual-basic"></a>字元資料類型 (Visual Basic)
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]提供*字元資料類型*應付可顯示的可列印字元。 雖然兩者處理 Unicode 字元`Char`保存單一字元，而`String`包含任何數目的字元。  
  
 顯示並行所比較之資料表的[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]資料類型，請參閱[資料型別](../../../../visual-basic/language-reference/data-types/data-type-summary.md)。  
  
## <a name="char-type"></a>Char 類型  
 `Char`資料型別是單一的兩個位元組 （16 位元） 的 Unicode 字元。 如果變數只會儲存一個字元，將它宣告為`Char`。 例如:   
  
 [!code-vb[VbVbalrCharTypes #&1;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/character-data-types_1.vb)]  
  
 在每個可能值`Char`或`String`變數是*程式碼點*，或在 Unicode 字元集的字元碼。 Unicode 字元包含基本 ASCII 字元集、 各種其他字母字元、 腔調字、 貨幣符號、 分數、 變音符號和數學和技術的符號。  
  
> [!NOTE]
>  Unicode 字元集字碼元素 D800 到 DFFF (55296 透過 55551 十進位) 的保留*surrogate 配對*，而這需要兩個 16 位元的值代表單一字碼指標。 A`Char`變數不能保留 surrogate 字組和`String`會使用兩個位置來容納這些組。  
  
 如需詳細資訊，請參閱[Char 資料型別](../../../../visual-basic/language-reference/data-types/char-data-type.md)。  
  
## <a name="string-type"></a>字串型別  
 `String`資料型別是一串零個或兩個位元組 （16 位元） Unicode 字元。 如果變數可以包含任何數目的字元，將它宣告為`String`。 例如:   
  
 [!code-vb[VbVbalrCharTypes #&2;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/character-data-types_2.vb)]  
  
 如需詳細資訊，請參閱[字串資料型別](../../../../visual-basic/language-reference/data-types/string-data-type.md)。  
  
## <a name="see-also"></a>另請參閱  
 [基本資料型別](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [複合資料型別](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)   
 [Visual Basic 中的泛型型別](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [實值型別和參考型別](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [在 Visual Basic 中的型別轉換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [資料類型疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [類型字元](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)

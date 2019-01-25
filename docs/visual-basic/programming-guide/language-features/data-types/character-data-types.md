---
title: 字元資料類型 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
ms.openlocfilehash: 5ede86cca1bddb15cab6518e17405837bda008f4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54536889"
---
# <a name="character-data-types-visual-basic"></a>字元資料類型 (Visual Basic)
Visual Basic 提供*字元資料類型*應付可顯示的可列印字元。 雖然兩者都使用 Unicode 字元處理`Char`保留的單一字元，而`String`包含不限數目的字元。  
  
 顯示 Visual Basic 資料類型的並排顯示比較的資料表，請參閱 <<c0> [ 資料型別](../../../../visual-basic/language-reference/data-types/index.md)。  
  
## <a name="char-type"></a>Char 類型  
 `Char`資料類型是單一的兩個位元組 （16 位元） 的 Unicode 字元。 如果變數一律會儲存一個字元，將它宣告為`Char`。 例如:   
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 中的每個可能值`Char`或`String`變數*字碼指標*，或在 Unicode 字元集的字元碼。 Unicode 字元會包含基本 ASCII 字元集、 各種其他字母字元、 重音符號、 貨幣符號、 分數、 變音符號與數學和技術的符號。  
  
> [!NOTE]
>  Unicode 字元集字碼元素 D800 到 DFFF (55296 透過 55551 十進位) 的保留*surrogate 字組*，而這需要兩個 16 位元值，來代表單一字碼指標。 A`Char`變數不能保留 surrogate 字組和`String`來保留這類組會使用兩個位置。  
  
 如需詳細資訊，請參閱 < [Char 資料型別](../../../../visual-basic/language-reference/data-types/char-data-type.md)。  
  
## <a name="string-type"></a>字串類型  
 `String`資料型別是一串零或多個兩個位元組 （16 位元） 的 Unicode 字元。 如果變數可以包含任何數目的字元，將它宣告為`String`。 例如:   
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 如需詳細資訊，請參閱 <<c0> [ 字串資料型別](../../../../visual-basic/language-reference/data-types/string-data-type.md)。  
  
## <a name="see-also"></a>另請參閱
- [基礎資料類型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [複合資料類型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Generic Types in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [在 Visual Basic 中的類型轉換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [資料類型的疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [類型字元](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)

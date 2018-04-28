---
title: 字元資料類型 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: afd368c00444f136c6d69b02a733c82f0c8eafe0
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="character-data-types-visual-basic"></a>字元資料類型 (Visual Basic)
Visual Basic 提供*字元資料類型*處理可列印及可顯示的字元。 雖然它們都使用 Unicode 字元處理`Char`保存單一字元，而`String`包含了不定數量的字元。  
  
 顯示的 Visual Basic 資料類型來並行比較的資料表，請參閱[資料型別](../../../../visual-basic/language-reference/data-types/data-type-summary.md)。  
  
## <a name="char-type"></a>Char 類型  
 `Char`資料類型是單一的兩個位元組 （16 位元） 的 Unicode 字元。 如果變數一律會儲存一個字元，將它宣告為`Char`。 例如:   
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 中的每個可能值`Char`或`String`變數是*程式碼點*，或在 Unicode 字元集的字元碼。 Unicode 字元包括基本的 ASCII 字元集、 各種其他字母字元、 重音符號、 貨幣符號、 分數、 變音符號和數學和技術的符號。  
  
> [!NOTE]
>  Unicode 字元集字碼元素 D800 到 DFFF (透過 55551 十進位 55296) 的保留*surrogate 字組*，而這需要兩個 16 位元值來表示單一字碼指標。 A`Char`變數無法容納 surrogate 字組和`String`用來保留此類配對的兩個位置。  
  
 如需詳細資訊，請參閱[Char 資料類型](../../../../visual-basic/language-reference/data-types/char-data-type.md)。  
  
## <a name="string-type"></a>字串類型  
 `String`資料型別是一串零或多個兩個位元組 （16 位元） 的 Unicode 字元。 如果變數可以包含任何數目的字元，將它宣告為`String`。 例如:   
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 如需詳細資訊，請參閱[字串資料型別](../../../../visual-basic/language-reference/data-types/string-data-type.md)。  
  
## <a name="see-also"></a>另請參閱  
 [基礎資料類型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [複合資料類型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [Visual Basic 中的泛型型別](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [值類型和參考類型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [在 Visual Basic 中的型別轉換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [資料類型的疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [類型字元](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)

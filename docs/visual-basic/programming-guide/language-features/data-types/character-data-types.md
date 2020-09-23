---
title: 字元資料類型
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
ms.openlocfilehash: 5fde5eff40d83bdd7d90cd611bd6749106db6e16
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077172"
---
# <a name="character-data-types-visual-basic"></a>字元資料類型 (Visual Basic)

Visual Basic 提供 *字元資料類型* 來處理可列印和可顯示的字元。 雖然它們都處理 Unicode 字元，但會保留一個字元，而不會 `Char` `String` 包含不定數目的字元。  
  
 如需顯示 Visual Basic 資料類型之並列比較的資料表，請參閱 [資料類型](../../../language-reference/data-types/index.md)。  
  
## <a name="char-type"></a>Char 類型  

 `Char`資料類型是單一雙位元組 (16 位) Unicode 字元。 如果變數永遠只儲存一個字元，請將它宣告為 `Char` 。 例如：  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 或變數中的每個可能值 `Char` `String` 都是 Unicode 字元集中的程式 *代碼點*或字元碼。 Unicode 字元包括基本的 ASCII 字元集、各種其他字母字母、重音、貨幣符號、分數、變音符號，以及數學和技術符號。  
  
> [!NOTE]
> Unicode 字元集會保留程式碼點 D800 至 DFFF (55296 至 55551 decimal) 用於 *代理配對*，這需要 2 16 位值以表示單一程式碼點。 `Char`變數無法保存代理組，而且會 `String` 使用兩個位置來保存這類配對。  
  
 如需詳細資訊，請參閱 [Char 資料型別](../../../language-reference/data-types/char-data-type.md)。  
  
## <a name="string-type"></a>字串類型  

 `String`資料類型是零或多個雙位元組 (16 位) Unicode 字元的序列。 如果變數可以包含不限數量的字元，請將它宣告為 `String` 。 例如：  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 如需詳細資訊，請參閱 [字串資料類型](../../../language-reference/data-types/string-data-type.md)。  
  
## <a name="see-also"></a>另請參閱

- [基礎資料類型](elementary-data-types.md)
- [複合資料類型](composite-data-types.md)
- [Generic Types in Visual Basic](generic-types.md)
- [Value Types and Reference Types](value-types-and-reference-types.md)
- [Visual Basic 中的類型轉換](type-conversions.md)
- [疑難排解資料類型的問題](troubleshooting-data-types.md)
- [類型字元](type-characters.md)

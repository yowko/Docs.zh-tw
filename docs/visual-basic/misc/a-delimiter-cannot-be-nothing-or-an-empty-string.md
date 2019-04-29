---
title: 分隔符號不可以是 Nothing 或空字串
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_DelimiterNothing
ms.assetid: 8885fcd1-c201-409d-9a32-6ff2b13c0c13
ms.openlocfilehash: ff21545bfe12fb8f6eccd50fd00c138bbab92b97
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940708"
---
# <a name="a-delimiter-cannot-be-nothing-or-an-empty-string"></a>分隔符號不可以是 Nothing 或空字串
`TextFieldParser` 無法讀取自檔案，因為 `Delimiters` 屬性設定為 `Nothing` 或為空白 `String` ("")。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 請提供 `Delimiters`的有效值。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters>
- [如何：從逗號分隔文字檔讀取](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [TextFieldParser 物件](../../visual-basic/language-reference/objects/textfieldparser-object.md)
- [使用 TextFieldParser 物件剖析文字檔](../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)

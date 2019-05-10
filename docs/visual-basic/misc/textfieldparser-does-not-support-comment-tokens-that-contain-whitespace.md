---
title: TextFieldParser 不支援包含空白字元的註解語彙基元
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_WhitespaceInToken
ms.assetid: 55107656-270e-4bbb-841a-478904df8e07
ms.openlocfilehash: af0f09bb7a8afc3b6e63cfab1a7176ba26cf20a6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64660889"
---
# <a name="textfieldparser-does-not-support-comment-tokens-that-contain-white-space"></a>TextFieldParser 不支援包含空白字元的註解語彙基元
已提供包含空白字元的註解語彙基元。 `TextFieldParser` 不支援包含空白字元的註解語彙基元，除非空白字元發生在語彙基元的開頭。 發生在語彙基元開頭的空白字元會被忽略。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 請提供正確的註解語彙基元。  
  
## <a name="see-also"></a>另請參閱

- [TextFieldParser.CommentTokens 屬性](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.CommentTokens%2A)
- [使用 TextFieldParser 物件剖析文字檔](../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [TextFieldParser 物件](../../visual-basic/language-reference/objects/textfieldparser-object.md)

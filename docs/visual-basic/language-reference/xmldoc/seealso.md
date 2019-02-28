---
title: <seealso> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <seealso> XML tag
- seealso XML tag
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
ms.openlocfilehash: 9f857be6d0bd46233a49c7d2ff0931670baa95a6
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965295"
---
# <a name="seealso-visual-basic"></a>\<seealso > (Visual Basic)
指定另請參閱 > 一節中所顯示的連結。  
  
## <a name="syntax"></a>語法  
  
```xml  
<seealso cref="member"/>  
```  
  
#### <a name="parameters"></a>參數  
 `member`  
 可從目前編譯環境呼叫的成員或欄位參考。 編譯器會檢查指定的程式碼項目是否存在，並將 `member` 傳遞給輸出 XML 中的項目名稱。 `member` 必須出現在雙引號內 (" ")。  
  
## <a name="remarks"></a>備註  
 使用`<seealso>`標記即可指定您想要另請參閱 > 一節中所顯示的文字。 使用 [\<see>](../../../visual-basic/language-reference/xmldoc/see.md)，以在文字內指定連結。  
  
 編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
 這個範例會使用`<seealso>`標記中的`DoesRecordExist`註解區段來參考`UpdateRecord`方法。  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>另請參閱
- [XML 註解標記](../../../visual-basic/language-reference/xmldoc/index.md)

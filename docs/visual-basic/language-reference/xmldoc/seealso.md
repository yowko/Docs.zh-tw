---
title: <seealso>
ms.date: 07/20/2015
helpviewer_keywords:
- <seealso> XML tag
- seealso XML tag
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
ms.openlocfilehash: 27bb2c271631170082709d9e3d76cd39eefbc860
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352209"
---
# <a name="seealso-visual-basic"></a>\<seealso> (Visual Basic)
Specifies a link that appears in the See Also section.  
  
## <a name="syntax"></a>語法  
  
```xml  
<seealso cref="member"/>  
```  
  
## <a name="parameters"></a>參數  
 `member`  
 可從目前編譯環境呼叫的成員或欄位參考。 編譯器會檢查指定的程式碼項目是否存在，並將 `member` 傳遞給輸出 XML 中的項目名稱。 `member` 必須出現在雙引號內 (" ")。  
  
## <a name="remarks"></a>備註  
 Use the `<seealso>` tag to specify the text that you want to appear in a See Also section. 使用 [\<see>](../../../visual-basic/language-reference/xmldoc/see.md)，以在文字內指定連結。  
  
 使用 [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) 編譯可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
 This example uses the `<seealso>` tag in the `DoesRecordExist` remarks section to refer to the `UpdateRecord` method.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>請參閱

- [XML 註解標記](../../../visual-basic/language-reference/xmldoc/index.md)

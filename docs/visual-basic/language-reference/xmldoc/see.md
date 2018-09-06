---
title: '&lt;請參閱&gt;(Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
ms.openlocfilehash: 78311651593d3d4a47c723f64a9a74d4660f7c90
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43854901"
---
# <a name="ltseegt-visual-basic"></a>&lt;請參閱&gt;(Visual Basic)
指定另一個成員的連結。  
  
## <a name="syntax"></a>語法  
  
```xml  
<see cref="member"/>  
```  
  
#### <a name="parameters"></a>參數  
 `member`  
 可從目前編譯環境呼叫的成員或欄位參考。 編譯器會檢查指定的程式碼項目存在，並將傳遞`member`輸出 XML 中的項目名稱。 `member` 必須出現在雙引號內 (" ")。  
  
## <a name="remarks"></a>備註  
 使用`<see>`標記即可指定文字中的連結。 使用[ \<seealso >](../../../visual-basic/language-reference/xmldoc/seealso.md)指出要顯示 「 請參閱 < 另請參閱 > 一節中的文字。  
  
 編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
 這個範例會使用`<see>`標記中的`UpdateRecord`註解區段來參考`DoesRecordExist`方法。  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/see_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [XML 註解標記](../../../visual-basic/language-reference/xmldoc/index.md)

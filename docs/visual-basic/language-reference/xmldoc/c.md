---
title: '&lt;c&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 556c00fa761a1bce5e922a304706c78893550901
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ltcgt-visual-basic"></a>&lt;c&gt; (Visual Basic)
描述內的文字表示的程式碼。  
  
## <a name="syntax"></a>語法  
  
```xml  
<c>text</c>  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|---|---|  
|`text`|您要指定為程式碼的文字。|  
  
## <a name="remarks"></a>備註  
 `<c>`標籤會提供一個方法來指示描述內的文字應該標記為程式碼。 請使用 [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) 將多行指定為程式碼。  
  
 編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
 這個範例會使用`<c>`表示摘要區段中的標記`Counter`是程式碼。  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/c_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [XML 註解標記](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)

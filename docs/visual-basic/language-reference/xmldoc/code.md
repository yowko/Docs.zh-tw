---
title: '&lt;程式碼&gt;(Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: 9ec9d23f1f62358dc272f9764f88e3bb2ba41f78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ltcodegt-visual-basic"></a>&lt;程式碼&gt;(Visual Basic)
指出文字是多行程式碼。  
  
## <a name="syntax"></a>語法  
  
```xml  
<code>content</code>  
```  
  
#### <a name="parameters"></a>參數  
 `content`  
 要標記為程式碼的文字。  
  
## <a name="remarks"></a>備註  
 使用`<code>`標記來表示多行程式碼。 [\<c>](../../../visual-basic/language-reference/xmldoc/c.md) 則用來指出在一段描述中應該標記為程式碼的文字。  
  
 編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
 這個範例會使用\<程式碼 > 標記包含範例程式碼使用`ID`欄位。  
  
 [!code-vb[VbVbcnXmlDocComments#2](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/code_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [XML 註解標記](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)

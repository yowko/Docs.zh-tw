---
title: '&lt;paramref&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: 763e311dfb46ceeed358c3b3bebd6212d3e2489c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ltparamrefgt-visual-basic"></a>&lt;paramref&gt; (Visual Basic)
格式化文字，做為參數。  
  
## <a name="syntax"></a>語法  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a>參數  
 `name`  
 要參考的參數名稱。 以雙引號 (" ") 括住名稱。  
  
## <a name="remarks"></a>備註  
 `<paramref>`標籤會提供一個方法來指示一個字是參數。 可以處理 XML 檔案，以醒目的方式格式化此參數。  
  
 編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
 這個範例會使用`<paramref>`標記來參考`id`參數。  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/paramref_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [XML 註解標記](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)

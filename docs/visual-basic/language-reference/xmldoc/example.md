---
title: '&lt;範例&gt;(Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: cd5ec21001263d7484500ab7680e6e36270e8768
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54670508"
---
# <a name="ltexamplegt-visual-basic"></a>&lt;範例&gt;(Visual Basic)
指定成員的範例。  
  
## <a name="syntax"></a>語法  
  
```xml  
<example>description</example>  
```  
  
#### <a name="parameters"></a>參數  
 `description`  
 程式碼範例的描述。  
  
## <a name="remarks"></a>備註  
 `<example>`標記可讓您指定如何使用方法或其他程式庫成員的範例。 這通常需要使用 [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) 標記。  
  
 編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
 這個範例會使用`<example>`包含使用的範例標記`ID`欄位。  
  
 [!code-vb[VbVbcnXmlDocComments#2](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/example_1.vb)]  
  
## <a name="see-also"></a>另請參閱
- [XML 註解標記](../../../visual-basic/language-reference/xmldoc/index.md)

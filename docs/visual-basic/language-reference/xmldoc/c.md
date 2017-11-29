---
title: '&lt;c&gt; (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7e57cae8fd4b93fee59992d717135ad7d3d78be5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltcgt-visual-basic"></a>&lt;c&gt; (Visual Basic)
描述內的文字表示的程式碼。  
  
## <a name="syntax"></a>語法  
  
```xml  
<c>text</c>  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|說明|  
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

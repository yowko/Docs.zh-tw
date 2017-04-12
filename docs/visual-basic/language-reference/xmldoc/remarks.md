---
title: "&lt;註解&gt;(Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 89f8d321505b528d07fd04780cec06fb65b0e05e
ms.lasthandoff: 03/13/2017

---
# <a name="ltremarksgt-visual-basic"></a>&lt;註解&gt;(Visual Basic)
指定成員的 < 備註 > 一節。  
  
## <a name="syntax"></a>語法  
  
```  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a>參數  
 `description`  
 成員的說明。  
  
## <a name="remarks"></a>備註  
 使用`<remarks>`標記來加入相關型別，以指定的資訊的補充資訊[\<摘要 >](../../../visual-basic/language-reference/xmldoc/summary.md)。  
  
 這項資訊會出現在 物件瀏覽器。 物件瀏覽器的相關資訊，請參閱[檢視程式碼結構](https://docs.microsoft.com/visualstudio/ide/viewing-the-structure-of-code)。  
  
 使用編譯[/doc](../../../visual-basic/reference/command-line-compiler/doc.md)程序至檔案的文件註解。  
  
## <a name="example"></a>範例  
 這個範例會使用`<remarks>`標記來解釋什麼`UpdateRecord`方法會執行。  
  
 [!code-vb[VbVbcnXmlDocComments #&6;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/remarks_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [XML 註解標記](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)

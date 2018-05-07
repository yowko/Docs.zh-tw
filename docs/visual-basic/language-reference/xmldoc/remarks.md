---
title: '&lt;註解&gt;(Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: 6e4e280760b9238fdc403ac5fe586743334e4c69
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ltremarksgt-visual-basic"></a>&lt;註解&gt;(Visual Basic)
指定成員的 < 備註 > 一節。  
  
## <a name="syntax"></a>語法  
  
```xml  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a>參數  
 `description`  
 成員的描述。  
  
## <a name="remarks"></a>備註  
 使用`<remarks>`加入類型，補充指定的資訊的相關資訊的標記[\<摘要 >](../../../visual-basic/language-reference/xmldoc/summary.md)。  
  
 這項資訊會出現在 物件瀏覽器。 物件瀏覽器的相關資訊，請參閱[檢視程式碼結構](/visualstudio/ide/viewing-the-structure-of-code)。  
  
 編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
 這個範例會使用`<remarks>`標記加入至說明`UpdateRecord`方法會執行。  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/remarks_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [XML 註解標記](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)

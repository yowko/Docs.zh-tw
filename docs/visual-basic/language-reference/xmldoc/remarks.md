---
title: <remarks> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: 7125f6079811421bc5a7abdce2e13d591a299630
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269324"
---
# <a name="remarks-visual-basic"></a>\<備註 > (Visual Basic)
指定成員的 < 備註 > 一節。  
  
## <a name="syntax"></a>語法  
  
```xml  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a>參數  
 `description`  
 成員的描述。  
  
## <a name="remarks"></a>備註  
 使用`<remarks>`類型，補充使用指定的資訊的相關資訊，將標記[\<摘要 >](../../../visual-basic/language-reference/xmldoc/summary.md)。  
  
 這項資訊會出現在 物件瀏覽器中。 物件瀏覽器的相關資訊，請參閱[檢視程式碼結構](/visualstudio/ide/viewing-the-structure-of-code)。  
  
 編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
 這個範例會使用`<remarks>`標記來解釋什麼`UpdateRecord`方法會執行。  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/remarks_1.vb)]  
  
## <a name="see-also"></a>另請參閱
- [XML 註解標記](../../../visual-basic/language-reference/xmldoc/index.md)

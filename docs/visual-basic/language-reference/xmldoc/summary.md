---
title: '&lt;摘要&gt;(Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 5ef9b7a98503ff36174de4418ca7d599c365f5aa
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44187256"
---
# <a name="ltsummarygt-visual-basic"></a>&lt;摘要&gt;(Visual Basic)
指定成員的摘要。  
  
## <a name="syntax"></a>語法  
  
```xml  
<summary>description</summary>  
```  
  
#### <a name="parameters"></a>參數  
 `description`  
 物件的摘要。  
  
## <a name="remarks"></a>備註  
 使用`<summary>`標記來描述類型或類型成員。 使用 [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md) 新增類型描述的補充資訊。  
  
 文字`<summary>`標記在 IntelliSense 中類型的相關資訊的唯一來源，且也會顯示在 物件瀏覽器。 物件瀏覽器的相關資訊，請參閱[檢視程式碼結構](/visualstudio/ide/viewing-the-structure-of-code)。  
  
 編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
 這個範例會使用`<summary>`標記來描述`ResetCounter`方法和`Counter`屬性。  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/summary_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [XML 註解標記](../../../visual-basic/language-reference/xmldoc/index.md)

---
title: <summary> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 0fbe07884f55b7e6f460929e54520de5f718e1af
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940760"
---
# <a name="summary-visual-basic"></a>\<m > (Visual Basic)
指定成員的摘要。  
  
## <a name="syntax"></a>語法  
  
```xml  
<summary>description</summary>  
```  
  
## <a name="parameters"></a>參數  
 `description`  
 物件的摘要。  
  
## <a name="remarks"></a>備註  
 使用`<summary>`標記來描述類型或類型成員。 使用 [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md) 新增類型描述的補充資訊。  
  
 文字`<summary>`標記在 IntelliSense 中類型的相關資訊的唯一來源，且也會顯示在 物件瀏覽器。 物件瀏覽器的相關資訊，請參閱[檢視程式碼結構](/visualstudio/ide/viewing-the-structure-of-code)。  
  
 編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
 這個範例會使用`<summary>`標記來描述`ResetCounter`方法和`Counter`屬性。  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [XML 註解標記](../../../visual-basic/language-reference/xmldoc/index.md)

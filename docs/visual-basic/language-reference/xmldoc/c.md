---
title: <c> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 9be9f9e96fc1b79ea97d54c54352da63b93ef264
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58838036"
---
# <a name="c-visual-basic"></a>\<c > (Visual Basic)
表示描述內的文字是程式碼。  
  
## <a name="syntax"></a>語法  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a>參數  
  
|參數|描述|  
|---|---|  
|`text`|您要指定為程式碼的文字。|  
  
## <a name="remarks"></a>備註  
 `<c>`標記可讓您一個方法來指示應該標記為程式碼，在一段描述的文字。 請使用 [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) 將多行指定為程式碼。  
  
 編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
 這個範例會使用`<c>`表示的摘要區段中的標記`Counter`是程式碼。  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [XML 註解標記](../../../visual-basic/language-reference/xmldoc/index.md)

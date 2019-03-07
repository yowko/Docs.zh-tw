---
title: <value> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 7ab1f4a19793c408acfe1c4adf76aed5679fc696
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474263"
---
# <a name="value-visual-basic"></a>\<值 > (Visual Basic)
指定屬性的描述。  
  
## <a name="syntax"></a>語法  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a>參數  
 `property-description`  
 屬性的描述。  
  
## <a name="remarks"></a>備註  
 使用`<value>`標記來描述屬性。 請注意，當您新增屬性，在 Visual Studio 開發環境中使用的程式碼精靈，它會新增[\<摘要 >](../../../visual-basic/language-reference/xmldoc/summary.md)新屬性的標記。 接著，您應該手動新增`<value>`標記來描述所代表之屬性的值。  
  
 編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
 這個範例會使用`<value>`標記來描述哪些值`Counter`屬性會保存。  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>另請參閱
- [XML 註解標記](../../../visual-basic/language-reference/xmldoc/index.md)

---
title: <value>
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 240c2131179420834e6dade729ee631c0d7811a4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352178"
---
# <a name="value-visual-basic"></a>\<value> (Visual Basic)
Specifies the description of a property.  
  
## <a name="syntax"></a>語法  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a>參數  
 `property-description`  
 屬性的描述。  
  
## <a name="remarks"></a>備註  
 Use the `<value>` tag to describe a property. Note that when you add a property using the code wizard in the Visual Studio development environment, it will add a [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md) tag for the new property. You should then manually add a `<value>` tag to describe the value that the property represents.  
  
 使用 [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) 編譯可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
 This example uses the `<value>` tag to describe what value the `Counter` property holds.  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>請參閱

- [XML 註解標記](../../../visual-basic/language-reference/xmldoc/index.md)

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
# <a name="value-visual-basic"></a>\<值 > （Visual Basic）
指定屬性的描述。  
  
## <a name="syntax"></a>語法  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a>參數  
 `property-description`  
 屬性的描述。  
  
## <a name="remarks"></a>備註  
 使用 `<value>` 標記來描述屬性。 請注意，當您在 Visual Studio 開發環境中使用程式碼 wizard 加入屬性時，它會為新的屬性加入[\<摘要 >](../../../visual-basic/language-reference/xmldoc/summary.md)標記。 接著，您應該手動加入 `<value>` 標記，以描述屬性所代表的值。  
  
 使用 [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) 編譯可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
 這個範例會使用 `<value>` 標記來描述 `Counter` 屬性所保存的值。  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [XML 註解標記](../../../visual-basic/language-reference/xmldoc/index.md)

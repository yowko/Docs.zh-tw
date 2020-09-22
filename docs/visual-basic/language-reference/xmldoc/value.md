---
title: <value>
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 550f8b63928f80878ba316bfaf09077e14091305
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875172"
---
# <a name="value-visual-basic"></a>\<value> (Visual Basic)

指定屬性的描述。  
  
## <a name="syntax"></a>語法  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a>參數  

 `property-description`  
 屬性的描述。  
  
## <a name="remarks"></a>備註  

 使用 `<value>` 標記來描述屬性。 請注意，當您在 Visual Studio 開發環境中使用程式碼嚮導加入屬性時，它會 [\<summary>](summary.md) 新增新屬性的標記。 然後，您應該手動新增 `<value>` 標記，以描述該屬性代表的值。  
  
 使用 [-doc](../../reference/command-line-compiler/doc.md) 進行編譯，以處理檔批註至檔案。  
  
## <a name="example"></a>範例  

 此範例會使用 `<value>` 標記來描述屬性所保存的值 `Counter` 。  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [XML 註解標籤](index.md)

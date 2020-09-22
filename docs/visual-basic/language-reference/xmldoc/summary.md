---
title: <summary>
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 471d3ddb5cf5a234cb77de6d1d93309faf754359
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90865837"
---
# <a name="summary-visual-basic"></a>\<summary> (Visual Basic)

指定成員的摘要。  
  
## <a name="syntax"></a>語法  
  
```xml  
<summary>description</summary>  
```  
  
## <a name="parameters"></a>參數  

 `description`  
 物件的摘要。  
  
## <a name="remarks"></a>備註  

 使用 `<summary>` 標記來描述類型或類型成員。 使用將 [\<remarks>](remarks.md) 補充資訊加入至類型描述。  
  
 標記的文字 `<summary>` 是 IntelliSense 中型別的唯一資訊來源，也會顯示在物件瀏覽器中。 如需物件瀏覽器的詳細資訊，請參閱 [查看程式碼結構](/visualstudio/ide/viewing-the-structure-of-code)。  
  
 使用 [-doc](../../reference/command-line-compiler/doc.md) 進行編譯，以處理檔批註至檔案。  
  
## <a name="example"></a>範例  

 此範例會使用 `<summary>` 標記來描述 `ResetCounter` 方法和 `Counter` 屬性。  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [XML 註解標籤](index.md)

---
title: <summary>
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 893ed299b46bd6255ca0e87d008ac53265698614
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411495"
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
  
 標記的文字 `<summary>` 是 IntelliSense 中類型的唯一資訊來源，也會顯示在物件瀏覽器中。 如需物件瀏覽器的相關資訊，請參閱[查看程式碼的結構](/visualstudio/ide/viewing-the-structure-of-code)。  
  
 使用[-doc](../../reference/command-line-compiler/doc.md)進行編譯，以處理檔案的檔批註。  
  
## <a name="example"></a>範例  
 這個範例會使用 `<summary>` 標記來描述 `ResetCounter` 方法和 `Counter` 屬性。  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [XML 註解標籤](index.md)

---
title: <returns>
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: 37b110cc6e12f11196d2a1c5cc6026d87b453626
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866414"
---
# <a name="returns-visual-basic"></a>\<returns> (Visual Basic)

指定屬性或函數的傳回值。  
  
## <a name="syntax"></a>語法  
  
```xml  
<returns>description</returns>  
```  
  
## <a name="parameters"></a>參數  

 `description`  
 傳回值的描述。  
  
## <a name="remarks"></a>備註  

 使用方法宣告的 `<returns>` 批註中的標記來描述傳回值。  
  
 使用 [-doc](../../reference/command-line-compiler/doc.md) 進行編譯，以處理檔批註至檔案。  
  
## <a name="example"></a>範例  

 此範例會使用 `<returns>` 標記來說明函式傳回的內容 `DoesRecordExist` 。  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>另請參閱

- [XML 註解標籤](index.md)

---
title: <example>
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 6e9f63e4d31df7790f51ae4d166b606f2c63f14b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872982"
---
# <a name="example-visual-basic"></a>\<example> (Visual Basic)

指定成員的範例。  
  
## <a name="syntax"></a>語法  
  
```xml  
<example>description</example>  
```  
  
## <a name="parameters"></a>參數  

 `description`  
 程式碼範例的描述。  
  
## <a name="remarks"></a>備註  

 `<example>`標記可讓您指定如何使用方法或其他程式庫成員的範例。 這通常牽涉到使用 [\<code>](code.md) 標記。  
  
 使用 [-doc](../../reference/command-line-compiler/doc.md) 進行編譯，以處理檔批註至檔案。  
  
## <a name="example"></a>範例  

 此範例會使用 `<example>` 標記來包含使用欄位的範例 `ID` 。  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>另請參閱

- [XML 註解標籤](index.md)

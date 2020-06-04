---
title: <example>
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 42f40581d252956433165789d6674234a295867c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400135"
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
  
 使用[-doc](../../reference/command-line-compiler/doc.md)進行編譯，以處理檔案的檔批註。  
  
## <a name="example"></a>範例  
 這個範例會使用 `<example>` 標記來包含使用欄位的範例 `ID` 。  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>另請參閱

- [XML 註解標籤](index.md)

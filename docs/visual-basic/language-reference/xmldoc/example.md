---
title: <example> （Visual Basic）
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 8f28dbf19bc03cb9d91323e9fa43a7081c1990db
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524013"
---
# <a name="example-visual-basic"></a>\<example > （Visual Basic）
指定成員的範例。  
  
## <a name="syntax"></a>語法  
  
```xml  
<example>description</example>  
```  
  
## <a name="parameters"></a>參數  
 `description`  
 程式碼範例的描述。  
  
## <a name="remarks"></a>備註  
 @No__t_0 標記可讓您指定如何使用方法或其他程式庫成員的範例。 這通常需要使用 [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) 標記。  
  
 使用 [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) 編譯可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
 這個範例會使用 `<example>` 標記來包含使用 `ID` 欄位的範例。  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>請參閱

- [XML 註解標記](../../../visual-basic/language-reference/xmldoc/index.md)

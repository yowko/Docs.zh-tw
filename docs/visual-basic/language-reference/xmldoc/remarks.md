---
title: <remarks>
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: b327e548bcdce1522a888855bd88e3150695147b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352253"
---
# <a name="remarks-visual-basic"></a>\<remarks> (Visual Basic)
Specifies a remarks section for the member.  
  
## <a name="syntax"></a>語法  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a>參數  
 `description`  
 成員的描述。  
  
## <a name="remarks"></a>備註  
 Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md).  
  
 This information appears in the Object Browser. For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).  
  
 使用 [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) 編譯可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
 This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>請參閱

- [XML 註解標記](../../../visual-basic/language-reference/xmldoc/index.md)

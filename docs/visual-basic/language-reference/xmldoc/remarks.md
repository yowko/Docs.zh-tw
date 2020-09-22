---
title: <remarks>
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: 70078752495240ab8c72fe1bbecdca554166fb22
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866427"
---
# <a name="remarks-visual-basic"></a>\<remarks> (Visual Basic)

指定成員的備註區段。  
  
## <a name="syntax"></a>語法  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a>參數  

 `description`  
 成員的描述。  
  
## <a name="remarks"></a>備註  

 您 `<remarks>` 可以使用標記來新增類型的相關資訊，以補充以指定的資訊 [\<summary>](summary.md) 。  
  
 這項資訊會出現在 [物件瀏覽器] 中。 如需物件瀏覽器的詳細資訊，請參閱 [查看程式碼結構](/visualstudio/ide/viewing-the-structure-of-code)。  
  
 使用 [-doc](../../reference/command-line-compiler/doc.md) 進行編譯，以處理檔批註至檔案。  
  
## <a name="example"></a>範例  

 此範例會使用 `<remarks>` 標記來說明方法的用途 `UpdateRecord` 。  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>另請參閱

- [XML 註解標籤](index.md)

---
title: <code>
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: aa65fed863718f1f00b510f82051a13e764e1b23
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400136"
---
# <a name="code-visual-basic"></a>\<code> (Visual Basic)
表示文字是多行程式碼。  
  
## <a name="syntax"></a>語法  
  
```xml  
<code>content</code>  
```  
  
## <a name="parameters"></a>參數  
 `content`  
 要標示為程式碼的文字。  
  
## <a name="remarks"></a>備註  
 使用 `<code>` 標記，將多行指定為程式碼。 用 [\<c>](c.md) 來表示描述中的文字應該標記為程式碼。  
  
 使用[-doc](../../reference/command-line-compiler/doc.md)進行編譯，以處理檔案的檔批註。  
  
## <a name="example"></a>範例  
 這個範例會使用 \<code> 標記來包含使用欄位的範例程式碼 `ID` 。  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>另請參閱

- [XML 註解標籤](index.md)

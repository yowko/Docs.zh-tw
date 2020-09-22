---
title: <code>
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: d058663213cf02f2142bff740aeec1b60791362c
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873023"
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

 使用 `<code>` 標記以程式碼表示多行。 用 [\<c>](c.md) 來表示描述中的文字應標示為程式碼。  
  
 使用 [-doc](../../reference/command-line-compiler/doc.md) 進行編譯，以處理檔批註至檔案。  
  
## <a name="example"></a>範例  

 此範例會使用 \<code> 標記來包含使用欄位的範例程式碼 `ID` 。  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>另請參閱

- [XML 註解標籤](index.md)

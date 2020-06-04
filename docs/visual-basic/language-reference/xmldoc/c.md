---
title: <c>
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: c8ba03d9cc01c4751d15c01530c6cbf7d499dc3b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400159"
---
# <a name="c-visual-basic"></a>\<c> (Visual Basic)
表示描述中的文字是程式碼。  
  
## <a name="syntax"></a>語法  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a>參數  
  
|參數|說明|  
|---|---|  
|`text`|您要指定為程式碼的文字。|  
  
## <a name="remarks"></a>備註  
 `<c>`標記可讓您指定描述中的文字應該標記為程式碼。 用 [\<code>](code.md) 來指示多行作為程式碼。  
  
 使用[-doc](../../reference/command-line-compiler/doc.md)進行編譯，以處理檔案的檔批註。  
  
## <a name="example"></a>範例  
 這個範例會使用 `<c>` [摘要] 區段中的標記，來表示 `Counter` 是程式碼。  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [XML 註解標籤](index.md)

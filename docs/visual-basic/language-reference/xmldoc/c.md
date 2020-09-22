---
title: <c>
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 969df339eb766d2edb444ab5626af4e69accddba
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871708"
---
# <a name="c-visual-basic"></a>\<c> (Visual Basic)

表示描述中的文字為程式碼。  
  
## <a name="syntax"></a>語法  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a>參數  
  
|參數|Description|  
|---|---|  
|`text`|您要指定為程式碼的文字。|  
  
## <a name="remarks"></a>備註  

 `<c>`標記可讓您表示描述中的文字應標示為程式碼。 用 [\<code>](code.md) 來指出多行程式碼。  
  
 使用 [-doc](../../reference/command-line-compiler/doc.md) 進行編譯，以處理檔批註至檔案。  
  
## <a name="example"></a>範例  

 此範例會使用 `<c>` [摘要] 區段中的標記，指出這 `Counter` 是程式碼。  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [XML 註解標籤](index.md)

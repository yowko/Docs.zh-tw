---
title: <code>
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: 1cbac2162bd39cdc8af9a55dfd6e2f90bc40b08a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354316"
---
# <a name="code-visual-basic"></a>\<程式碼 > （Visual Basic）
表示文字是多行程式碼。  
  
## <a name="syntax"></a>語法  
  
```xml  
<code>content</code>  
```  
  
## <a name="parameters"></a>參數  
 `content`  
 要標示為程式碼的文字。  
  
## <a name="remarks"></a>備註  
 使用 `<code>` 標記，將多行指定為程式碼。 [\<c>](../../../visual-basic/language-reference/xmldoc/c.md) 則用來指出在一段描述中應該標記為程式碼的文字。  
  
 使用 [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) 編譯可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
 這個範例會使用 \<的程式碼 > 標記，以包含使用 [`ID`] 欄位的範例程式碼。  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>另請參閱

- [XML 註解標記](../../../visual-basic/language-reference/xmldoc/index.md)

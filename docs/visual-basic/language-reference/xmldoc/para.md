---
title: <para>
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: 0e2051d1b00b881c06082b3af483890d8595899f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400069"
---
# <a name="para-visual-basic"></a>\<para> (Visual Basic)
指定將內容格式化為段落。  
  
## <a name="syntax"></a>語法  
  
```xml  
<para>content</para>  
```  
  
## <a name="parameters"></a>參數  
 `content`  
 段落的文字。  
  
## <a name="remarks"></a>備註  
 `<para>`標記用於標記內（例如 [\<summary>](summary.md) 、 [\<remarks>](remarks.md) 或 [\<returns>](returns.md) ），並可讓您將結構新增至文字。  
  
 使用[-doc](../../reference/command-line-compiler/doc.md)進行編譯，以處理檔案的檔批註。  
  
## <a name="example"></a>範例  
 這個範例會使用 `<para>` 標記，將方法的備註區段分割 `UpdateRecord` 成兩個段落。  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>另請參閱

- [XML 註解標籤](index.md)

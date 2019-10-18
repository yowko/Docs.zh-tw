---
title: <para> （Visual Basic）
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: aa4e4c14717b69b9ca4595e20c768a2b91aac1e4
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524735"
---
# <a name="para-visual-basic"></a>\<para > （Visual Basic）
指定將內容格式化為段落。  
  
## <a name="syntax"></a>語法  
  
```xml  
<para>content</para>  
```  
  
## <a name="parameters"></a>參數  
 `content`  
 段落的文字。  
  
## <a name="remarks"></a>備註  
 @No__t_0 標記是用於標記內（例如[\<summary >](../../../visual-basic/language-reference/xmldoc/summary.md)、 [\<remarks >](../../../visual-basic/language-reference/xmldoc/remarks.md)或[\<returns >](../../../visual-basic/language-reference/xmldoc/returns.md)），並可讓您將結構新增至文字。  
  
 使用 [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) 編譯可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
 這個範例會使用 `<para>` 標記，將 `UpdateRecord` 方法的備註區段分割成兩個段落。  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>請參閱

- [XML 註解標記](../../../visual-basic/language-reference/xmldoc/index.md)

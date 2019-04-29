---
title: <returns> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: 5a0ff0da7cf26a1cea75a5b2e4678593d9b72f54
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940786"
---
# <a name="returns-visual-basic"></a>\<傳回 > (Visual Basic)
指定屬性或函式的傳回值。  
  
## <a name="syntax"></a>語法  
  
```xml  
<returns>description</returns>  
```  
  
## <a name="parameters"></a>參數  
 `description`  
 傳回值的描述。  
  
## <a name="remarks"></a>備註  
 使用`<returns>`標記來描述傳回值的方法宣告的註解中。  
  
 編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
 這個範例會使用`<returns>`標記來解釋什麼`DoesRecordExist`函式會傳回。  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>另請參閱

- [XML 註解標記](../../../visual-basic/language-reference/xmldoc/index.md)

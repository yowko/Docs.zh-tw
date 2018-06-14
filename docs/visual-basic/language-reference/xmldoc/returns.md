---
title: '&lt;傳回&gt;(Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: effc55bd65ae6c54575b7931529499505a9523cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33598361"
---
# <a name="ltreturnsgt-visual-basic"></a>&lt;傳回&gt;(Visual Basic)
指定屬性或函式的傳回值。  
  
## <a name="syntax"></a>語法  
  
```xml  
<returns>description</returns>  
```  
  
#### <a name="parameters"></a>參數  
 `description`  
 傳回值的描述。  
  
## <a name="remarks"></a>備註  
 使用`<returns>`標記來描述傳回值的方法宣告的註解中。  
  
 編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
 這個範例會使用`<returns>`標記加入至說明`DoesRecordExist`函式會傳回。  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/returns_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [XML 註解標記](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)

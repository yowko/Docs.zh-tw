---
title: '&lt;typeparam&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: 73ffb1319e6724a13a80b3cd1ca6985e4cbac05c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54567057"
---
# <a name="lttypeparamgt-visual-basic"></a>&lt;typeparam&gt; (Visual Basic)
定義的型別參數名稱和描述。  
  
## <a name="syntax"></a>語法  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
#### <a name="parameters"></a>參數  
 `name`  
 型別參數的名稱。 以雙引號 (" ") 括住名稱。  
  
 `description`  
 型別參數的描述。  
  
## <a name="remarks"></a>備註  
 使用`<typeparam>`泛型類型或泛型成員宣告來描述的其中一個類型參數的註解中的標記。  
  
 編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
 這個範例會使用`<typeparam>`標記來描述`id`參數。  
  
 [!code-vb[VbVbcnXmlDocComments#8](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/typeparam_1.vb)]  
  
## <a name="see-also"></a>另請參閱
- [XML 註解標記](../../../visual-basic/language-reference/xmldoc/index.md)

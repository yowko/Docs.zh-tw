---
title: "&lt;param&gt; (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 41852a7fc41595050940d87f9e741df5cb23361c
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="ltparamgt-visual-basic"></a>&lt;param&gt; (Visual Basic)
定義的參數名稱和描述。  
  
## <a name="syntax"></a>語法  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a>參數  
 `name`  
 方法參數的名稱。 將名稱括在雙引號 ("")。  
  
 `description`  
 參數的描述。  
  
## <a name="remarks"></a>備註  
 `<param>`標記應使用於方法宣告的註解來描述的其中一個方法參數。  
  
 文字`<param>`標記會出現在下列位置︰  
  
-   IntelliSense 的參數資訊。 如需詳細資訊，請參閱[使用 IntelliSense](https://docs.microsoft.com/visualstudio/ide/using-intellisense)。  
  
-   物件瀏覽器。 如需詳細資訊，請參閱[檢視程式碼的結構](https://docs.microsoft.com/visualstudio/ide/viewing-the-structure-of-code)。  
  
 使用編譯[/doc](../../../visual-basic/reference/command-line-compiler/doc.md)程序至檔案的文件註解。  
  
## <a name="example"></a>範例  
 這個範例會使用`<param>`標記，來說明`id`參數。  
  
 [!code-vb[VbVbcnXmlDocComments #&6;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/param_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [XML 註解標記](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)

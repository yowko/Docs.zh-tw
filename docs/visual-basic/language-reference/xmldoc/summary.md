---
title: "&lt;摘要&gt;(Visual Basic) |Microsoft 文件"
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
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
caps.latest.revision: 12
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ad2053e21e58c49205fe869a484cb2dffd2169ee
ms.lasthandoff: 03/13/2017

---
# <a name="ltsummarygt-visual-basic"></a>&lt;摘要&gt;(Visual Basic)
指定成員的摘要。  
  
## <a name="syntax"></a>語法  
  
```  
<summary>description</summary>  
```  
  
#### <a name="parameters"></a>參數  
 `description`  
 物件的摘要。  
  
## <a name="remarks"></a>備註  
 使用`<summary>`標記，來說明型別或型別成員。 使用[\<註解 >](../../../visual-basic/language-reference/xmldoc/remarks.md)加入類型描述的補充資訊。  
  
 文字`<summary>`標記是唯一的來源中的 IntelliSense，類型的相關資訊，也會顯示在 物件瀏覽器。 物件瀏覽器的相關資訊，請參閱[檢視程式碼結構](https://docs.microsoft.com/visualstudio/ide/viewing-the-structure-of-code)。  
  
 使用編譯[/doc](../../../visual-basic/reference/command-line-compiler/doc.md)程序至檔案的文件註解。  
  
## <a name="example"></a>範例  
 這個範例會使用`<summary>`標記，來說明`ResetCounter`方法和`Counter`屬性。  
  
 [!code-vb[VbVbcnXmlDocComments #&1;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/summary_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [XML 註解標記](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)

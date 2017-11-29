---
title: "屬性 &#39;&lt;attributename&gt;&#39; 無法套用多次"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords: BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 216cf54fd164ca95b6378517a679b5b54183559f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="attribute-39ltattributenamegt39-cannot-be-applied-multiple-times"></a>屬性 &#39;&lt;attributename&gt;&#39; 無法套用多次
屬性只能套用一次。 `AttributeUsage`屬性會決定是否可以多次套用屬性。  
  
 **錯誤 ID:** BC30663  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請確定屬性只能套用一次。  
  
2.  如果您使用的您開發的自訂屬性，請考慮變更其`AttributeUsage`屬性，以允許多個屬性使用方式，如同下列範例。  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.AttributeUsageAttribute>  
 [建立自訂屬性](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [AttributeUsage](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)

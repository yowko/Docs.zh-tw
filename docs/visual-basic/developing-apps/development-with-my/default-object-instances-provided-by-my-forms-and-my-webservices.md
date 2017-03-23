---
title: "Default Object Instances Provided by My.Forms and My.WebServices (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My.WebServices object, developing applications"
  - "My.Forms object, developing applications"
  - "rapid application development (RAD), My.Forms"
  - "rapid application development (RAD), My.WebServices"
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
caps.latest.revision: 5
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 5
---
# Default Object Instances Provided by My.Forms and My.WebServices (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

[My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md) 和 [My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md) 物件會提供對應用程式所使用之表單、資料來源和 XML Web Service 的存取。  它們是透過提供這些物件之「*預設執行個體*」\(Default Instance\) 的集合達成此目的。  
  
## 預設執行個體  
 預設執行個體是執行階段所提供之類別的執行個體，而且不需要使用 `Dim` 和 `New` 陳述式進行宣告及執行個體化。  下列範例將示範過去如何宣告及執行個體化稱為 `Form1` 之 <xref:System.Windows.Forms.Form> 類別的執行個體，以及現在如何透過 `My.Forms` 取得這個 <xref:System.Windows.Forms.Form> 類別的執行個體。  
  
 [!code-vb[VbVbcnMy#5](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/default-object-instances-provided-by-my-forms-and-my-webservices_1.vb)]  
  
 [!code-vb[VbVbcnMy#6](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/default-object-instances-provided-by-my-forms-and-my-webservices_2.vb)]  
  
 `My.Forms` 物件會針對專案中存在的每個 `Form` 類別，傳回預設執行個體的集合。  同樣地，`My.WebServices` 會針對在應用程式中建立參考的每個 Web 服務，提供 Proxy 類別的預設執行個體。  
  
## 請參閱  
 [My.Forms Object](../../../visual-basic/language-reference/objects/my-forms-object.md)   
 [My.WebServices Object](../../../visual-basic/language-reference/objects/my-webservices-object.md)   
 [How My Depends on Project Type](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
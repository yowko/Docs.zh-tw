---
title: "Accessing Application Web Services (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Web services, My.WebServices object"
  - "My.WebServices object"
  - "applications [Visual Basic], Web services"
ms.assetid: 8ad5405b-e771-42b1-82d3-ce97af2cea9e
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# Accessing Application Web Services (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

`My.WebServices` 物件會提供目前專案所參考之每個 Web 服務的執行個體。  每個執行個體都會視需要執行個體化。  您可以透過 `My.WebServices` 物件的屬性 \(Property\) 存取這些 Web 服務。  屬性名稱會與屬性所存取的 Web 服務名稱相同。  任何繼承自 <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> 的類別 \(Class\) 都是 Web 服務。  
  
## 工作  
 下表會列出用於存取應用程式所參考之 Web 服務的可能方法。  
  
|||  
|-|-|  
|若要|請參閱|  
|呼叫 Web 服務|[My.WebServices Object](../../../visual-basic/language-reference/objects/my-webservices-object.md)|  
|非同步呼叫 Web 服務並於完成時處理事件|[How to: Call a Web Service Asynchronously](../../../visual-basic/developing-apps/programming/how-to-call-a-web-service-asynchronously.md)|  
  
## 請參閱  
 [My.WebServices Object](../../../visual-basic/language-reference/objects/my-webservices-object.md)
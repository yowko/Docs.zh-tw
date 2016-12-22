---
title: "Accessing User Data (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "domain names, retrieving"
  - "data [Visual Basic], accessing user data"
  - "My.User object, tasks"
  - "user data, domain"
  - "user names, retrieving"
  - "user data, accessing"
  - "login names"
  - "examples [Visual Basic], accessing user data"
ms.assetid: 32492a15-ee59-4a63-a1f1-9b24cc13140a
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Accessing User Data (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

本章節涵蓋有關 `My.User` 物件與使用此物件可以完成之工作的主題。  
  
 `My.User` 物件會傳回實作 <xref:System.Security.Principal.IPrincipal> 介面的物件，藉以提供存取已登入的使用者之相關資訊的權限。  
  
## 工作  
  
|若要|請參閱|  
|--------|---------|  
|取得使用者的登入名稱|<xref:Microsoft.VisualBasic.ApplicationServices.User.Name%2A>|  
|取得使用者的網域名稱 \(如果應用程式使用 Windows 驗證\)|<xref:Microsoft.VisualBasic.ApplicationServices.User.CurrentPrincipal>|  
|判斷使用者的角色|<xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A>|  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.ApplicationServices.User>
---
title: "How to: Read Application Settings in Visual Basic | Microsoft Docs"
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
  - "reading application settings"
  - "My.Settings object, reading application settings"
  - "application settings, reading"
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Read Application Settings in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

您可以存取 `My.Settings` 物件上的設定屬性 \(Property\)，藉以讀取使用者設定。  
  
 `My.Settings` 物件將每個設定公開為屬性。  屬性名稱與設定名稱相同，並且屬性型別也與設定型別相同。  此設定的 \[**範圍**\] 會判斷屬性是否為 read\-only。如果 \[**使用者**\] 範圍設定的屬性為 read\-write，則 \[**應用程式**\] 範圍設定的屬性為 read\-only。  如需詳細資訊，請參閱[My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md)。  
  
## 範例  
 這個範例會顯示 `Nickname` 設定的值。  
  
 [!code-vb[VbVbalrMyResources#14](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-read-application-settings_1.vb)]  
  
 如果要使這個範例能夠運作，您的應用程式必須具有型別為 `String` 的 `Nickname` 設定。  如需詳細資訊，請參閱[管理應用程式設定 \(.NET\)](/visual-studio/ide/managing-application-settings-dotnet)。  
  
## 請參閱  
 [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md)   
 [How to: Change User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)   
 [How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)   
 [How to: Create Property Grids for User Settings in Visual Basic](../Topic/How%20to:%20Create%20Property%20Grids%20for%20User%20Settings%20in%20Visual%20Basic.md)   
 [管理應用程式設定 \(.NET\)](/visual-studio/ide/managing-application-settings-dotnet)
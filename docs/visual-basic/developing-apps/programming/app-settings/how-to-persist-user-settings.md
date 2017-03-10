---
title: "How to: Persist User Settings in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My.Settings object, persisting user settings"
  - "persistence, persisting user settings [Visual Basic]"
  - "user settings, persisting"
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# How to: Persist User Settings in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

您可以使用 `My.Settings.Save` 方法，保存使用者設定的變更。  
  
 通常應用程式是設計為在關閉應用程式時，保存使用者設定的變更。  這是因為儲存變更可能要花數秒鐘的時間，視各種因素而定。  
  
 如需詳細資訊，請參閱[My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md)。  
  
> [!NOTE]
>  雖然您可以在執行階段變更和儲存使用者範圍設定的值，但是應用程式範圍的設定為唯讀，且無法以程式設計方式變更。  當建立應用程式時，您可以透過 \[**專案設計工具**\]，或藉由編輯應用程式的組態檔，以變更應用程式範圍的設定。  如需詳細資訊，請參閱[管理應用程式設定 \(.NET\)](/visual-studio/ide/managing-application-settings-dotnet)。  
  
## 範例  
 這個範例會變更 `LastChanged` 使用者設定的值，然後呼叫 `My.Settings.Save` 方法儲存該變更。  
  
 [!code-vb[VbVbalrMyResources#5](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/visualbasic/VbVbalrMyResources2/Form1.vb#5)]  
  
 若要成功使用這個範例，您的應用程式必須具有型別為 `Date` 的 `LastChanged` 使用者設定。  如需詳細資訊，請參閱[管理應用程式設定 \(.NET\)](/visual-studio/ide/managing-application-settings-dotnet)。  
  
## 請參閱  
 [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md)   
 [How to: Read Application Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)   
 [How to: Change User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)   
 [How to: Create Property Grids for User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)   
 [管理應用程式設定 \(.NET\)](/visual-studio/ide/managing-application-settings-dotnet)
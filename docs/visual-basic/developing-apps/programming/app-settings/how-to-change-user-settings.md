---
title: "How to: Change User Settings in Visual Basic | Microsoft Docs"
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
  - "user settings, changing in Visual Basic"
  - "user settings"
  - "My.Settings object, changing user settings"
  - "examples [Visual Basic], changing user settings"
ms.assetid: 41250181-c594-4854-9988-8183b9eb03cf
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# How to: Change User Settings in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

您可以指派新值給 `My.Settings` 物件的設定屬性 \(Property\)，藉以變更使用者設定。  
  
 `My.Settings` 物件將每個設定公開為屬性。  屬性名稱與設定名稱相同，並且屬性型別也與設定型別相同。  此設定的 \[**範圍**\] 會判斷屬性是否為 read\-only。若 \[**使用者**\] 範圍設定的屬性為 read\-write，則 \[**應用程式**\] 範圍設定的屬性為 read\-only。  如需詳細資訊，請參閱[My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md)。  
  
> [!NOTE]
>  雖然您可以在執行階段變更和儲存使用者範圍設定的值，但是應用程式範圍的設定為唯讀，且無法以程式設計方式變更。  當您建立應用程式時，可以使用 \[**專案設計工具**\]，或編輯應用程式的組態檔，以變更應用程式範圍的設定。  如需詳細資訊，請參閱[管理應用程式設定 \(.NET\)](/visual-studio/ide/managing-application-settings-dotnet)。  
  
## 範例  
 這個範例會變更 `Nickname` 使用者設定的值。  
  
 [!code-vb[VbVbalrMyResources#7](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-change-user-settings_1.vb)]  
  
 如果要使這個範例能夠運作，您的應用程式必須具有型別為 `String` 的 `Nickname` 使用者設定。  
  
 應用程式關閉時，會儲存使用者設定。  若要立即儲存設定值，請呼叫 `My.Settings.Save` 方法。  如需詳細資訊，請參閱[How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)。  
  
## 請參閱  
 [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md)   
 [How to: Read Application Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)   
 [How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)   
 [How to: Create Property Grids for User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)   
 [管理應用程式設定 \(.NET\)](/visual-studio/ide/managing-application-settings-dotnet)
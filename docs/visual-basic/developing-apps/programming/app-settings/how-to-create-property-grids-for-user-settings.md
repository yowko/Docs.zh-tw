---
title: "How to: Create Property Grids for User Settings in Visual Basic | Microsoft Docs"
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
  - "My.Settings object, creating property grids for user settings"
  - "user settings, creating property grids"
  - "property grids, creating for user settings"
  - "property grids"
ms.assetid: b0bc737e-50d1-43d1-a6df-268db6e6f91c
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# How to: Create Property Grids for User Settings in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

您可以使用 `My.Settings` 物件的使用者設定屬性，填入 <xref:System.Windows.Forms.PropertyGrid> 控制項，以建立使用者設定值的屬性方格。  
  
> [!NOTE]
>  為了讓此範例能夠運作，您的應用程式必須設定它的使用者設定值。  如需詳細資訊，請參閱[管理應用程式設定 \(.NET\)](/visual-studio/ide/managing-application-settings-dotnet)。  
  
 `My.Settings` 物件將每個設定公開為屬性。  屬性名稱與設定名稱相同，並且屬性型別也與設定型別相同。  此設定的 \[**範圍**\] 會判斷屬性是否為 read\-only。若 \[**使用者**\]\-範圍設定的屬性為 read\-write，則 \[**應用程式**\]\-範圍設定的屬性為 read\-only。  如需詳細資訊，請參閱[My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md)。  
  
> [!NOTE]
>  在執行階段不可變更或儲存應用程式範圍的設定值。  只有在建立應用程式時，或藉由編輯應用程式的組態檔，才能變更應用程式範圍的設定值 \(經由 \[**專案設計工具**\]\)。  如需詳細資訊，請參閱[管理應用程式設定 \(.NET\)](/visual-studio/ide/managing-application-settings-dotnet)。  
  
 這個範例會使用 <xref:System.Windows.Forms.PropertyGrid> 控制項，存取 `My.Settings` 物件的使用者設定屬性。  根據預設，<xref:System.Windows.Forms.PropertyGrid> 會顯示 `My.Settings` 物件的所有屬性。  不過，使用者設定屬性 \(Property\) 具有 <xref:System.Configuration.UserScopedSettingAttribute> 屬性 \(Attribute\)。  這個範例會將 <xref:System.Windows.Forms.PropertyGrid> 的 <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> 屬性設定為 <xref:System.Configuration.UserScopedSettingAttribute>，僅顯示使用者設定屬性。  
  
### 若要加入使用者設定屬性方格  
  
1.  請在 \[**工具箱**\] 中，將 \[**PropertyGrid**\] 控制項加入至應用程式的設計介面，此處會假設為 `Form1`。  
  
     屬性方格控制項的預設名稱為 `PropertyGrid1`。  
  
2.  按兩下 `Form1` 的設計介面，以開啟表單載入事件處理常式的程式碼。  
  
3.  將 `My.Settings` 物件設定為屬性方格的選取物件。  
  
     [!code-vb[VbVbalrMyResources#11](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/visualbasic/VbVbalrMyResources2/Form1.vb#11)]  
  
4.  將屬性方格設定為僅顯示使用者設定。  
  
     [!code-vb[VbVbalrMyResources#12](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/visualbasic/VbVbalrMyResources2/Form1.vb#12)]  
  
    > [!NOTE]
    >  若只要顯示應用程式範圍的設定，請使用 <xref:System.Configuration.ApplicationScopedSettingAttribute> 屬性而不是 <xref:System.Configuration.UserScopedSettingAttribute>。  
  
## 穩固程式設計  
 應用程式關閉時，會儲存使用者設定。  若要立即儲存設定值，請呼叫 `My.Settings.Save` 方法。  如需詳細資訊，請參閱[How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)。  
  
## 請參閱  
 [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md)   
 [How to: Read Application Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)   
 [How to: Change User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)   
 [How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)   
 [管理應用程式設定 \(.NET\)](/visual-studio/ide/managing-application-settings-dotnet)
---
title: "如何：在 Visual Basic 中建立使用者設定的屬性方格 | Microsoft Docs"
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
- My.Settings object, creating property grids for user settings
- user settings, creating property grids
- property grids, creating for user settings
- property grids
ms.assetid: b0bc737e-50d1-43d1-a6df-268db6e6f91c
caps.latest.revision: 13
author: stevehoag
ms.author: shoag
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 17fab50b0f95bacd12d7044ec95c6cef2453d250
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-property-grids-for-user-settings-in-visual-basic"></a>如何：在 Visual Basic 中建立使用者設定的屬性方格
您可以使用 `My.Settings` 物件的使用者設定屬性填入 <xref:System.Windows.Forms.PropertyGrid> 控制項，以建立使用者設定的屬性方格。  
  
> [!NOTE]
>  為了確保此範例正常運作，您的應用程式必須已設定其使用者設定。 如需詳細資訊，請參閱[管理應用程式設定 (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-settings-dotnet)。  
  
 `My.Settings` 物件會將每個設定公開為屬性。 屬性名稱與設定名稱相同，而屬性類型與設定類型相同。 設定的 [範圍]**** 可判斷屬性是否為唯讀；[應用程式]**** 範圍設定的屬性為唯讀，而 [使用者]**** 範圍設定的屬性為讀寫。 如需詳細資訊，請參閱 [My.Settings 物件](../../../../visual-basic/language-reference/objects/my-settings-object.md)。  
  
> [!NOTE]
>  您無法在執行階段變更或儲存應用程式範圍設定的值。 只有在建立應用程式時 (透過 [專案設計工具]****或藉由編輯應用程式的組態檔)，才能變更應用程式範圍的設定。 如需詳細資訊，請參閱[管理應用程式設定 (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-settings-dotnet)。  
  
 此範例會使用 <xref:System.Windows.Forms.PropertyGrid> 控制項來存取 `My.Settings` 物件的使用者設定屬性。 根據預設，<xref:System.Windows.Forms.PropertyGrid> 會顯示 `My.Settings` 物件的所有屬性。 不過，使用者設定屬性 (Property) 具有 <xref:System.Configuration.UserScopedSettingAttribute> 屬性 (Attribute)。 此範例會將 <xref:System.Windows.Forms.PropertyGrid> 的 <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> 屬性設定為 <xref:System.Configuration.UserScopedSettingAttribute>，只顯示使用者設定屬性。  
  
### <a name="to-add-a-user-setting-property-grid"></a>新增使用者設定屬性方格  
  
1.  將 **PropertyGrid** 控制項從 [工具箱]**** 新增至應用程式 (此處假設為 `Form1`) 的設計介面。  
  
     屬性方格控制項的預設名稱為 `PropertyGrid1`。  
  
2.  按兩下 `Form1` 的設計介面，以開啟表單載入事件處理常式的程式碼。  
  
3.  將 `My.Settings` 物件設定為屬性方格的選取物件。  
  
     [!code-vb[VbVbalrMyResources#11](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-create-property-grids-for-user-settings_1.vb)]  
  
4.  將屬性方格設定為只顯示使用者設定。  
  
     [!code-vb[VbVbalrMyResources#12](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-create-property-grids-for-user-settings_2.vb)]  
  
    > [!NOTE]
    >  若只要顯示應用程式範圍的設定，請使用 <xref:System.Configuration.ApplicationScopedSettingAttribute> 屬性而不是 <xref:System.Configuration.UserScopedSettingAttribute>。  
  
## <a name="robust-programming"></a>穩固程式設計  
 應用程式關閉時，會儲存使用者設定。 若要立即儲存設定，請呼叫 `My.Settings.Save` 方法。 如需詳細資訊，請參閱[如何：保存 Visual Basic 中的使用者設定](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)。  
  
## <a name="see-also"></a>另請參閱  
 [My.Settings 物件](../../../../visual-basic/language-reference/objects/my-settings-object.md)   
 [如何：在 Visual Basic 中讀取應用程式設定](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)   
 [如何：在 Visual Basic 中變更使用者設定](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)   
 [如何：保存 Visual Basic 中的使用者設定](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)   
 [管理應用程式設定 (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-settings-dotnet)

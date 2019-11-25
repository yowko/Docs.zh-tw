---
title: My.Settings 物件
ms.date: 07/20/2015
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
ms.openlocfilehash: 9560a51332ea596d4cf2228f1e07c158a0457ece
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350350"
---
# <a name="mysettings-object"></a>My.Settings 物件
Provides properties and methods for accessing the application's settings.  
  
## <a name="remarks"></a>備註  
 The `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application. 如需詳細資訊，請參閱[管理應用程式設定 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)。  
  
## <a name="properties"></a>內容  
 `My.Settings` 物件的屬性可存取您應用程式的設定。 To add or remove settings, use the **Settings Designer**.  
  
 Each setting has a **Name**, **Type**, **Scope**, and **Value**, and these settings determine how the property to access each setting appears in the `My.Settings` object:  
  
- **Name** determines the name of the property.  
  
- **Type** determines the type of the property.  
  
- **Scope** indicates if the property is read-only. If the value is **Application**, the property is read-only; if the value is **User**, the property is read-write.  
  
- **Value** is the default value of the property.  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|---|---|  
|`Reload`|Reloads the user settings from the last saved values.|  
|`Save`|Saves the current user settings.|  
  
 The `My.Settings` object also provides advanced properties and methods, inherited from the <xref:System.Configuration.ApplicationSettingsBase> class.  
  
## <a name="tasks"></a>工作  
 The following table lists examples of tasks involving the `My.Settings` object.  
  
|若要|請參閱|  
|---|---|  
|Read an application setting|[如何：在 Visual Basic 中讀取應用程式設定](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|Change a user setting|[如何：在 Visual Basic 中變更使用者設定](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|Persist user settings|[如何：保存 Visual Basic 中的使用者設定](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|Create a property grid for user settings|[如何：在 Visual Basic 中建立使用者設定的屬性方格](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a>範例  
 此範例會顯示 `Nickname` 設定的值。  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 為了確保此範例正常運作，您的應用程式必須具有 `String` 類型的 `Nickname` 設定。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Configuration.ApplicationSettingsBase>
- [如何：在 Visual Basic 中讀取應用程式設定](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [如何：在 Visual Basic 中變更使用者設定](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [如何：保存 Visual Basic 中的使用者設定](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [如何：在 Visual Basic 中建立使用者設定的屬性方格](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [管理應用程式設定 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)

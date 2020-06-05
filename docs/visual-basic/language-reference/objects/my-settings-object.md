---
title: My.Settings 物件
ms.date: 07/20/2015
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
ms.openlocfilehash: c905ff85c8e9729dd4d6068f0d34f729962bbb57
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372397"
---
# <a name="mysettings-object"></a>My.Settings 物件
提供用來存取應用程式設定的屬性和方法。  
  
## <a name="remarks"></a>備註  
 `My.Settings`物件可讓您存取應用程式的設定，並可讓您以動態方式儲存和抓取應用程式的屬性設定和其他資訊。 如需詳細資訊，請參閱[管理應用程式設定 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)。  
  
## <a name="properties"></a>屬性  
 `My.Settings` 物件的屬性可存取您應用程式的設定。 若要新增或移除設定，請使用 [**設定設計**工具]。  
  
 每個設定都有 [**名稱**]、[**類型**]、[**範圍**] 和 [**值**]，而這些設定會決定要如何存取每個設定的屬性會出現在 `My.Settings` 物件中：  
  
- **名稱**決定屬性的名稱。  
  
- **類型**決定屬性的類型。  
  
- **範圍**指出屬性是否為唯讀。 如果值為**Application**，則屬性為唯讀;如果值為**User**，則屬性為讀寫。  
  
- **Value**是屬性的預設值。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|---|---|  
|`Reload`|從上次儲存的值重載使用者設定。|  
|`Save`|儲存目前的使用者設定。|  
  
 `My.Settings`物件也提供繼承自類別的先進屬性和方法 <xref:System.Configuration.ApplicationSettingsBase> 。  
  
## <a name="tasks"></a>工作  
 下表列出涉及物件的工作範例 `My.Settings` 。  
  
|至|請參閱|  
|---|---|  
|讀取應用程式設定|[如何：在 Visual Basic 中讀取應用程式設定](../../developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|變更使用者設定|[如何：在 Visual Basic 中變更使用者設定](../../developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|保存使用者設定|[如何：保存 Visual Basic 中的使用者設定](../../developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|建立使用者設定的屬性方格|[如何：在 Visual Basic 中建立使用者設定的屬性方格](../../developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a>範例  
 此範例會顯示 `Nickname` 設定的值。  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 為了確保此範例正常運作，您的應用程式必須具有 `String` 類型的 `Nickname` 設定。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Configuration.ApplicationSettingsBase>
- [如何：在 Visual Basic 中讀取應用程式設定](../../developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [如何：在 Visual Basic 中變更使用者設定](../../developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [如何：保存 Visual Basic 中的使用者設定](../../developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [如何：在 Visual Basic 中建立使用者設定的屬性方格](../../developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [管理應用程式設定 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)

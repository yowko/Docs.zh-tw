---
title: "My.Settings 物件 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
dev_langs:
- VB
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
caps.latest.revision: 16
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d48d3556f55ef286e2f501e2df5bf5035d3aff90
ms.lasthandoff: 03/13/2017

---
# <a name="mysettings-object"></a>My.Settings 物件
提供屬性和方法來存取應用程式的設定。  
  
## <a name="remarks"></a>備註  
 `My.Settings`物件提供應用程式的設定存取權，並可讓您動態儲存和擷取屬性設定和應用程式的其他資訊。 如需詳細資訊，請參閱[管理應用程式設定 (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-settings-dotnet)。  
  
## <a name="properties"></a>屬性  
 屬性的`My.Settings`物件提供存取您的應用程式設定。 若要新增或移除設定，使用**設定設計工具**。  
  
 每個設定**名稱**，**類型**，**範圍**，和**值**，以及這些設定會決定要存取的每個設定的屬性會出現在`My.Settings`物件︰  
  
-   **名稱**判斷屬性的名稱。  
  
-   **型別**判斷屬性的型別。  
  
-   **範圍**指出屬性是否為唯讀。 如果值為**應用程式**，屬性是唯讀; 如果值為**使用者**，屬性是讀寫。  
  
-   **值**是屬性的預設值。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|---|---|  
|`Reload`|重新載入使用者設定從上次儲存的值。|  
|`Save`|儲存目前的使用者設定。|  
  
 `My.Settings`物件也會提供進階的屬性和方法，繼承自<xref:System.Configuration.ApplicationSettingsBase>類別。</xref:System.Configuration.ApplicationSettingsBase>  
  
## <a name="tasks"></a>工作  
 下表列出包含工作的範例`My.Settings`物件。  
  
|以|請參閱|  
|---|---|  
|讀取應用程式設定|[如何︰ 讀取 Visual Basic 中的應用程式設定](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|變更使用者設定|[如何︰ 變更 Visual Basic 中的使用者設定](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|保存使用者設定|[如何︰ 保存 Visual Basic 中的使用者設定](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|建立使用者設定的屬性方格|[如何︰ 建立 Visual Basic 中的使用者設定的屬性方格](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a>範例  
 此範例中顯示的值`Nickname`設定。  
  
 [!code-vb[VbVbalrMyResources #&14;](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-settings-object_1.vb)]  
  
 為了讓範例能夠運作，您的應用程式必須`Nickname`類型設定`String`。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Configuration.ApplicationSettingsBase></xref:System.Configuration.ApplicationSettingsBase>   
 [如何︰ 讀取 Visual Basic 中的應用程式設定](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)   
 [如何︰ 變更 Visual Basic 中的使用者設定](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)   
 [如何︰ 保存 Visual Basic 中的使用者設定](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)   
 [如何︰ 建立 Visual Basic 中的使用者設定的屬性方格](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)   
 [管理應用程式設定 (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-settings-dotnet)

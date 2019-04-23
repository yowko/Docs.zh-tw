---
title: HOW TO：在 Visual Basic 中建立使用者設定的屬性方格
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], creating property grids for user settings
- user settings [Visual Basic], creating property grids
- property grids [Visual Basic], creating for user settings
- property grids
ms.assetid: b0bc737e-50d1-43d1-a6df-268db6e6f91c
ms.openlocfilehash: 5f4b962762aeecea65748c5456bc4a2d75595d4f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59311613"
---
# <a name="how-to-create-property-grids-for-user-settings-in-visual-basic"></a>HOW TO：在 Visual Basic 中建立使用者設定的屬性方格
您可以使用 `My.Settings` 物件的使用者設定屬性填入 <xref:System.Windows.Forms.PropertyGrid> 控制項，以建立使用者設定的屬性方格。  
  
> [!NOTE]
>  為了確保此範例正常運作，您的應用程式必須已設定其使用者設定。 如需詳細資訊，請參閱[管理應用程式設定 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)。  
  
 `My.Settings` 物件會將每項設定公開為屬性。 屬性名稱與設定名稱相同，而屬性類型與設定類型相同。 設定的 [範圍] 可判斷屬性是否為唯讀；[應用程式] 範圍設定的屬性為唯讀，而 [使用者] 範圍設定的屬性為讀寫。 如需詳細資訊，請參閱 [My.Settings 物件](../../../../visual-basic/language-reference/objects/my-settings-object.md)。  
  
> [!NOTE]
>  您無法在執行階段變更或儲存應用程式範圍設定的值。 只有在建立應用程式時 (透過 [專案設計工具]或藉由編輯應用程式的組態檔)，才能變更應用程式範圍的設定。 如需詳細資訊，請參閱[管理應用程式設定 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)。  
  
 此範例會使用 <xref:System.Windows.Forms.PropertyGrid> 控制項來存取 `My.Settings` 物件的使用者設定屬性。 <xref:System.Windows.Forms.PropertyGrid> 預設會顯示 `My.Settings` 物件的所有屬性。 不過，使用者設定屬性有 <xref:System.Configuration.UserScopedSettingAttribute> 屬性。 此範例會將 <xref:System.Windows.Forms.PropertyGrid> 的 <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> 屬性設定為 <xref:System.Configuration.UserScopedSettingAttribute> 以只顯示使用者設定屬性。  
  
### <a name="to-add-a-user-setting-property-grid"></a>新增使用者設定屬性方格  
  
1. 將 PropertyGrid 控制項從 [工具箱] 新增至應用程式 (此處假設為 `Form1`) 的設計介面。  
  
     屬性方格控制項的預設名稱為 `PropertyGrid1`。  
  
2. 按兩下 `Form1` 的設計介面，以開啟表單載入事件處理常式的程式碼。  
  
3. 將 `My.Settings` 物件設定為屬性方格的選取物件。  
  
     [!code-vb[VbVbalrMyResources#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#11)]  
  
4. 將屬性方格設定為只顯示使用者設定。  
  
     [!code-vb[VbVbalrMyResources#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#12)]  
  
    > [!NOTE]
    >  若只要顯示應用程式範圍的設定，請使用 <xref:System.Configuration.ApplicationScopedSettingAttribute> 屬性而不是 <xref:System.Configuration.UserScopedSettingAttribute>。  
  
## <a name="robust-programming"></a>穩固程式設計  
 應用程式關閉時，會儲存使用者設定。 若要立即儲存設定，請呼叫 `My.Settings.Save` 方法。 如需詳細資訊，請參閱[如何：保存 Visual Basic 中的使用者設定](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)。  
  
## <a name="see-also"></a>另請參閱

- [My.Settings 物件](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [如何：在 Visual Basic 中讀取應用程式設定](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [如何：在 Visual Basic 中變更使用者設定](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [如何：保存 Visual Basic 中的使用者設定](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [管理應用程式設定 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)

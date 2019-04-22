---
title: HOW TO：保存 Visual Basic 中的使用者設定
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], persisting user settings
- persistence [Visual Basic], persisting user settings [Visual Basic]
- user settings [Visual Basic], persisting
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
ms.openlocfilehash: 35997db52a59aeaff5a2c404ea83b15639ea23a0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58825177"
---
# <a name="how-to-persist-user-settings-in-visual-basic"></a>HOW TO：保存 Visual Basic 中的使用者設定
您可以使用 `My.Settings.Save` 方法來保存使用者設定的變更。  
  
 通常，應用程式設計成在關閉應用程式時，保存使用者設定的變更。 這是因為儲存變更可能需要幾秒鐘的時間，視幾個因素而定。  
  
 如需詳細資訊，請參閱 [My.Settings 物件](../../../../visual-basic/language-reference/objects/my-settings-object.md)。  
  
> [!NOTE]
>  雖然您可以在執行階段變更和儲存使用者範圍設定的值，但是應用程式範圍的設定為唯讀，且無法以程式設計方式變更。 建立應用程式時，您可以透過 [專案設計工具]，或藉由編輯應用程式的組態檔，來變更應用程式範圍的設定。 如需詳細資訊，請參閱[管理應用程式設定 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)。  
  
## <a name="example"></a>範例  
 此範例會變更 `LastChanged` 使用者設定的值，然後呼叫 `My.Settings.Save` 方法儲存該變更。  
  
 [!code-vb[VbVbalrMyResources#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#5)]  
  
 為了確保此範例正常運作，您的應用程式必須具有 `Date` 類型的 `LastChanged` 使用者設定。 如需詳細資訊，請參閱[管理應用程式設定 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)。  
  
## <a name="see-also"></a>另請參閱

- [My.Settings 物件](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [如何：在 Visual Basic 中讀取應用程式設定](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [如何：在 Visual Basic 中變更使用者設定](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [如何：在 Visual Basic 中建立使用者設定的屬性方格](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [管理應用程式設定 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)

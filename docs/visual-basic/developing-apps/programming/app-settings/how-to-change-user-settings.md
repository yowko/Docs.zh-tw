---
title: 作法：在 Visual Basic 中變更使用者設定
ms.date: 07/20/2015
helpviewer_keywords:
- user settings [Visual Basic], changing in Visual Basic
- user settings
- My.Settings object [Visual Basic], changing user settings
- examples [Visual Basic], changing user settings
ms.assetid: 41250181-c594-4854-9988-8183b9eb03cf
ms.openlocfilehash: 553ebc5b0d6381f56783df8be83344f96a21dd8e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968410"
---
# <a name="how-to-change-user-settings-in-visual-basic"></a>作法：在 Visual Basic 中變更使用者設定
您可以將新值指派給 `My.Settings` 物件的設定屬性，來變更使用者設定。  
  
 `My.Settings` 物件會將每項設定公開為屬性。 屬性名稱與設定名稱相同，而屬性類型與設定類型相同。 設定的 [範圍]  可判斷屬性是否為唯讀：[應用程式]  範圍設定的屬性為唯讀，而 [使用者]  範圍設定的屬性為讀寫。 如需詳細資訊，請參閱 [My.Settings 物件](../../../../visual-basic/language-reference/objects/my-settings-object.md)。  
  
> [!NOTE]
> 雖然您可以在執行階段變更和儲存使用者範圍設定的值，但是應用程式範圍的設定為唯讀，且無法以程式設計方式變更。 建立應用程式時，您可以使用 [專案設計工具] 或編輯應用程式組態檔，來變更應用程式範圍的設定。  如需詳細資訊，請參閱[管理應用程式設定 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)。  
  
## <a name="example"></a>範例  
 這個範例會變更 `Nickname` 使用者設定的值。  
  
 [!code-vb[VbVbalrMyResources#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#7)]  
  
 為了確保此範例正常運作，您的應用程式必須具有 `String` 類型的 `Nickname` 使用者設定。  
  
 應用程式關閉時，會儲存使用者設定。 若要立即儲存設定，請呼叫 `My.Settings.Save` 方法。 如需詳細資訊，請參閱[如何：保存 Visual Basic 中的使用者設定](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)。  
  
## <a name="see-also"></a>另請參閱

- [My.Settings 物件](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [如何：在 Visual Basic 中讀取應用程式設定](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [如何：保存 Visual Basic 中的使用者設定](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [如何：在 Visual Basic 中建立使用者設定的屬性方格](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [管理應用程式設定 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)

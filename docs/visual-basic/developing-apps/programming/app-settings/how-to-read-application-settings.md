---
title: HOW TO：在 Visual Basic 中讀取應用程式設定
ms.date: 07/20/2015
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
ms.openlocfilehash: e7d909563ca7e991a51c2f921b5248aa587a83d7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58823580"
---
# <a name="how-to-read-application-settings-in-visual-basic"></a>HOW TO：在 Visual Basic 中讀取應用程式設定
您可以藉由存取 `My.Settings` 物件上的設定屬性，來讀取使用者設定。  
  
 `My.Settings` 物件會將每個設定公開為屬性。 屬性名稱與設定名稱相同，而屬性類型與設定類型相同。 設定的 [範圍] 指出屬性是否為唯讀；[應用程式] 範圍設定的屬性為唯讀，而 [使用者] 範圍設定的屬性為讀寫。 如需詳細資訊，請參閱 [My.Settings 物件](../../../../visual-basic/language-reference/objects/my-settings-object.md)。  
  
## <a name="example"></a>範例  
 此範例會顯示 `Nickname` 設定的值。  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 為了確保此範例正常運作，您的應用程式必須具有 `String` 類型的 `Nickname` 設定。 如需詳細資訊，請參閱[管理應用程式設定 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)。  
  
## <a name="see-also"></a>另請參閱

- [My.Settings 物件](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [如何：在 Visual Basic 中變更使用者設定](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [如何：保存 Visual Basic 中的使用者設定](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [如何：在 Visual Basic 中建立使用者設定的屬性方格](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [管理應用程式設定 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)

---
title: "如何：保存 Visual Basic 中的使用者設定 | Microsoft Docs"
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
- My.Settings object, persisting user settings
- persistence, persisting user settings [Visual Basic]
- user settings, persisting
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 53fc5bd08265e4eb28a8bc6a8a145c50d662c494
ms.contentlocale: zh-tw
ms.lasthandoff: 05/24/2017

---
# <a name="how-to-persist-user-settings-in-visual-basic"></a>如何：保存 Visual Basic 中的使用者設定
您可以使用 `My.Settings.Save` 方法來保存使用者設定的變更。  
  
 通常，應用程式設計成在關閉應用程式時，保存使用者設定的變更。 這是因為儲存變更可能需要幾秒鐘的時間，視幾個因素而定。  
  
 如需詳細資訊，請參閱 [My.Settings 物件](../../../../visual-basic/language-reference/objects/my-settings-object.md)。  
  
> [!NOTE]
>  雖然您可以在執行階段變更和儲存使用者範圍設定的值，但是應用程式範圍的設定為唯讀，且無法以程式設計方式變更。 建立應用程式時，您可以透過 [專案設計工具]，或藉由編輯應用程式的組態檔，來變更應用程式範圍的設定。 如需詳細資訊，請參閱[管理應用程式設定 (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-settings-dotnet)。  
  
## <a name="example"></a>範例  
 此範例會變更 `LastChanged` 使用者設定的值，然後呼叫 `My.Settings.Save` 方法儲存該變更。  
  
 [!code-vb[VbVbalrMyResources#5](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-persist-user-settings_1.vb)]  
  
 為了確保此範例正常運作，您的應用程式必須具有 `Date` 類型的 `LastChanged` 使用者設定。 如需詳細資訊，請參閱[管理應用程式設定 (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-settings-dotnet)。  
  
## <a name="see-also"></a>另請參閱  
 [My.Settings 物件](../../../../visual-basic/language-reference/objects/my-settings-object.md)   
 [如何：在 Visual Basic 中讀取應用程式設定](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)   
 [如何：在 Visual Basic 中變更使用者設定](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)   
 [如何：在 Visual Basic 中建立使用者設定的屬性方格](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)   
 [管理應用程式設定 (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-settings-dotnet)

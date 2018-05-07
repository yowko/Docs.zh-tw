---
title: 使用 My.Resources 和 My.Settings 進行快速應用程式開發 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
ms.openlocfilehash: 808e02510d4f0a237ad4354b2edac8fa024b5f83
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a>使用 My.Resources 和 My.Settings 進行快速應用程式開發 (Visual Basic)
`My.Resources`物件提供的應用程式資源的存取權，並可讓您以動態方式擷取您的應用程式的資源。  
  
## <a name="retrieving-resources"></a>擷取資源  
 可以透過擷取的資源，例如音訊檔案、 圖示、 影像和字串的數字`My.Resources`物件。 例如，您可以存取應用程式的特定文化特性資源檔。 下列範例會設定表單的圖示的圖示，名為`Form1Icon`儲存應用程式的資源檔案。  
  
 [!code-vb[VbVbcnMy#7](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/rapid-application-development-with-my-resources-and-my-settings_1.vb)]  
  
 `My.Resources`物件會公開只有全域資源。 它不提供與表單相關聯的資源檔案的存取權。 您必須在表單中存取的表單資源。  
  
 同樣地，`My.Settings`物件存取應用程式的設定，並可讓您動態儲存及擷取屬性設定和應用程式的其他資訊。 如需詳細資訊，請參閱[My.Resources 物件](../../../visual-basic/language-reference/objects/my-resources-object.md)和[My.Settings 物件](../../../visual-basic/language-reference/objects/my-settings-object.md)。  
  
## <a name="see-also"></a>另請參閱  
 [My.Resources 物件](../../../visual-basic/language-reference/objects/my-resources-object.md)  
 [My.Settings 物件](../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [存取應用程式設定](../../../visual-basic/developing-apps/programming/app-settings/accessing-application-settings.md)

---
title: 使用 My.Resources 和 My.Settings 進行快速應用程式開發 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
ms.openlocfilehash: 4a9021af23200323397cc49fa1a44a0cc48b5a1d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58816703"
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a>使用 My.Resources 和 My.Settings 進行快速應用程式開發 (Visual Basic)
`My.Resources`物件來存取應用程式的資源，而且可讓您以動態方式擷取您的應用程式的資源。  
  
## <a name="retrieving-resources"></a>擷取資源  
 可以透過擷取幾個資源，例如音訊檔案、 圖示、 影像和字串的`My.Resources`物件。 例如，您可以存取應用程式的特定文化特性資源檔。 下列範例會將名為圖示表單的圖示`Form1Icon`儲存在應用程式的資源檔。  
  
 [!code-vb[VbVbcnMy#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#7)]  
  
 `My.Resources`物件會公開僅有全域資源。 它不提供與表單相關聯的資源檔案的存取權。 您必須從表單來存取表單資源。  
  
 同樣地，`My.Settings`物件可讓您存取應用程式的設定，並可讓您以動態方式儲存及擷取屬性設定和應用程式的其他資訊。 如需詳細資訊，請參閱 < [My.Resources 物件](../../../visual-basic/language-reference/objects/my-resources-object.md)並[My.Settings 物件](../../../visual-basic/language-reference/objects/my-settings-object.md)。  
  
## <a name="see-also"></a>另請參閱

- [My.Resources 物件](../../../visual-basic/language-reference/objects/my-resources-object.md)
- [My.Settings 物件](../../../visual-basic/language-reference/objects/my-settings-object.md)
- [存取應用程式設定](../../../visual-basic/developing-apps/programming/app-settings/index.md)

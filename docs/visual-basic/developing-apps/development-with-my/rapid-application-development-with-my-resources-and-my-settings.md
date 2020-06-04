---
title: 使用 My.Resources 及 my.settings 加快開發應用程式的速度
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
ms.openlocfilehash: 6c53d11a3830a5a8a2cb898728bed8694a226686
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411664"
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a>使用 My.Resources 和 My.Settings 進行快速應用程式開發 (Visual Basic)

`My.Resources`物件提供應用程式資源的存取權，並可讓您以動態方式取得應用程式的資源。  
  
## <a name="retrieving-resources"></a>擷取資源  

 您可以透過物件來抓取一些資源，例如音訊檔案、圖示、影像和字串 `My.Resources` 。 例如，您可以存取應用程式的特定文化特性資源檔。 下列範例會將表單的圖示設定為 `Form1Icon` 應用程式資源檔中所儲存的圖示。  
  
 [!code-vb[VbVbcnMy#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#7)]  
  
 `My.Resources`物件只會公開全域資源。 它不會提供與表單相關聯之資源檔的存取權。 您必須從表單存取表單資源。  
  
 同樣地， `My.Settings` 物件也會提供應用程式設定的存取權，並可讓您動態儲存和抓取應用程式的屬性設定和其他資訊。 如需詳細資訊，請參閱[My .Resources 物件](../../language-reference/objects/my-resources-object.md)和[My. Settings 物件](../../language-reference/objects/my-settings-object.md)。  
  
## <a name="see-also"></a>另請參閱

- [My.Resources 物件](../../language-reference/objects/my-resources-object.md)
- [My.Settings 物件](../../language-reference/objects/my-settings-object.md)
- [Accessing Application Settings](../programming/app-settings/index.md)

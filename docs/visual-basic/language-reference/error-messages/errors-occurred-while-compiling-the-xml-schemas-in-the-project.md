---
title: 編譯專案中的 XML 結構描述時發生錯誤
ms.date: 07/20/2015
f1_keywords:
- bc36810
- vbc36810
helpviewer_keywords:
- BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
ms.openlocfilehash: 17c31301e28c757954e72ba103254f038905671f
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874357"
---
# <a name="errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a>編譯專案中的 XML 結構描述時發生錯誤

編譯專案中的 XML 架構時發生錯誤。 因此，無法使用 XML IntelliSense。  
  
 專案中包含 (XSD) 架構的 XML 架構定義發生錯誤。 當您加入 XSD 架構 ( .xsd) 檔案，且該檔案與專案的現有 XSD 架構集發生衝突時，就會發生這個錯誤。  
  
 **錯誤識別碼：** BC36810  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 按兩下 [ **錯誤清單** ] 視窗中的警告。 Visual Basic 會帶您前往 XSD 檔案中的位置，這是警告的來源。 更正 XSD 架構中的錯誤。  
  
- 確定所有必要的 XSD 架構 ( .xsd) 檔案都包含在專案中。 您可能需要按一下 [**專案**] 功能表上的 [**顯示所有**檔案]，才能在**方案總管**中查看 .xsd 檔。 以滑鼠右鍵按一下 .xsd 檔案，然後按一下 [ **包含在專案中** ]，將檔案包含在您的專案中。  
  
- 如果您使用 XML to Schema Wizard，則如果您從相同的來源推斷出一次以上的架構，就會發生此錯誤。 在此情況下，您可以從專案中移除現有的 XSD 架構檔案、將新的 XML 新增至架構專案範本，然後為 XML 提供適用于您專案的所有適用 XML 來源的 [XML 至架構]。  
  
- 如果 XSD 架構中找不到錯誤，XML 編譯器可能沒有足夠的資訊來提供詳細的錯誤訊息。 如果您確定專案中包含之 .xsd 檔的 XML 命名空間符合 Visual Studio 中設定之 XML 架構所識別的 XML 命名空間，您可能可以取得更詳細的錯誤資訊。  
  
## <a name="see-also"></a>另請參閱

- [錯誤清單視窗](/visualstudio/ide/reference/error-list-window)
- [XML](../../programming-guide/language-features/xml/index.md)

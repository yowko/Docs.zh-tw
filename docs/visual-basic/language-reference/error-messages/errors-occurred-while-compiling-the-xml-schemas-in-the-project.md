---
title: 編譯專案中的 XML 結構描述時發生錯誤
ms.date: 07/20/2015
f1_keywords:
- bc36810
- vbc36810
helpviewer_keywords:
- BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
ms.openlocfilehash: 0cc565809792c619ca9903f9ef9b029b51a8aa17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588258"
---
# <a name="errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a>編譯專案中的 XML 結構描述時發生錯誤
編譯專案中的 XML 結構描述時發生錯誤。 因為這個緣故，則無法使用 XML IntelliSense。  
  
 在 XML 結構描述定義 (XSD) 結構描述中包含在專案中有錯誤。 當您將加入專案中設定與現有的 XSD 結構描述衝突的 XSD 結構描述 (.xsd) 檔案，就會發生此錯誤。  
  
 **錯誤 ID:** BC36810  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   按兩下警告中的**錯誤清單**視窗。 Visual Basic 會帶您前往來源警告的 XSD 檔中的位置。 更正的 XSD 結構描述中的錯誤。  
  
-   請確定所有必要的 XSD 結構描述 (.xsd) 檔案會包含在專案中。 您可能需要按一下**顯示所有檔案**上**專案**中的檔案 功能表，查看您.xsd**方案總管 中**。 以滑鼠右鍵按一下.xsd 檔案，然後按一下**包含在專案**以您的專案中包含的檔案。  
  
-   如果您使用 XML to Schema 精靈時，如果您從相同來源推斷結構描述一次以上，就可以會發生這個錯誤。 在此情況下，您可以移除現有的 XSD 結構描述檔案從專案中，加入新的 XML 結構描述項目範本，然後再提供 XML to Schema 精靈與所有適用的 XML 來源專案。  
  
-   如果在 XSD 結構描述中不發現任何錯誤，XML 編譯器可能沒有足夠的資訊來提供詳細的錯誤訊息。 您可以取得更詳細的錯誤資訊，如果您確定.xsd 檔案的 XML 命名空間中包含您專案的相符項目識別為 Visual Studio 中設定的 XML 結構描述的 XML 命名空間。  
  
## <a name="see-also"></a>另請參閱  
 [錯誤清單視窗](/visualstudio/ide/reference/error-list-window)  
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)

---
title: "編譯專案中的 XML 結構描述時發生錯誤 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36810
- vbc36810
dev_langs:
- VB
helpviewer_keywords:
- BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
caps.latest.revision: 11
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: cf04e85da98db53d1c78269169571936f708cd21
ms.lasthandoff: 03/13/2017

---
# <a name="errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a>編譯專案中的 XML 結構描述時發生錯誤
編譯專案中的 XML 結構描述時發生錯誤。 因為這個緣故，XML IntelliSense 無法使用。  
  
 包含在專案中的 XML 結構描述定義 (XSD) 結構描述中沒有錯誤。 當您將加入專案中設定與現有的 XSD 結構描述衝突的 XSD 結構描述 (.xsd) 檔案，就會發生此錯誤。  
  
 **錯誤識別碼︰** BC36810  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   按兩下警告中的**錯誤清單**視窗。 Visual Basic 會帶您前往來源警告的 XSD 檔中的位置。 更正 XSD 結構描述中的錯誤。  
  
-   請確定所有必要的 XSD 結構描述 (.xsd) 檔案包含在專案中。 您可能需要按一下**顯示所有檔案**上**專案**中的檔案 功能表上，若要查看您.xsd**方案總管 中**。 以滑鼠右鍵按一下.xsd 檔案，然後按一下**加入至專案**將檔案併入專案中。  
  
-   如果您使用 XML to Schema 精靈時，如果您從相同來源推斷結構描述一次以上，就可以會發生這個錯誤。 在此情況下，您可以從專案移除現有的 XSD 結構描述檔案加入新的 XML 結構描述項目範本，然後再提供 XML 結構描述精靈與所有適用的 XML 來源專案。  
  
-   如果您的 XSD 結構描述中沒有識別任何錯誤，XML 編譯器可能沒有足夠的資訊來提供詳細的錯誤訊息。 您可以取得更詳細的錯誤資訊，如果您確定為.xsd 檔的 XML 命名空間包含在專案的比對識別 Visual Studio 中設定的 XML 結構描述的 XML 命名空間。  
  
## <a name="see-also"></a>另請參閱  
 [錯誤清單視窗](https://docs.microsoft.com/visualstudio/ide/reference/error-list-window)   
 [在 Visual Basic 中的 XML IntelliSense](../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)   
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)

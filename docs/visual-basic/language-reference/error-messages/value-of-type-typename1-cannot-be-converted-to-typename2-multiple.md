---
title: 類型 '<typename1>' 的值無法轉換成 '<typename2>' (多重檔案參考)
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: 58b334eb5e6db443bcfaba72729d59cb1d798e70
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833525"
---
# <a name="value-of-type-typename1-cannot-be-converted-to-typename2-multiple-file-references"></a>類型的值 '\<typename1 >' 無法轉換成'\<2&gt >' （多重檔案參考）
類型的值 '\<typename1 >' 無法轉換成'\<2&gt >'。 類型不相符可能是因為混用的檔案參考 '\<filepath1 >' 在專案'\<projectname1 >' 的檔案參考 '\<filepath2 >' 在專案'\<專案名稱 2> >'。 如果兩個組件相同，請嘗試更換這些參考，讓兩個參考都來自相同的位置。  
  
 其中一個專案可多個檔案參考的組件的情況下，編譯器無法保證一個類型可轉換成另一個。  
  
 每個檔案參考指定的檔案路徑和專案 （通常是 DLL 檔案） 的輸出檔名稱。 編譯器無法保證輸出檔案來自相同的來源，或它們代表相同的組件的相同版本。 因此，它無法保證在不同的參考類型都是相同的類型，，或甚至是其中一個可以轉換成其他。  
  
 如果您知道所參考組件有相同的組件識別，您可以使用單一檔案參考。 *「組件識別」* (assembly identity) 包含組件的名稱、版本、公開金鑰 (如果有) 和文化特性。 這是可唯一識別組件的資訊。  
  
 **錯誤 ID:** BC30961  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   如果參考的組件有相同的組件識別，然後移除或取代檔案參考的其中一個，以便只包含單一檔案的參考。  
  
-   如果參考的組件沒有相同的組件識別，然後變更您的程式碼，使它不會嘗試在其他類型的其中一個類型轉換。  
  
## <a name="see-also"></a>另請參閱

- [在 Visual Basic 中的類型轉換](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [管理專案中的參考](/visualstudio/ide/managing-references-in-a-project)

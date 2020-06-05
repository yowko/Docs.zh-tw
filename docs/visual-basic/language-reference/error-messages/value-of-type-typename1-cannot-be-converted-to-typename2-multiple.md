---
title: 類型 '<typename1>' 的值無法轉換成 '<typename2>' (多重檔案參考)
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: 25008f05979638e050b74fc659fdc0a6d13b3c31
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406582"
---
# <a name="value-of-type-typename1-cannot-be-converted-to-typename2-multiple-file-references"></a>類型 '\<typename1>' 的值無法轉換成 '\<typename2>' (多重檔案參考)
類型 ' ' 的值 \<typename1> 無法轉換成 ' \<typename2> '。 類型不符的原因可能是因為在專案 ' ' 中混用 ' ' 的檔案參考 \<filepath1> \<projectname1> 與 \<filepath2> 專案 ' ' 中 ' ' 的檔案參考 \<projectname2> 。 如果兩個組件相同，請嘗試更換這些參考，讓兩個參考都來自相同的位置。  
  
 在專案對元件進行多個檔案參考的情況下，編譯器無法保證一個類型可以轉換成另一個。  
  
 每個檔案參考都會指定專案輸出檔的檔案路徑和名稱（通常是 DLL 檔案）。 編譯器無法保證輸出檔案來自相同的來源，或其代表相同元件的相同版本。 因此，它無法保證不同參考中的類型都是相同的類型，甚至是可以轉換成另一個。  
  
 如果您知道參考的元件具有相同的元件識別，您可以使用單一檔案參考。 *元件識別*包含元件的名稱、版本、公開金鑰（如果有）和文化特性。 這是可唯一識別組件的資訊。  
  
 **錯誤識別碼：** BC30961  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 如果參考的元件具有相同的元件識別，則請移除或取代其中一個檔案參考，讓只有一個檔案參考。  
  
- 如果參考的元件不具有相同的元件識別，請變更您的程式碼，使其不會嘗試將某個類型轉換成另一個中的類型。  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的類型轉換](../../programming-guide/language-features/data-types/type-conversions.md)
- [管理專案中的參考](/visualstudio/ide/managing-references-in-a-project)

---
title: 類型 '<typename1>' 的值無法轉換成 '<typename2>' (多重檔案參考)
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: 4b74fdc5584fd296d4bbe36034920d4b467dbb7a
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875065"
---
# <a name="value-of-type-typename1-cannot-be-converted-to-typename2-multiple-file-references"></a>類型 '\<typename1>' 的值無法轉換成 '\<typename2>' (多重檔案參考)

類型 ' ' 的值 \<typename1> 無法轉換成 ' \<typename2> '。 類型不符的原因可能是混合 \<filepath1> 專案 ' ' 中的 ' ' 檔案參考 \<projectname1> 與專案 ' ' 中的 ' \<filepath2> ' 檔案參考 \<projectname2> 。 如果兩個組件相同，請嘗試更換這些參考，讓兩個參考都來自相同的位置。  
  
 在專案對元件建立多個檔案參考的情況下，編譯器無法保證可以將一個類型轉換成另一個類型。  
  
 每個檔案參考都會指定專案輸出檔的檔案路徑和名稱， (通常是) 的 DLL 檔案。 編譯器無法保證輸出檔來自相同的來源，或者它們代表相同元件的相同版本。 因此，它無法保證不同參考中的型別是相同類型，或甚至可以轉換成另一個參考。  
  
 如果您知道參考的元件具有相同的元件識別，則可以使用單一檔案參考。 *元件身分識別*包含元件的名稱、版本、公開金鑰（如果有）和文化特性。 這是可唯一識別組件的資訊。  
  
 **錯誤識別碼：** BC30961  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 如果參考的元件具有相同的元件識別，則請移除或取代其中一個檔案參考，如此就只會有單一檔案參考。  
  
- 如果參考的元件沒有相同的元件識別，則請變更您的程式碼，使其不會嘗試將某個類型轉換成另一個類型。  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的類型轉換](../../programming-guide/language-features/data-types/type-conversions.md)
- [管理專案中的參考](/visualstudio/ide/managing-references-in-a-project)

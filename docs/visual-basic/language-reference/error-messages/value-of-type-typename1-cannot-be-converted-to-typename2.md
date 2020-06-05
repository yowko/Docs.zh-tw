---
title: 類型 '<typename1>' 的值無法轉換成 '<typename2>'
ms.date: 07/20/2015
f1_keywords:
- vbc30955
- bc30955
helpviewer_keywords:
- BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
ms.openlocfilehash: f6b35efbc445887c537b94dd299b317a28e5f689
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406556"
---
# <a name="value-of-type-typename1-cannot-be-converted-to-typename2"></a>類型 '\<typename1>' 的值無法轉換成 '\<typename2>'
類型 ' ' 的值 \<typename1> 無法轉換成 ' \<typename2> '。 類型不符的原因可能是混合了檔案參考與元件 ' ' 的專案參考 \<assemblyname> 。 請嘗試將專案 ' ' 中 ' ' 的檔案參考取代為 \<filepath> \<projectname1> ' ' 的專案參考 \<projectname2> 。  
  
 在專案同時做為專案參考和檔案參考的情況下，編譯器無法保證一個型別可以轉換成另一個類型。  
  
 下列虛擬程式碼說明可能會產生此錯誤的情況。  
  
 `' ================ Visual Basic project P1 ================`  
  
 `'        P1 makes a PROJECT REFERENCE to project P2`  
  
 `'        and a FILE REFERENCE to project P3.`  
  
 `Public commonObject As P3.commonClass`  
  
 `commonObject = P2.getCommonClass()`  
  
 `' ================ Visual Basic project P2 ================`  
  
 `'        P2 makes a PROJECT REFERENCE to project P3`  
  
 `Public Function getCommonClass() As P3.commonClass`  
  
 `Return New P3.commonClass`  
  
 `End Function`  
  
 `' ================ Visual Basic project P3 ================`  
  
 `Public Class commonClass`  
  
 `End Class`  
  
 Project `P1` 會透過專案對專案進行間接專案參考 `P2` `P3` ，同時也會直接參考的檔案 `P3` 。 的宣告會 `commonObject` 使用的檔案參考 `P3` ，而呼叫會 `P2.getCommonClass` 使用的專案參考 `P3` 。  
  
 這種情況的問題在於，檔案參考指定了（通常是 p3）輸出檔的檔案路徑和名稱 `P3` ，而專案參考則是依專案名稱識別來源專案（ `P3` ）。 因此，編譯器無法保證類型會 `P3.commonClass` 透過兩個不同的參考來自相同的原始程式碼。  
  
 當專案參考和檔案參考混合時，通常就會發生這種情況。 在上圖中，如果 `P1` 直接進行專案參考，而不是檔案參考，就不會發生此問題 `P3` 。  
  
 **錯誤識別碼：** BC30955  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 將檔案參考變更為專案參考。  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的類型轉換](../../programming-guide/language-features/data-types/type-conversions.md)
- [管理專案中的參考](/visualstudio/ide/managing-references-in-a-project)

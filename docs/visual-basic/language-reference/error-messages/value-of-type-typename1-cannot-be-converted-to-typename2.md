---
title: 類型 '<typename1>' 的值無法轉換成 '<typename2>'
ms.date: 07/20/2015
f1_keywords:
- vbc30955
- bc30955
helpviewer_keywords:
- BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
ms.openlocfilehash: 5f313a43bc3a2f983dabbd45477d120fdb80d063
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58829016"
---
# <a name="value-of-type-typename1-cannot-be-converted-to-typename2"></a>類型的值 '\<typename1 >' 無法轉換成'\<2&gt >'
類型的值 '\<typename1 >' 無法轉換成'\<2&gt >'。 型別不相符可能是因為混用了檔案參考和組件的專案參考的 '\<組件名稱 >'。 請嘗試更換的檔案參考 '\<檔案路徑 >' 在專案'\<projectname1 >' 的專案參考 '\<專案名稱 2> >'。  
  
 其中一個專案可專案參考和檔案參考的情況下，編譯器無法保證一個類型可轉換成另一個。  
  
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
  
 專案`P1`會透過專案間接的專案參考`P2`專案`P3`，和也直接與檔案參考`P3`。 宣告`commonObject`使用的檔案參考`P3`，而呼叫`P2.getCommonClass`使用的專案參考`P3`。  
  
 在此情況下問題就是檔案參考指定的檔案路徑與名稱的輸出檔案`P3`(通常 p3.dll)，在專案參考中找到的原始碼專案時 (`P3`) 依專案名稱。 因此，編譯器無法保證類型`P3.commonClass`來自相同的原始程式碼，透過兩個不同的參考。  
  
 通常會發生這種情況在混合的檔案參考和專案的參考時。 在上圖中，就不會發生問題如果`P1`所做的直接存取的專案參考`P3`而非檔案參考。  
  
 **錯誤 ID:** BC30955  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   變更的專案參考的檔案參考。  
  
## <a name="see-also"></a>另請參閱

- [在 Visual Basic 中的類型轉換](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [管理專案中的參考](/visualstudio/ide/managing-references-in-a-project)

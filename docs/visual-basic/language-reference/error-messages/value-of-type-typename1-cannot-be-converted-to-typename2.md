---
title: 類型 '<typename1>' 的值無法轉換成 '<typename2>'
ms.date: 07/20/2015
f1_keywords:
- vbc30955
- bc30955
helpviewer_keywords:
- BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
ms.openlocfilehash: a4aab83fd5695633a660eab00a5032ffbe45f326
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161318"
---
# <a name="bc30955-value-of-type-typename1-cannot-be-converted-to-typename2"></a>BC30955：類型 ' ' 的值 \<typename1> 無法轉換成 ' \<typename2> '

類型 ' ' 的值 \<typename1> 無法轉換成 ' \<typename2> '。 類型不符的原因可能是混合檔案參考與元件 ' ' 的專案參考 \<assemblyname> 。 請嘗試將專案 ' ' 中的 ' ' 檔案參考取代為 \<filepath> \<projectname1> ' ' 的專案參考 \<projectname2> 。

 在專案同時建立專案參考和檔案參考的情況下，編譯器無法保證某個類型可以轉換成另一個類型。

 下列虛擬程式碼說明可能會產生此錯誤的狀況。

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

 Project `P1` 會透過專案對專案進行間接專案參考 `P2` `P3` ，以及的直接檔案參考 `P3` 。 的宣告會 `commonObject` 使用的檔案參考 `P3` ，而的呼叫會 `P2.getCommonClass` 使用的專案參考 `P3` 。

 在這種情況下的問題是，檔案參考會為 (的輸出檔指定檔案路徑和名稱 `P3` ，通常是 p3.dll) ，而專案參考則是 `P3` 依專案名稱來識別來源專案 () 。 因此，編譯器無法保證類型會 `P3.commonClass` 透過兩個不同的參考來自相同的原始程式碼。

 當專案參考和檔案參考混合時，通常就會發生這種情況。 在上圖中，如果 `P1` 直接參考專案，而不是檔案參考，則不會發生此問題 `P3` 。

 **錯誤識別碼：** BC30955

## <a name="to-correct-this-error"></a>更正這個錯誤

- 將檔案參考變更為專案參考。

## <a name="see-also"></a>另請參閱

- [Visual Basic 中的類型轉換](../../programming-guide/language-features/data-types/type-conversions.md)
- [管理專案中的參考](/visualstudio/ide/managing-references-in-a-project)

---
title: 堆疊空間用盡
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: afb6a42372bdbd2e49ac15fbbf2b9e254f8db431
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871318"
---
# <a name="out-of-stack-space-visual-basic"></a>堆疊空間不足 (Visual Basic)

堆疊是記憶體的工作區域，會隨著執行程式的需求動態增加和縮減。 已超過其限制。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 檢查程式是否太深。  
  
2. 請確定遞迴程式會正常終止。  
  
3. 如果區域變數需要的本機變數空間超過可用的數目，請嘗試在模組層級宣告一些變數。 您也可以在 `Property` 、或關鍵字前面加上，將程式中的所有變數宣告 `Sub` `Function` 為靜態 `Static` 。 或者，您可以使用 `Static` 語句來宣告程式中的個別靜態變數。  
  
4. 將部分固定長度的字串重新定義為可變長度的字串，因為固定長度的字串使用的堆疊空間比可變長度的字串多。 您也可以在模組層級定義不需要任何堆疊空間的字串。  
  
5. 檢查嵌套 `DoEvents` 函式呼叫的數目，方法是使用 `Calls` 對話方塊來查看堆疊上的作用中程式。  
  
6. 藉由觸發呼叫已在堆疊上之事件程式的事件，確定您未產生「事件串聯」。 事件串聯類似于未結束的遞迴程序呼叫，但比較不明顯，因為呼叫是由 Visual Basic 而不是程式碼中的明確呼叫所進行。 使用 `Calls` 對話方塊可查看堆疊上的作用中程式。  
  
## <a name="see-also"></a>另請參閱

- [記憶體視窗](/visualstudio/debugger/memory-windows)

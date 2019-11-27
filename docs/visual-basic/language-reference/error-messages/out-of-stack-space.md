---
title: 堆疊空間用盡
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: 9ae604a9727413f2705d42a4b68f5a50b7dd3feb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349188"
---
# <a name="out-of-stack-space-visual-basic"></a>堆疊空間不足 (Visual Basic)
堆疊是記憶體的工作區域，會隨著執行程式的需求動態成長和縮減。 已超過其限制。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 檢查程式是否的嵌套太深。  
  
2. 請確定遞迴程式已正確終止。  
  
3. 如果本機變數需要的本機變數空間比可用的數目還要多，請嘗試在模組層級宣告一些變數。 您也可以在 `Property`、`Sub`或 `Function` 關鍵字前面加上 `Static`，以宣告程式中的所有變數。 或者，您可以使用 `Static` 語句，在程式內宣告個別的靜態變數。  
  
4. 將部分固定長度的字串重新定義為可變長度字串，因為固定長度的字串會使用比可變長度字串更多的堆疊空間。 您也可以在模組層級定義不需要堆疊空間的字串。  
  
5. 使用 [`Calls`] 對話方塊，查看堆疊上作用中的程式，以檢查嵌套 `DoEvents` 函式呼叫的數目。  
  
6. 觸發呼叫已在堆疊上之事件程式的事件，以確定您未造成「事件 cascade」。 事件 cascade 類似于未結束的遞迴程序呼叫，但較不明顯，因為呼叫是由 Visual Basic，而不是程式碼中的明確呼叫所發出。 使用 [`Calls`] 對話方塊，即可查看堆疊上作用中的程式。  
  
## <a name="see-also"></a>請參閱

- [記憶體視窗](/visualstudio/debugger/memory-windows)

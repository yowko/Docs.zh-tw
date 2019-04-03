---
title: 堆疊空間不足 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: 25905e65e74b11d167d3ce2ad258599fb958eb88
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814597"
---
# <a name="out-of-stack-space-visual-basic"></a>堆疊空間不足 (Visual Basic)
堆疊是執行程式的需求使用動態記憶體成長和縮減工作區域。 已超過其限制。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請檢查該程序無巢狀太深。  
  
2.  請確定遞迴程序會正確地終止。  
  
3.  如果本機變數需要更多區域的變數空間大於可用，請嘗試宣告一些變數，在模組層級。 您也可以宣告程序中的所有變數靜態前面`Property`， `Sub`，或`Function`關鍵字搭配`Static`。 或者您可以使用`Static`陳述式來宣告程序內的個別靜態變數。  
  
4.  重新定義部分的可變長度的字串，為您固定長度字串的固定長度字串使用堆疊空間較可變長度的字串。 您也可以定義在模組層級，它不需要堆疊空間的字串。  
  
5.  檢查數目巢狀`DoEvents`函式呼叫，使用`Calls`對話方塊來檢視哪些程序會在堆疊上作用。  
  
6.  請確定您不會觸發已將事件程序呼叫堆疊的事件 」 事件 cascade"。 事件串聯類似於未結束的遞迴程序呼叫，但它是較不明顯，因為 Visual Basic，而不是明確呼叫程式碼中的進行呼叫。 使用`Calls`對話方塊來檢視哪些程序會在堆疊上作用。  
  
## <a name="see-also"></a>另請參閱

- [記憶體視窗](/visualstudio/debugger/memory-windows)

---
title: 堆疊空間不足 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: e39be5913fe877cf7b3396e4f13f4440288cb8f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593281"
---
# <a name="out-of-stack-space-visual-basic"></a>堆疊空間不足 (Visual Basic)
堆疊是記憶體的工作區域的成長和壓縮，以動態方式與執行程式的需求。 已超過其限制。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請檢查該程序無巢狀太深。  
  
2.  請確定遞迴程序會正確地終止。  
  
3.  如果本機變數需要多個本機變數空間大於可用空間，請嘗試宣告部分模組層級的變數。 您也可以宣告程序中的所有變數靜態前`Property`， `Sub`，或`Function`關鍵字搭配`Static`。 您可以使用或`Static`宣告程序內的個別靜態變數的陳述式。  
  
4.  重新定義為可變長度字串，固定長度字串的部分為固定長度字串使用堆疊空間較可變長度的字串。 您也可以定義在模組層級，不需要堆疊空間的字串。  
  
5.  檢查數目巢狀`DoEvents`函式呼叫，使用`Calls`對話方塊來檢視哪些程序會在堆疊作用中。  
  
6.  請確定您未透過觸發已將事件程序呼叫堆疊的事件不會造成 」 事件串聯 」。 事件串聯類似結束的遞迴程序呼叫，但它是較不明顯，因為 Visual Basic，而不是在程式碼中明確呼叫進行呼叫。 使用`Calls`對話方塊來檢視哪些程序會在堆疊作用中。  
  
## <a name="see-also"></a>另請參閱  
 [記憶體視窗](/visualstudio/debugger/memory-windows)

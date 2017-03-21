---
title: "堆疊空間 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID28
dev_langs:
- VB
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
caps.latest.revision: 8
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6343767da28ea4e02f9443006b222640755f7882
ms.lasthandoff: 03/13/2017

---
# <a name="out-of-stack-space-visual-basic"></a>堆疊空間不足 (Visual Basic)
堆疊是執行程式的要求使用動態記憶體成長和縮減工作區域。 已超過其限制。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請檢查程序不太深，巢狀。  
  
2.  請確定遞迴程序會正確地終止。  
  
3.  如果區域變數需要多個本機變數空間大於可用空間，請嘗試一些變數，在模組層級中宣告。 您也可以宣告此程序中的所有變數靜態前面的`Property`， `Sub`，或`Function`關鍵字與`Static`。 或者您可以使用`Static`陳述式來宣告程序內的個別靜態變數。  
  
4.  重新定義一些固定長度字串為可變長度字串的固定長度字串使用堆疊空間較可變長度的字串。 您也可以定義在模組層級，不需要堆疊空間的字串。  
  
5.  檢查數目巢狀`DoEvents`函式呼叫，使用`Calls`對話方塊來檢視哪些程序會在堆疊上作用。  
  
6.  請確定您不會 」 事件串聯"造成所觸發的事件，已經呼叫堆疊上的事件程序。 事件串聯結束的遞迴程序呼叫，類似，但它是較不明顯，因為呼叫由進行[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]而不是在程式碼中明確呼叫。 使用`Calls`對話方塊來檢視哪些程序會在堆疊上作用。  
  
## <a name="see-also"></a>另請參閱  
 [記憶體視窗](https://docs.microsoft.com/visualstudio/debugger/memory-windows)

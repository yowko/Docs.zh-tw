---
title: 結束&lt;關鍵字&gt;陳述式 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.EndDefinition
helpviewer_keywords:
- End keyword [Visual Basic]
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cf0ac1221f8a85a8a43599d9c5ec210884205e5e
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="end-ltkeywordgt-statement-visual-basic"></a>結束&lt;關鍵字&gt;陳述式 (Visual Basic)
其他關鍵字後面跟著，結束該關鍵字所導入的陳述式區塊的定義。  
  
## <a name="syntax"></a>語法  
  
```  
End AddHandler  
End Class   
End Enum   
End Event   
End Function   
End Get   
End If   
End Interface   
End Module   
End Namespace   
End Operator   
End Property   
End RaiseEvent  
End RemoveHandler  
End Select   
End Set   
End Structure   
End Sub   
End SyncLock   
End Try   
End While   
End With  
```  
  
## <a name="parts"></a>組件  
 `End`  
 必要項。 結束程式設計項目的定義。  
  
 `AddHandler`  
 必要`AddHandler`開始比對的存取子`AddHandler`陳述式中自訂[Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)。  
  
 `Class`  
 必要的類別定義，開始比對[Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)。  
  
 `Enum`  
 藉由比對開始列舉定義必要[Enum 陳述式](../../../visual-basic/language-reference/statements/enum-statement.md)。  
  
 `Event`  
 必要`Custom`開始比對事件定義[Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)。  
  
 `Function`  
 必要`Function`開始比對程序定義[Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)。 如果執行遇到`End``Function`陳述式，控制權回到呼叫的程式碼。  
  
 `Get`  
 必要`Property`開始比對程序定義[Get 陳述式](../../../visual-basic/language-reference/statements/get-statement.md)。 如果執行遇到`End``Get`陳述式，控制權會傳回要求的屬性值的陳述式。  
  
 `If`  
 必要`If`...`Then`...`Else`區塊定義比對開始`If`陳述式。 請參閱[如果...Then...Else 陳述式](../../../visual-basic/language-reference/statements/if-then-else-statement.md)。  
  
 `Interface`  
 必要的介面定義，藉由比對開始[介面陳述式](../../../visual-basic/language-reference/statements/interface-statement.md)。  
  
 `Module`  
 必要模組定義比對開始[Module 陳述式](../../../visual-basic/language-reference/statements/module-statement.md)。  
  
 `Namespace`  
 必要命名空間定義比對開始[命名空間陳述式](../../../visual-basic/language-reference/statements/namespace-statement.md)。  
  
 `Operator`  
 必要項相對[Operator 陳述式](../../../visual-basic/language-reference/statements/operator-statement.md)。  
  
 `Property`  
 必要屬性定義，藉由比對開始[Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)。  
  
 `RaiseEvent`  
 必要`RaiseEvent`開始比對的存取子`RaiseEvent`陳述式中自訂[Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)。  
  
 `RemoveHandler`  
 必要`RemoveHandler`開始比對的存取子`RemoveHandler`陳述式中自訂[Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)。  
  
 `Select`  
 必要`Select`...`Case`區塊定義比對開始`Select`陳述式。 請參閱[選取...陳述式的大小寫](../../../visual-basic/language-reference/statements/select-case-statement.md)。  
  
 `Set`  
 必要`Property`開始比對程序定義[Set 陳述式](../../../visual-basic/language-reference/statements/set-statement.md)。 如果執行遇到`End``Set`陳述式，控制權會傳回設定的屬性值的陳述式。  
  
 `Structure`  
 必要項相對[Structure 陳述式](../../../visual-basic/language-reference/statements/structure-statement.md)。  
  
 `Sub`  
 必要`Sub`開始比對程序定義[Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)。 如果執行遇到`End``Sub`陳述式，控制權回到呼叫的程式碼。  
  
 `SyncLock`  
 必要`SyncLock`區塊定義比對開始`SyncLock`陳述式。 請參閱[SyncLock 陳述式](../../../visual-basic/language-reference/statements/synclock-statement.md)。  
  
 `Try`  
 必要`Try`...`Catch`...`Finally`區塊定義比對開始`Try`陳述式。 請參閱[再試一次...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。  
  
 `While`  
 必要`While`迴圈定義比對開始`While`陳述式。 請參閱[時...結束 While 陳述式](../../../visual-basic/language-reference/statements/while-end-while-statement.md)。  
  
 `With`  
 必要`With`區塊定義比對開始`With`陳述式。 請參閱[與...With 陳述式](../../../visual-basic/language-reference/statements/with-end-with-statement.md)。  
  
## <a name="remarks"></a>備註  
 [End 陳述式](../../../visual-basic/language-reference/statements/end-statement.md)，沒有其他的關鍵字，立即結束執行。  
  
 當前面加上數字符號 (`#`)、`End`關鍵字終止所對應的指示詞引入的前置處理區塊。  
  
 `#End`  
 必要項。 結束前置處理的區塊的定義。  
  
 `#ExternalSource`  
 必要的外部來源區塊，藉由比對開始[#ExternalSource 指示詞](../../../visual-basic/language-reference/directives/externalsource-directive.md)。  
  
 `#If`  
 必要開始比對的條件式編譯區塊`#If`指示詞。 請參閱[#If......#Else 指示詞](../../../visual-basic/language-reference/directives/if-then-else-directives.md)。  
  
 `#Region`  
 來源區域區塊開始比對必要[#Region 指示詞](../../../visual-basic/language-reference/directives/region-directive.md)。  
  
## <a name="smart-device-developer-notes"></a>智慧型裝置開發人員注意事項  
 `End`陳述式中，沒有其他的關鍵字，不支援。  
  
## <a name="see-also"></a>另請參閱  
 [End 陳述式](../../../visual-basic/language-reference/statements/end-statement.md)

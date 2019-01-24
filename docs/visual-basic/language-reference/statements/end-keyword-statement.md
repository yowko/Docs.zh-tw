---
title: 結束&lt;關鍵字&gt;陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.EndDefinition
helpviewer_keywords:
- End keyword [Visual Basic]
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
ms.openlocfilehash: d65c921a1631cd38c4d0d1ab9b34db3d7e43a97e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654837"
---
# <a name="end-ltkeywordgt-statement-visual-basic"></a>結束&lt;關鍵字&gt;陳述式 (Visual Basic)

當後面接著一個額外的關鍵字，會終止陳述式區塊，該關鍵字所導入的定義。

## <a name="syntax"></a>語法

```vb
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

|組件|描述|
|---|---|
|`End`|必要項。 結束程式設計項目的定義。|
|`AddHandler`|才能終止`AddHandler`存取子應開始`AddHandler`陳述式，在自訂[Event 陳述式](event-statement.md)。|
|`Class`|終止開始比對的類別定義，才能[Class 陳述式](class-statement.md)。|
|`Enum`|終止開始比對的列舉型別定義所需[Enum 陳述式](enum-statement.md)。|
|`Event`|需要終止`Custom`開始比對的事件定義[Event 陳述式](event-statement.md)。|  
|`Function`|需要終止`Function`應開始的程序定義[Function 陳述式](function-statement.md)。 如果執行時發生`End Function`陳述式中，控制回到呼叫端程式碼。|
|`Get`|需要終止`Property`應開始的程序定義[Get 陳述式](get-statement.md)。 如果執行時發生`End Get`陳述式中，控制項會返回至 要求屬性值的陳述式。|
|`If`|必要`If`...`Then`...`Else`區塊定義比對開始`If`陳述式。 請參閱[如果...Then...Else 陳述式](if-then-else-statement.md)。|
|`Interface`|必要的介面定義，開始比對[Interface 陳述式](interface-statement.md)。|
|`Module`|結束模組定義比對開始時所需[Module 陳述式](module-statement.md)。|
|`Namespace`|必要命名空間定義比對開始[命名空間陳述式](namespace-statement.md)。|
|`Operator`|終止開始比對運算子定義所需[Operator Statement](operator-statement.md)。|
|`Property`|必要開始比對的屬性定義[Property Statement](property-statement.md)。|
|`RaiseEvent`|才能終止`RaiseEvent`存取子應開始`RaiseEvent`陳述式，在自訂[Event 陳述式](event-statement.md)。|
|`RemoveHandler`|才能終止`RemoveHandler`存取子應開始`RemoveHandler`陳述式，在自訂[Event 陳述式](event-statement.md)。|
|`Select`|必要`Select`...`Case`區塊定義比對開始`Select`陳述式。 請參閱[選取...Case 陳述式](select-case-statement.md)。  
|`Set`|需要終止`Property`應開始的程序定義[Set 陳述式](set-statement.md)。 如果執行時發生`End Set`陳述式，控制權會回到陳述式以設定屬性的值。  
|`Structure`|必要的結構定義，開始比對[Structure 陳述式](structure-statement.md)。  
|`Sub`|需要終止`Sub`應開始的程序定義[Sub 陳述式](sub-statement.md)。 如果執行時發生`End Sub`陳述式中，控制回到呼叫端程式碼。  
|`SyncLock`|需要終止`SyncLock`區塊定義比對開始`SyncLock`陳述式。 請參閱[SyncLock 陳述式](synclock-statement.md)。  
|`Try`|必要`Try`...`Catch`...`Finally`區塊定義比對開始`Try`陳述式。 請參閱[試...Catch...Try...catch...finally 陳述式](try-catch-finally-statement.md)。  
|`While`|需要終止`While`迴圈開始比對的定義`While`陳述式。 請參閱[時...結束 While 陳述式](while-end-while-statement.md)。  
|`With`| 需要終止`With`區塊定義比對開始`With`陳述式。 請參閱[與...With...end With 陳述式](with-end-with-statement.md)。  
|||
  
## <a name="directives"></a>指示詞

當前面加上數字符號 (`#`)，則`End`關鍵字會終止對應的指示詞所引入的前置處理區塊。  

```vb
#End ExternalSource
#End If
#End Region
```

|組件|描述|
|---|---|
|`#End`|必要項。 結束前置處理的區塊的定義。|
|`ExternalSource`|必要開始比對的外部來源區塊[#ExternalSource 指示詞](../directives/externalsource-directive.md)。|
|`If`|必要開始比對的條件式編譯區塊`#If`指示詞。 請參閱[#If......#Else 指示詞](../directives/if-then-else-directives.md)。|
|`Region`|必要開始比對來源區域區塊[#Region 指示詞](../directives/region-directive.md)。|
|||

## <a name="remarks"></a>備註

[End 陳述式](end-statement.md)，而不需要額外的關鍵字，執行會立即終止。

## <a name="smart-device-developer-notes"></a>智慧型裝置開發人員注意事項  

`End`陳述式，而不需要額外的關鍵字，不支援。  
  
## <a name="see-also"></a>另請參閱

- [End 陳述式](end-statement.md)

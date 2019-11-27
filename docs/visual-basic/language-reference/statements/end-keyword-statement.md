---
title: End <keyword> 陳述式
ms.date: 07/20/2015
f1_keywords:
- vb.EndDefinition
helpviewer_keywords:
- End keyword [Visual Basic]
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
ms.openlocfilehash: 87f4724cc036e6e0bdf0b558854a4034f45b9ab5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343741"
---
# <a name="end-keyword-statement-visual-basic"></a>End \<關鍵字 > 語句（Visual Basic）

後面接著一個額外的關鍵字時，會終止該關鍵字所引進之語句區塊的定義。

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
|`End`|必要。 結束程式設計項目的定義。|
|`AddHandler`|需要終止自訂[事件語句](event-statement.md)中符合的 `AddHandler` 語句開始的 `AddHandler` 存取子。|
|`Class`|需要終止由相符的[Class 語句](class-statement.md)開始的類別定義。|
|`Enum`|需要終止相符的[Enum 語句](enum-statement.md)所開始的列舉定義。|
|`Event`|終止由相符的[事件語句](event-statement.md)開始的 `Custom` 事件定義時所需。|  
|`Function`|終止由相符的[Function 語句](function-statement.md)開始的 `Function` 程序定義所需。 如果執行遇到 `End Function` 語句，則控制權會回到呼叫程式碼。|
|`Get`|終止由相符的[Get 語句](get-statement.md)開始的 `Property` 程序定義所需。 如果執行遇到 `End Get` 語句，則控制權會回到要求屬性值的語句。|
|`If`|需要終止 `If`...`Then`...`Else` 由相符的 `If` 語句開始的區塊定義。 查看[是否 .。。然後 .。。Else 語句](if-then-else-statement.md)。|
|`Interface`|必須有，才能結束字元合的[介面語句](interface-statement.md)所開始的介面定義。|
|`Module`|必須有此項，才能終止由相符[模組語句](module-statement.md)開始的模組定義。|
|`Namespace`|需要終止相符的[命名空間語句](namespace-statement.md)所開始的命名空間定義。|
|`Operator`|終止由相符的[運算子語句](operator-statement.md)開始的運算子定義時所需。|
|`Property`|需要結束字元合的[屬性語句](property-statement.md)開始的屬性定義。|
|`RaiseEvent`|需要終止自訂[事件語句](event-statement.md)中符合的 `RaiseEvent` 語句開始的 `RaiseEvent` 存取子。|
|`RemoveHandler`|需要終止自訂[事件語句](event-statement.md)中符合的 `RemoveHandler` 語句開始的 `RemoveHandler` 存取子。|
|`Select`|需要終止 `Select`...`Case` 區塊定義（由相符的 `Select` 語句開始）。 請參閱[Select .。。Case 語句](select-case-statement.md)。  
|`Set`|終止由相符[Set 語句](set-statement.md)開始的 `Property` 程序定義所需。 如果執行遇到 `End Set` 語句，則控制權會回到設定屬性值的語句。  
|`Structure`|需要終止由相符的[Structure 語句](structure-statement.md)開始的結構定義。  
|`Sub`|終止由相符的[Sub 語句](sub-statement.md)開始的 `Sub` 程序定義所需。 如果執行遇到 `End Sub` 語句，則控制權會回到呼叫程式碼。  
|`SyncLock`|需要結束字元合的 `SyncLock` 語句開始的 `SyncLock` 區塊定義。 請參閱[SyncLock 語句](synclock-statement.md)。  
|`Try`|需要終止 `Try`...`Catch`...`Finally` 由相符的 `Try` 語句開始的區塊定義。 請參閱[嘗試 .。。Catch .。。Finally 語句](try-catch-finally-statement.md)。  
|`While`|需要結束字元合的 `While` 語句開始的 `While` 迴圈定義。 請參閱[While .。。End While 語句](while-end-while-statement.md)。  
|`With`| 需要結束字元合的 `With` 語句開始的 `With` 區塊定義。 請參閱[With .。。結尾為語句](with-end-with-statement.md)。  
|||
  
## <a name="directives"></a>指示詞

當前面加上數位記號（`#`）時，`End` 關鍵字會終止對應指示詞所引進的前置處理區塊。  

```vb
#End ExternalSource
#End If
#End Region
```

|組件|描述|
|---|---|
|`#End`|必要。 終止前置處理區塊的定義。|
|`ExternalSource`|需要結束字元合的[#ExternalSource](../directives/externalsource-directive.md)指示詞開始的外部來源區塊。|
|`If`|終止由相符的 `#If` 指示詞開始的條件式編譯區塊時所需。 請參閱[#If .。。Then ... #Else](../directives/if-then-else-directives.md)指示詞。|
|`Region`|終止由相符的[#Region](../directives/region-directive.md)指示詞開始的來源區域區塊時所需。|
|||

## <a name="remarks"></a>備註

[結尾語句](end-statement.md)（不含額外的關鍵字）會立即終止執行。

## <a name="smart-device-developer-notes"></a>智慧型裝置開發人員注意事項  

不支援不含額外關鍵字的 `End` 語句。  
  
## <a name="see-also"></a>請參閱

- [End 陳述式](end-statement.md)

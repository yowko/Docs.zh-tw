---
title: WithEvents
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: c2dcb044d04099c51f57d82a8bc08f0932bf3542
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875422"
---
# <a name="withevents-visual-basic"></a>WithEvents (Visual Basic)

指定一或多個宣告的成員變數參考可引發事件之類別的實例。

## <a name="remarks"></a>備註

使用定義的變數時 `WithEvents` ，您可以使用關鍵字，以宣告方式指定方法處理變數的事件 `Handles` 。

您 `WithEvents` 只能在類別或模組層級使用。 這表示變數的宣告內容 `WithEvents` 必須是類別或模組，且不能是原始程式檔、命名空間、結構或程式。

您無法 `WithEvents` 在結構成員上使用。

您只能使用宣告個別變數（非陣列） `WithEvents` 。

## <a name="rules"></a>規則

**元素類型。** 您必須 `WithEvents` 將變數宣告為物件變數，讓它們可以接受類別實例。 不過，您無法將它們宣告為 `Object` 。 您必須將它們宣告為可引發事件的特定類別。

`WithEvents`修飾詞可用於此內容： [Dim 語句](../statements/dim-statement.md)

## <a name="example"></a>範例

```vb
Dim WithEvents app As Application
```

## <a name="see-also"></a>另請參閱

- [處理](../statements/handles-clause.md)
- [關鍵字](../keywords/index.md)
- [事件](../../programming-guide/language-features/events/index.md)

---
title: WithEvents (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: 50d5a768393e90d28d150b451405e35e6f4c7953
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583034"
---
# <a name="withevents-visual-basic"></a>WithEvents (Visual Basic)
指定一個或多個宣告的成員變數參考可引發事件之類別的實例。

## <a name="remarks"></a>備註

使用 `WithEvents` 定義變數時，您可以使用 `Handles` 關鍵字，以宣告方式指定方法處理變數的事件。

您只能在類別或模組層級使用 `WithEvents`。 這表示 `WithEvents` 變數的宣告內容必須是類別或模組，而且不能是原始程式檔、命名空間、結構或程式。

您不能在結構成員上使用 `WithEvents`。

您只能使用 `WithEvents` 宣告個別變數（而非陣列）。

## <a name="rules"></a>規則

**元素類型。** 您必須將 `WithEvents` 變數宣告為物件變數，使其可以接受類別實例。 不過，您無法將它們宣告為 `Object`。 您必須將它們宣告為可引發事件的特定類別。

@No__t_0 修飾詞可以在此內容中使用： [Dim 語句](../../../visual-basic/language-reference/statements/dim-statement.md)

## <a name="example"></a>範例

```vb
Dim WithEvents app As Application
```

## <a name="see-also"></a>請參閱

- [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
- [關鍵字](../../../visual-basic/language-reference/keywords/index.md)
- [事件](../../../visual-basic/programming-guide/language-features/events/index.md)

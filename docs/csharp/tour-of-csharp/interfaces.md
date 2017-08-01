---
title: "C# 介面 - C# 語言教學課程"
description: "介面會定義 C# 中由類型實作的合約"
keywords: ".NET, csharp, 介面, 多重繼承, 多型"
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a9bf82f4-efd1-4216-bd34-4ef0fa48c968
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 673ac56f3f5732fcda02d313b6f4273708ae365f
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---

# <a name="interfaces"></a>介面

「介面」定義可由類別和結構實作的合約。 介面可以包含方法、屬性、事件和索引子。 介面不提供它所定義之成員的實作 (它只會指定必須由類別提供的成員或實作介面的結構)。

介面可以採用「多重繼承」。 在下列範例中，介面 `IComboBox` 同時繼承自 `ITextBox` 和 `IListBox`。

[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]

類別和結構可以實作多個介面。 在下列範例中，類別 `EditBox` 可以實作 `IControl` 與 `IDataBound` 兩者。

[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]

當類別或結構實作特定介面時，可以將該類別或結構的執行個體隱含地轉換為該介面型別。 例如

[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]

在實作特定介面的執行個體無法確知的情況下，可以使用動態型別轉換。 例如，下列陳述式使用動態型別轉換以取得物件的 `IControl` 和 `IDataBound` 介面實作。 因為物件的執行階段實際型別是 `EditBox`，所以會轉型成功。

[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]

在上一個 `EditBox` 類別中，來自 `IControl` 介面的 `Paint` 方法和來自 `IDataBound` 介面的 `Bind` 方法，都使用公用成員來實作。 C# 也支援明確「介面成員實作」，啟用類別或結構以避免將成員設為公用。 明確介面成員實作是使用介面成員完整名稱來撰寫。 例如，`EditBox` 類別可以使用明確介面成員實作來實作 `IControl.Paint` 和 `IDataBound.Bind` 方法，如下所示。

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]

明確介面成員只能透過介面型別來存取。 例如，要先將 `EditBox` 參考轉換為 `IControl` 介面型別，才可以叫用上述 EditBox 類別所提供的 `IControl.Paint` 實作。

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]

>[!div class="step-by-step"]
[上一頁](arrays.md)
[下一頁](enums.md)


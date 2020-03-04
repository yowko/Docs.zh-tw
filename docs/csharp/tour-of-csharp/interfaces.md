---
title: C# 介面 - C# 語言教學課程
description: 介面會定義 C# 中由類型實作的合約
ms.date: 02/27/2020
ms.assetid: a9bf82f4-efd1-4216-bd34-4ef0fa48c968
ms.openlocfilehash: 62d94462fa481379cf70d63a598deb7f36be204f
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159126"
---
# <a name="interfaces"></a>介面

「介面」定義可由類別和結構實作的合約。 介面可以包含方法、屬性、事件和索引子。 介面不提供它所定義之成員的執行，它只會指定必須由實作為介面的類別或結構所提供的成員。

介面可以採用「多重繼承」。 在下列範例中，介面 `IComboBox` 同時繼承自 `ITextBox` 和 `IListBox`。

[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]

類別和結構可以實作多個介面。 在下列範例中，類別 `EditBox` 可以實作 `IControl` 與 `IDataBound` 兩者。

[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]

當類別或結構實作特定介面時，可以將該類別或結構的執行個體隱含地轉換為該介面型別。 例如：

[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]

如果實例無法以靜態方式得知如何執行特定介面，則可以使用動態類型轉換。 例如，下列陳述式使用動態型別轉換以取得物件的 `IControl` 和 `IDataBound` 介面實作。 因為物件的執行階段實際型別是 `EditBox`，所以會轉型成功。

[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]

在上一個 `EditBox` 類別中，來自 `Paint` 介面的 `IControl` 方法和來自 `Bind` 介面的 `IDataBound` 方法，都使用公用成員來實作。 C# 也支援明確「介面成員實作」，啟用類別或結構以避免將成員設為公用。 明確介面成員實作是使用介面成員完整名稱來撰寫。 例如，`EditBox` 類別可以使用明確介面成員實作來實作 `IControl.Paint` 和 `IDataBound.Bind` 方法，如下所示。

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]

明確介面成員只能透過介面型別來存取。 例如，要先將 `IControl.Paint` 參考轉換為 `EditBox` 介面型別，才可以叫用上述 EditBox 類別所提供的 `IControl` 實作。

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]

>[!div class="step-by-step"]
>[上一頁](arrays.md)
>[下一頁](delegates.md)

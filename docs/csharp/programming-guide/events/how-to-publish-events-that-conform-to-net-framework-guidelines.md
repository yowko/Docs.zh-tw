---
title: '發行符合 .NET 指導方針的事件-c # 程式設計手冊'
ms.date: 05/26/2020
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: df2f643f867b93b74d04d8fbd673df545c28938e
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2020
ms.locfileid: "84240742"
---
# <a name="how-to-publish-events-that-conform-to-net-guidelines-c-programming-guide"></a>如何發行符合 .NET 指導方針的事件（c # 程式設計手冊）

下列程式示範如何將遵循標準 .NET 模式的事件新增至您的類別和結構。 .NET Framework 類別庫中的所有事件都是以 <xref:System.EventHandler> 委派為基礎，其定義如下：

```csharp
public delegate void EventHandler(object sender, EventArgs e);
```

> [!NOTE]
> .NET Framework 2.0 引進此委派的泛型版本 <xref:System.EventHandler%601> 。 下列範例示範如何使用這兩種版本。

雖然您定義之類別中的事件可以根據任何有效的委派類型，甚至是傳回值的委派，但通常建議您使用來根據 .NET 模式來建立事件的基礎 <xref:System.EventHandler> ，如下列範例所示。

名稱 `EventHandler` 可能會造成一些混淆，因為它實際上不會處理事件。 <xref:System.EventHandler>、和泛型 <xref:System.EventHandler%601> 是委派類型。 其簽章符合委派定義的方法或 lambda 運算式是*事件處理常式*，而且會在引發事件時叫用。

## <a name="publish-events-based-on-the-eventhandler-pattern"></a>根據 EventHandler 模式發佈事件

1. （如果您不需要隨事件傳送自訂資料，請略過此步驟並移至步驟3a）。針對您的「發行者」和「訂閱者」類別顯示的範圍，宣告自訂資料的類別。 然後新增必要的成員來保存自訂事件資料。 在此範例中，會傳回一個簡單的字串。

    ```csharp
    public class CustomEventArgs : EventArgs
    {
        public CustomEventArgs(string message)
        {
            Message = message;
        }

        public string Message { get; set; }
    }
    ```

2. （如果您使用的是泛型版本，請略過此步驟 <xref:System.EventHandler%601> ）。在發行類別中宣告委派。 提供結尾為的名稱 `EventHandler` 。 第二個參數指定您的自訂 `EventArgs` 類型。

    ```csharp
    public delegate void CustomEventHandler(object sender, CustomEventArgs args);
    ```

3. 使用下列其中一個步驟，在發行類別中宣告事件。

    1. 如果沒有自訂 EventArgs 類別，Event 類型將會是非泛型的 EventHandler 委派。 因為當您建立 C# 專案時所包含的 <xref:System> 命名空間中已宣告委派，所以您不需要宣告委派。 將下列程式碼新增至發行者類別。

        ```csharp
        public event EventHandler RaiseCustomEvent;
        ```

    2. 如果您使用的是 <xref:System.EventHandler> 的非泛型版本，而且有衍生自 <xref:System.EventArgs> 的自訂類別，請在發行類別內宣告事件，並使用步驟 2 中的委派作為類型。

        ```csharp
        public event CustomEventHandler RaiseCustomEvent;
        ```

    3. 如果您使用的是泛型版本，則不需要自訂委派。 相反地，您會在發行類別中將事件類型指定為 `EventHandler<CustomEventArgs>`，來替代角括號之間的類別名稱。

        ```csharp
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;
        ```

## <a name="example"></a>範例

下列範例使用自訂 EventArgs 類別和 <xref:System.EventHandler%601> 作為事件類型，來示範上述步驟。

[!code-csharp[csProgGuideEvents#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#2)]

## <a name="see-also"></a>另請參閱

- <xref:System.Delegate>
- [C # 程式設計指南](../index.md)
- [事件](index.md)
- [委派](../delegates/index.md)

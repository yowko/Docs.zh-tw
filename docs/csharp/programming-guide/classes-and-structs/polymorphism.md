---
title: 多型 - C# 程式設計手冊
ms.date: 02/08/2020
helpviewer_keywords:
- C# language, polymorphism
- polymorphism [C#]
ms.assetid: 086af969-29a5-4ce8-a993-0b7d53839dab
ms.openlocfilehash: 58980bd0d70d8a778cdb208f56d31ee8465871a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170165"
---
# <a name="polymorphism-c-programming-guide"></a>多型 (C# 程式設計手冊)

多型通常是指物件導向程式設計的第三個重要部分，其重要性僅次於封裝和繼承。 多型在希臘文中表示「多種形狀」，可分成下列兩方面：
  
- 在執行階段，衍生類別物件可視為方法參數和集合或陣列等位置中的基底類別物件。 發生此多態性時，物件的聲明類型不再與其運行時類型相同。
- 基底類別可以定義和實作 [virtual「方法」](../../language-reference/keywords/virtual.md) **，而衍生類別可以[覆寫](../../language-reference/keywords/override.md)這些方法，換句話說，衍生類別會提供自己的定義和實作。 在執行階段，當用戶端程式碼呼叫方法時，CLR 會查詢物件的執行階段類型，然後叫用虛擬方法的覆寫。 在原始程式碼中，可以調用基類上的方法，並導致執行派生類的方法版本。

虛擬方法可讓您以一致的方式來使用相關物件群組。 例如，假設您有一個繪圖應用程式，可讓使用者在繪圖介面上建立各種圖形。 您不知道使用者將在編譯時期建立哪一種圖形。 但是，應用程式必須追蹤所建立的所有不同圖形類型，並且必須根據使用者滑鼠動作來更新圖形。 您可以使用多型，分兩個基本步驟來解決這個問題：

1. 建立類別階層架構，其中每個特定圖形類別都是衍生自一個通用基底類別。
1. 使用虛擬方法，透過對基底類別方法發出單一呼叫，在任何衍生類別上叫用適當的方法。

首先，建立稱為 `Shape` 的基底類別，以及 `Rectangle`、`Circle` 和 `Triangle` 等衍生類別。 將稱為 `Shape` 的虛擬方法提供給 `Draw` 類別，然後在每個衍生類別中覆寫此方法，以繪製該類別代表的特定圖形。 創建物件`List<Shape>`並添加`Circle`、`Triangle`和`Rectangle`。

[!code-csharp[Polymorphism overview](~/samples/snippets/csharp/objectoriented/Inheritance.cs#PolymorphismOverview)]

若要更新繪圖介面，請使用 [foreach](../../language-reference/keywords/foreach-in.md) 迴圈逐一查看清單，並在清單中的每個 `Shape` 物件上呼叫 `Draw` 方法。 即使清單中的每個物件都有聲明的類型`Shape`，但將被調用的是運行時類型（每個派生類中方法的重寫版本）。

[!code-csharp[Polymorphism overview](~/samples/snippets/csharp/objectoriented/Inheritance.cs#UsePolymorphism)]

在 C# 中，所有類型都是多型類型，因為所有類型 (包括使用者定義的類型) 都是繼承自 <xref:System.Object>。  

## <a name="polymorphism-overview"></a>多態性概述

### <a name="virtual-members"></a>虛擬成員

當派生類從基類繼承時，它將獲得基類的所有方法、欄位、屬性和事件。 派生類的設計器可以針對虛擬方法的行為做出不同的選擇：

- 派生類可以覆蓋基類中的虛擬成員，定義新行為。
- 派生類繼承最接近的基類方法而不重寫它，保留現有行為，但允許進一步的派生類重寫該方法。
- 派生類可以定義隱藏基類實現的成員的新非虛擬實現。

只有在基底類別成員宣告為 [virtual](../../language-reference/keywords/virtual.md) 或 [abstract](../../language-reference/keywords/abstract.md) 時，衍生類別才能覆寫基底類別成員。 衍生成員必須使用 [override](../../language-reference/keywords/override.md) 關鍵字明確指出方法預定會參與虛擬引動過程。 下列程式碼提供一個範例：

[!code-csharp[Virtual overview](~/samples/snippets/csharp/objectoriented/Inheritance.cs#VirtualMethods)]

欄位不能為虛擬欄位;因此，欄位不能為虛擬欄位。只有方法、屬性、事件和索引子可以是虛擬的。 當衍生類別覆寫虛擬成員時，即使將該類別的執行個體當做基底類別的執行個體來存取，也會呼叫該成員。 下列程式碼提供一個範例：

[!code-csharp[Virtual overview example](~/samples/snippets/csharp/objectoriented/Inheritance.cs#VirtualMethods)]

虛擬方法和屬性可讓衍生類別不需要使用方法的基底類別實作，即可擴充基底類別。 如需詳細資訊，請參閱[使用 Override 和 New 關鍵字進行版本控制](./versioning-with-the-override-and-new-keywords.md)。 介面是用來定義將其實作保留給衍生類別之一個方法或一組方法的另一種做法。 如需詳細資訊，請參閱[介面](../interfaces/index.md)。

### <a name="hide-base-class-members-with-new-members"></a>使用新成員隱藏基類成員

如果希望派生類具有與基類中成員同名的成員，則可以使用[new](../../language-reference/keywords/new-modifier.md)關鍵字隱藏基類成員。 `new` 關鍵字會放置在要取代之類別成員的傳回類型前面。 下列程式碼提供一個範例：

[!code-csharp[New method overview example](~/samples/snippets/csharp/objectoriented/Inheritance.cs#NewMethods)]

通過將派生類的實例強制轉換到基類的實例，可以從用戶端代碼訪問隱藏的基類成員。 例如：

[!code-csharp[New method overview usage](~/samples/snippets/csharp/objectoriented/Inheritance.cs#UseNewMethods)]

### <a name="prevent-derived-classes-from-overriding-virtual-members"></a>防止派生類覆蓋虛擬成員  

虛擬成員保持虛擬狀態，無論虛擬成員和最初聲明它的類之間已聲明多少個類。 如果類`A`聲明虛擬成員，並且類`B`派生自`A`，則類`C``B``C`繼承虛擬成員，並且可以重寫它，而不管類`B`是否聲明瞭該成員的重寫。 下列程式碼提供一個範例：

[!code-csharp[Basic hierarchy](~/samples/snippets/csharp/objectoriented/Hierarchy.cs#FirstHierarchy)]

衍生類別可以透過將覆寫宣告為 [sealed](../../language-reference/keywords/sealed.md)，來停止虛擬繼承。 停止繼承需要將`sealed`關鍵字放在類成員`override`聲明中的關鍵字之前。 下列程式碼提供一個範例：

[!code-csharp[A sealed overridden member](~/samples/snippets/csharp/objectoriented/Hierarchy.cs#SealedOverride)]

在前面的示例中，該方法`DoWork`不再對派生自`C`的任何類具有虛擬性。 對於 的實例，即使它們被強制`C`轉換為鍵入`B`或鍵入`A`，它仍然是虛擬的。 可以使用`new`關鍵字將密封方法替換為派生類，如下例所示：

[!code-csharp[New method declaration](~/samples/snippets/csharp/objectoriented/Hierarchy.cs#NewDeclaration)]

`DoWork`在這種情況下，如果使用`D`類型的`D`變數調用 new， 則調用 new。 `DoWork` `C`如果類型 中的變數`B`、`A`或 用於訪問 的`D`實例， 調用`DoWork`將遵循虛擬繼承的規則，將這些調用路由到 類`DoWork``C`上的實現 。

### <a name="access-base-class-virtual-members-from-derived-classes"></a>從派生類訪問基類虛擬成員

已取代或覆寫方法或屬性的衍生類別，仍可使用 `base` 關鍵字存取基底類別上的方法或屬性。 下列程式碼提供一個範例：

```csharp
public class Base
{
    public virtual void DoWork() {/*...*/ }
}
public class Derived : Base
{
    public override void DoWork()
    {
        //Perform Derived's work here
        //...
        // Call DoWork on base class
        base.DoWork();
    }
}
```

如需詳細資訊，請參閱 [base](../../language-reference/keywords/base.md)。

> [!NOTE]
> 建議虛擬成員使用 `base`，在其所擁有的實作中呼叫其基底類別實作。 允許發生基底類別行為，可讓衍生類別集中實作衍生類別的特定行為。 如果不呼叫基底類別實作，則衍生類別可自行決定是否要讓其行為與基底類別的行為相容。

## <a name="in-this-section"></a>本節內容

- [使用 Override 和 New 關鍵字進行版本控制](./versioning-with-the-override-and-new-keywords.md)
- [了解使用 Override 和 New 關鍵字的時機](./knowing-when-to-use-override-and-new-keywords.md)
- [如何覆寫 ToString 方法](./how-to-override-the-tostring-method.md)

## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../index.md)
- [繼承](./inheritance.md)
- [抽象和密封類別以及類別成員](./abstract-and-sealed-classes-and-class-members.md)
- [方法](./methods.md)
- [事件](../events/index.md)
- [屬性](./properties.md)
- [索引子](../indexers/index.md)
- [型別](../types/index.md)

---
title: 多型 - C# 程式設計手冊
ms.date: 02/08/2020
helpviewer_keywords:
- C# language, polymorphism
- polymorphism [C#]
ms.assetid: 086af969-29a5-4ce8-a993-0b7d53839dab
ms.openlocfilehash: 169ba2a1307a301c80b3d9ccac45f4ac9f707921
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626284"
---
# <a name="polymorphism-c-programming-guide"></a>多型 (C# 程式設計手冊)

多型通常是指物件導向程式設計的第三個重要部分，其重要性僅次於封裝和繼承。 多型在希臘文中表示「多種形狀」，可分成下列兩方面：
  
- 在執行階段，衍生類別物件可視為方法參數和集合或陣列等位置中的基底類別物件。 當這個多型發生時，物件的宣告型別就不再與執行時間型別完全相同。
- 基類可能會定義和實作為[虛擬](../../language-reference/keywords/virtual.md)*方法*，而衍生類別可以覆[寫](../../language-reference/keywords/override.md)它們，這表示它們會提供自己的定義和執行。 在執行階段，當用戶端程式碼呼叫方法時，CLR 會查詢物件的執行階段類型，然後叫用虛擬方法的覆寫。 在您的原始程式碼中，您可以呼叫基類上的方法，並使衍生類別的方法版本執行。

虛擬方法可讓您以一致的方式來使用相關物件群組。 例如，假設您有一個繪圖應用程式，可讓使用者在繪圖介面上建立各種圖形。 您不知道使用者將在編譯時期建立哪一種圖形。 但是，應用程式必須追蹤所建立的所有不同圖形類型，並且必須根據使用者滑鼠動作來更新圖形。 您可以使用多型，分兩個基本步驟來解決這個問題：

1. 建立類別階層架構，其中每個特定圖形類別都是衍生自一個通用基底類別。
1. 使用虛擬方法，透過對基底類別方法發出單一呼叫，在任何衍生類別上叫用適當的方法。

首先，建立稱為 `Shape` 的基底類別，以及 `Rectangle`、`Circle` 和 `Triangle` 等衍生類別。 將稱為 `Shape` 的虛擬方法提供給 `Draw` 類別，然後在每個衍生類別中覆寫此方法，以繪製該類別代表的特定圖形。 建立 `List<Shape>` 物件，並在其中新增 `Circle`、`Triangle`和 `Rectangle`。 

[!code-csharp[Polymorphism overview](~/samples/snippets/csharp/objectoriented/Inheritance.cs#PolymorphismOverview)]

若要更新繪圖介面，請使用 [foreach](../../language-reference/keywords/foreach-in.md) 迴圈逐一查看清單，並在清單中的每個 `Draw` 物件上呼叫 `Shape` 方法。 即使清單中的每個物件都有已宣告的 `Shape`類型，它還是會叫用的執行時間類型（每個衍生類別中方法的覆寫版本）。

[!code-csharp[Polymorphism overview](~/samples/snippets/csharp/objectoriented/Inheritance.cs#UsePolymorphism)]

在 C# 中，所有類型都是多型類型，因為所有類型 (包括使用者定義的類型) 都是繼承自 <xref:System.Object>。  

## <a name="polymorphism-overview"></a>多型總覽

### <a name="virtual-members"></a>虛擬成員

當衍生類別繼承自基類時，它會取得基類的所有方法、欄位、屬性和事件。 衍生類別的設計工具可以針對虛擬方法的行為進行不同的選擇：

- 衍生的類別可能會覆寫基類中的虛擬成員，並定義新的行為。
- 衍生的類別會繼承最接近的基類方法，而不會覆寫它、保留現有的行為，但允許進一步的衍生類別來覆寫方法。
- 衍生的類別可以定義隱藏基類實作為之成員的新非虛擬執行。

只有在基底類別成員宣告為 [virtual](../../language-reference/keywords/virtual.md) 或 [abstract](../../language-reference/keywords/abstract.md) 時，衍生類別才能覆寫基底類別成員。 衍生成員必須使用 [override](../../language-reference/keywords/override.md) 關鍵字明確指出方法預定會參與虛擬引動過程。 下列程式碼提供一個範例：

[!code-csharp[Virtual overview](~/samples/snippets/csharp/objectoriented/Inheritance.cs#VirtualMethods)]

欄位不可以是虛擬的;只有方法、屬性、事件和索引子可以是虛擬的。 當衍生類別覆寫虛擬成員時，即使將該類別的執行個體當做基底類別的執行個體來存取，也會呼叫該成員。 下列程式碼提供一個範例：

[!code-csharp[Virtual overview example](~/samples/snippets/csharp/objectoriented/Inheritance.cs#VirtualMethods)]

虛擬方法和屬性可讓衍生類別不需要使用方法的基底類別實作，即可擴充基底類別。 如需詳細資訊，請參閱[使用 Override 和 New 關鍵字進行版本控制](./versioning-with-the-override-and-new-keywords.md)。 介面是用來定義將其實作保留給衍生類別之一個方法或一組方法的另一種做法。 如需詳細資訊，請參閱 [介面](../interfaces/index.md)中定義的介面的私用 C++ 專屬實作。

### <a name="hide-base-class-members-with-new-members"></a>以新成員隱藏基類成員

如果您想要讓衍生類別具有與基類中的成員同名的成員，您可以使用[new](../../language-reference/keywords/new-modifier.md)關鍵字來隱藏基類成員。 `new` 關鍵字會放置在要取代之類別成員的傳回類型前面。 下列程式碼提供一個範例：

[!code-csharp[New method overview example](~/samples/snippets/csharp/objectoriented/Inheritance.cs#NewMethods)]

藉由將衍生類別的實例轉換為基類的實例，可以從用戶端程式代碼存取隱藏的基類成員。 例如：

[!code-csharp[New method overview usage](~/samples/snippets/csharp/objectoriented/Inheritance.cs#UseNewMethods)]

### <a name="prevent-derived-classes-from-overriding-virtual-members"></a>防止衍生類別覆寫虛擬成員  

無論虛擬成員和原本宣告它的類別之間已宣告多少個類別，虛擬成員仍然是虛擬的。 如果類別 `A` 宣告虛擬成員，而類別 `B` 衍生自 `A`，而類別 `C` 衍生自 `B`，則類別 `C` 會繼承該虛擬成員，而不論類別是否 `B` 宣告該成員的覆寫，都可以覆寫它。 下列程式碼提供一個範例：

[!code-csharp[Basic hierarchy](~/samples/snippets/csharp/objectoriented/Hierarchy.cs#FirstHierarchy)]

衍生類別可以透過將覆寫宣告為 [sealed](../../language-reference/keywords/sealed.md)，來停止虛擬繼承。 若要停止繼承，必須將 `sealed` 關鍵字放在類別成員宣告中的 `override` 關鍵字前面。 下列程式碼提供一個範例：

[!code-csharp[A sealed overridden member](~/samples/snippets/csharp/objectoriented/Hierarchy.cs#SealedOverride)]

在上述範例中，`DoWork` 的方法不再與任何衍生自 `C`的類別虛擬。 即使是轉換成類型 `B` 或類型 `A`，它仍是虛擬的 `C`實例。 密封的方法可以使用 `new` 關鍵字來取代為衍生類別，如下列範例所示：

[!code-csharp[New method declaration](~/samples/snippets/csharp/objectoriented/Hierarchy.cs#NewDeclaration)]

在此情況下，如果使用 `D`類型的變數在 `D` 上呼叫 `DoWork`，就會呼叫新的 `DoWork`。 如果 `C`、`B`或 `A` 類型的變數用來存取 `D`的實例，則呼叫 `DoWork` 會遵循虛擬繼承的規則，將這些呼叫路由至類別 `DoWork` 上的 `C`執行。

### <a name="access-base-class-virtual-members-from-derived-classes"></a>從衍生類別存取基類虛擬成員

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
- [類型](../types/index.md)

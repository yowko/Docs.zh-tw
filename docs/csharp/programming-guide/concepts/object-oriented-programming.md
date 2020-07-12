---
title: 物件導向程式設計 (C#)
ms.date: 05/13/2020
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: 83140a9dbd16f60f04f50ba18c71099cdd862f15
ms.sourcegitcommit: 67cf756b033c6173a1bbd1cbd5aef1fccac99e34
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2020
ms.locfileid: "86226630"
---
# <a name="object-oriented-programming-c"></a>物件導向程式設計 (c # ) 

C # 提供對面向物件程式設計的完整支援，包括抽象、封裝、繼承和多型。

- *抽象*表示隱藏型別取用者不必要的詳細資料。
- 「封裝」** 指的是將一組相關的屬性、方法和其他成員，視為單一單位或物件。
- 「繼承」** 則是描述依據現有類別來建立新類別的能力。
- 「多型」** 指的是您可以有多個交替使用的類別，即使每個類別是以不同的方式來實作相同的屬性或方法。

## <a name="classes-and-objects"></a>類別與物件

詞彙*類別*和*物件*會分別描述物件的*類型*和類別的*實例*。 因此，建立物件的動作稱為「具現化」**。 再以藍圖作比喻，若類別是藍圖，物件就是根據藍圖所蓋的建築物。

若要定義類別：

```csharp
class SampleClass
{
}
```

C # 也提供稱為*結構*的類型，當您不需要對繼承或多型的支援時很有用。 如需詳細資訊，請參閱[在類別和結構之間選擇](../../../standard/design-guidelines/choosing-between-class-and-struct.md)。

若要定義結構：

```csharp
struct SampleStruct
{
}
```

如需詳細資訊，請參閱[類別](../../language-reference/keywords/class.md)和[結構](../../language-reference/builtin-types/struct.md)關鍵字上的文章。

### <a name="class-members"></a>類別成員

每個類別都有不同的「類別成員」**，包括描述類別資料的屬性、定義類別行為的方法，以及提供不同類別與物件之間通訊的事件。

#### <a name="properties-and-fields"></a>屬性和欄位

欄位和屬性表示物件包含的資訊。 欄位就像變數一樣，因為它們可以直接讀取或設定，受限於適當的存取修飾詞。

若要定義可從類別的實例中存取的欄位：

```csharp
public class SampleClass
{
    string sampleField;
}
```

屬性具有 `get` 和 `set` 存取子，可對設定或傳回值的方式提供更多的控制。

C # 可讓您建立私用欄位來儲存屬性值，或使用自動執行的屬性，在幕後自動建立此欄位，並提供屬性程式的基本邏輯。

若要定義自動實作屬性：

```csharp
class SampleClass
{
    public int SampleProperty { get; set; }
}
```

如果您需要執行某些額外作業來讀取和寫入屬性值，請定義用來儲存屬性值的欄位，並提供儲存和擷取這個欄位的基本邏輯：

```csharp
class SampleClass
{
    private int _sample;
    public int Sample
    {
        // Return the value stored in a field.
        get => _sample;
        // Store the value in the field.
        set =>  _sample = value;
    }
}
```

大部分屬性都具有方法或程序，可以設定及取得屬性值。 但是您可以建立唯讀或唯寫屬性來限制不得修改或讀取。 在 C# 中，則可以省略 `get` 或 `set` 屬性方法。 不過，自動執行的屬性不能是寫入。 唯讀自動執行的屬性可以在包含類別的函式中設定。

如需詳細資訊，請參閱：

- [get](../../language-reference/keywords/get.md)
- [set](../../language-reference/keywords/set.md)

#### <a name="methods"></a>方法

「方法」** 是物件可執行的動作。

若要定義類別的方法：

```csharp
class SampleClass
{
    public int SampleMethod(string sampleParam)
    {
        // Insert code here
    }
}
```

類別可以有同一個方法的多個實作或「多載」**，但是這些實作的參數個數和參數類型並不相同。

若要多載方法：

```csharp
public int SampleMethod(string sampleParam) { }
public int SampleMethod(int sampleParam) { }
```

在多數情況下，您是在類別定義中宣告方法。 不過， C# 也支援「擴充方法」**，允許您在現有類別的實際定義之外將方法新增至類別。

如需詳細資訊，請參閱：

- [方法](../classes-and-structs/methods.md)
- [擴充方法](../classes-and-structs/extension-methods.md)

#### <a name="constructors"></a>建構函式

建構函式是類別方法，會在建立指定類型的物件時自動執行。 建構函式通常用來初始化新物件的資料成員， 而且只能在建立類別時執行一次。 此外，建構函式中的程式碼永遠會在類別中的任何其他程式碼執行之前執行。 不過，就和其他任何方法一樣，您可以建立多個建構函式多載。

若要定義類別的建構函式：

```csharp
public class SampleClass
{
    public SampleClass()
    {
        // Add code here
    }
}
```

如需詳細資訊，請參閱[建構函式](../classes-and-structs/constructors.md)。

#### <a name="finalizers"></a>完成項

完成項是用來終結類別的實例。 在 .NET 中，垃圾收集行程會自動管理應用程式中受管理物件的記憶體配置和釋放。 不過，您可能仍需要使用完成項來清除應用程式建立的任何 Unmanaged 資源。 一個類別只能有一個完成項。

如需 .NET 中完成項和垃圾收集的詳細資訊，請參閱[垃圾收集](../../../standard/garbage-collection/index.md)。

#### <a name="events"></a>事件

事件可讓類別或物件在某些相關的事情發生時，告知其他類別或物件。 傳送 (或引發) 事件的類別稱為「發行者」**，而接收 (或處理) 事件的類別則稱為「訂閱者」**。 如需事件的詳細資訊以及如何引發和處理事件，請參閱[處理和引發事件](../../../standard/events/index.md)。

- 若要宣告類別中的事件，請使用 [event](../../language-reference/keywords/event.md) 關鍵字。
- 要引發事件，請叫用事件委派。
- 若要訂閱事件，請使用 `+=` 運算子；若要取消訂閱事件，則使用 `-=` 運算子。

#### <a name="nested-classes"></a>嵌套類別

在類別中定義的另一個類別即稱為「巢狀」** 類別。 巢狀類別預設為私用。

```csharp
class Container
{
    class Nested
    {
        // Add code here.
    }
}
```

若要建立巢狀類別的執行個體，請使用容器類別名稱，後面加上點號，再接著巢狀類別名稱，如下所示：

```csharp
Container.Nested nestedInstance = new Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a>存取修飾詞與存取層級

所有類別及類別成員都可以使用「存取修飾詞」**，指定要提供給其他類別的存取層級。

下列為可用的存取修飾詞：

| C# 修飾詞 | 定義 |
|--|--|
| [public](../../language-reference/keywords/public.md) | 類型或成員可由相同組件或參考該組件的另一個組件中的任何其他程式碼存取。 |
| [私人](../../language-reference/keywords/private.md) | 類型或成員只能由相同類別中的程式碼存取。 |
| [受保護](../../language-reference/keywords/protected.md) | 類型或成員只能由相同類別中，或是衍生類別中的程式碼存取。 |
| [內部](../../language-reference/keywords/internal.md) | 類型或成員可由相同組件中的任何程式碼存取，但是不包括其他組件中的程式碼。 |
| [protected internal](../../language-reference/keywords/protected-internal.md) | 類型或成員可由相同組件中的任何程式碼，或是其他組件中的任何衍生類別存取。 |
| [private protected](../../language-reference/keywords/private-protected.md) | 只有在基底類別組件中，於相同類別或衍生類別內的程式碼才能存取類型或成員。 |

如需詳細資訊，請參閱[存取修飾詞](../classes-and-structs/access-modifiers.md)。

### <a name="instantiating-classes"></a>具現化類別

若要建立物件，您必須將類別執行個體化，或是建立類別執行個體。

```csharp
SampleClass sampleObject = new SampleClass();
```

將類別執行個體化之後，您就可以將值指派給執行個體的屬性和欄位，並叫用類別方法。

```csharp
// Set a property value.
sampleObject.sampleProperty = "Sample String";
// Call a method.
sampleObject.SampleMethod();
```

若要在類別執行個體化期間將值指派給屬性，請使用物件初始設定式：

```csharp
// Set a property value.
var sampleObject = new SampleClass
{
    FirstProperty = "A",
    SecondProperty = "B"
};
```

如需詳細資訊，請參閱：

- [new 運算子](../../language-reference/operators/new-operator.md)
- [物件和集合初始設定式](../classes-and-structs/object-and-collection-initializers.md)

### <a name="static-classes-and-members"></a>靜態類別與成員

類別的靜態成員是類別所有執行個體共用的屬性、程序或欄位。

定義靜態成員：

```csharp
static class SampleClass
{
    public static string SampleString = "Sample String";
}
```

若要存取靜態成員，請使用類別的名稱，但不要建立這個類別的物件：

```csharp
Console.WriteLine(SampleClass.SampleString);
```

C# 中的靜態類別只有靜態成員，且無法具現化。 靜態成員也無法存取非靜態屬性、欄位或方法

如需詳細資訊，請參閱[靜態](../../language-reference/keywords/static.md)。

### <a name="anonymous-types"></a>匿名型別

使用匿名類型建立物件時，您不需要撰寫資料類型的類別定義， 編譯器 (Compiler) 會自動幫您建立類別 (Class)。 這個類別沒有可使用的名稱，但是包含您在宣告物件時指定的屬性。

若要建立匿名類型的執行個體：

```csharp
// sampleObject is an instance of a simple anonymous type.
var sampleObject = new
{
    FirstProperty = "A",
    SecondProperty = "B"
};
```

如需詳細資訊，請參閱[匿名型別](../classes-and-structs/anonymous-types.md)。

## <a name="inheritance"></a>繼承

繼承可讓您建立新類別以重複使用、擴充和修改其他類別中定義的行為。 成員被繼承的類別稱為「基底類別」**，而繼承這種成員的類別即稱為「衍生類別」**。 不過，C# 中的所有類別都隱含繼承 <xref:System.Object> 類別，這個類別會支援 .NET 類別階層架構，並為所有類別提供低階服務。

> [!NOTE]
> C# 不支援多重繼承。 也就是說，您只能為衍生類別指定一個基底類別。

若要繼承基底類別：

```csharp
class DerivedClass:BaseClass { }
```

所有類別預設都可以被繼承。 不過，您可以指定類別是否不得當做基底類別，或是建立只能當做基底類別的類別。

若要指定類別不得當做基底類別使用：

```csharp
public sealed class A { }
```

若要指定類別只能當做基底類別且無法執行個體化：

```csharp
public abstract class B { }
```

如需詳細資訊，請參閱：

- [sealed](../../language-reference/keywords/sealed.md)
- [概要](../../language-reference/keywords/abstract.md)

### <a name="overriding-members"></a>覆寫成員

衍生類別預設會從其基底類別繼承所有成員。 如果想要變更所繼承成員的行為，您必須覆寫這個成員。 也就是說，您可以定義衍生類別中方法、屬性或事件的新實作。

下列修飾詞是用來控制如何覆寫屬性及方法：

| C# 修飾詞 | 定義 |
|--|--|
| [虛擬](../../language-reference/keywords/virtual.md) | 允許在衍生類別中覆寫類別成員。 |
| [覆寫](../../language-reference/keywords/override.md) | 覆寫在基底類別中定義的虛擬 (可覆寫) 成員。 |
| [概要](../../language-reference/keywords/abstract.md) | 要求在衍生類別中覆寫類別成員。 |
| [new 修飾詞](../../language-reference/keywords/new-modifier.md) | 隱藏繼承自基底類別的成員。 |

## <a name="interfaces"></a>介面

介面就像類別，可定義屬性、方法和事件集。 但與類別不同的是，介面並不提供實作。 介面是由類別實作，並定義為與類別不同的實體。 介面就代表著一種合約，因為實作介面的類別必須完全依介面的定義來實作這個介面的各個方面。

若要定義介面：

```csharp
interface ISampleInterface
{
    void DoSomething();
}
```

若要在類別中實作介面：

```csharp
class SampleClass : ISampleInterface
{
    void ISampleInterface.DoSomething()
    {
        // Method implementation.
    }
}
```

如需詳細資訊，請[參閱介面上](../interfaces/index.md)的程式設計指南一文和[interface](../../language-reference/keywords/interface.md)關鍵字上的語言參考文章。

## <a name="generics"></a>泛型

.NET 中的類別、結構、介面和方法可以包含定義可儲存或使用之物件類型的*類型參數*。 泛型最常見的範例是集合，您可以在其中指定要儲存於集合之物件的類型。

若要定義泛型類別：

```csharp
public class SampleGeneric<T>
{
    public T Field;
}
```

若要建立泛型類別的執行個體：

```csharp
var sampleObject = new SampleGeneric<string>();
sampleObject.Field = "Sample string";
```

如需詳細資訊，請參閱：

- [.NET 的泛型](../../../standard/generics/index.md)
- [泛型 - C# 程式設計手冊](../generics/index.md)

## <a name="delegates"></a>委派

「委派」** 是定義方法簽章的類型，可以提供任何具有相容簽章之方法的參考。 您可以透過委派叫用 (Invoke) 或呼叫方法。 委派可以用來將方法當做引數傳遞給其他方法。

> [!NOTE]
> 事件處理常式就是透過委派叫用的方法。 如需使用委派處理事件的詳細資訊，請參閱[處理和引發事件](../../../standard/events/index.md)。

若要建立委派：

```csharp
public delegate void SampleDelegate(string str);
```

若要建立與委派所指定簽章相符之方法的參考：

```csharp
class SampleClass
{
    // Method that matches the SampleDelegate signature.
    public static void SampleMethod(string message)
    {
        // Add code here.
    }

    // Method that instantiates the delegate.
    void SampleDelegate()
    {
        SampleDelegate sd = sampleMethod;
        sd("Sample string");
    }
}
```

如需詳細資訊，請[參閱委派](../../language-reference/builtin-types/reference-types.md)關鍵字上的程式設計指南[文章和語言](../delegates/index.md)參考文章。

## <a name="see-also"></a>另請參閱

- [C # 程式設計指南](../index.md)

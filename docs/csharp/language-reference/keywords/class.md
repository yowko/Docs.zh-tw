---
title: class 關鍵字 - C# 參考
ms.custom: seodec18
ms.date: 07/18/2017
f1_keywords:
- class_CSharpKeyword
- class
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
ms.openlocfilehash: 0c4fc9645e43f23e340804b46bbe8a5faa19525d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922395"
---
# <a name="class-c-reference"></a>類別 (C# 參考)

使用 `class` 關鍵字宣告類別，如下列範例所示︰

```csharp
class TestClass
{
    // Methods, properties, fields, events, delegates
    // and nested classes go here.
}
```

## <a name="remarks"></a>備註

僅允許在 C# 中使用單一繼承。 換句話說，類別可以只從一個基底類別繼承實作。 不過，類別可以實作多個介面。 下表顯示類別繼承和介面實作範例︰

|繼承|範例|
|-----------------|-------------|
|None|`class ClassA { }`|
|Single|`class DerivedClass: BaseClass { }`|
|無，實作兩個介面|`class ImplClass: IFace1, IFace2 { }`|
|單一，實作一個介面|`class ImplDerivedClass: BaseClass, IFace1 { }`|

直接在命名空間內宣告的類別 (未巢狀在其他類別內) 可以是 [public](./public.md) 或 [internal](./internal.md)。 類別預設為 `internal`。

類別成員 (包含巢狀類別) 可以是 [public](public.md)、[protected internal](protected-internal.md)、[protected](protected.md)、[internal](internal.md)、[private](private.md) 或 [private protected](private-protected.md)。 成員預設是 `private`。

如需詳細資訊，請參閱[存取修飾詞](../../programming-guide/classes-and-structs/access-modifiers.md)。

您可以宣告具有型別參數的泛型類別。 如需詳細資訊，請參閱[泛型類別](../../programming-guide/generics/generic-classes.md)。

類別可以包含下列成員的宣告︰

- [建構函式](../../programming-guide/classes-and-structs/constructors.md)

- [常數](../../programming-guide/classes-and-structs/constants.md)

- [欄位](../../programming-guide/classes-and-structs/fields.md)

- [完成項](../../programming-guide/classes-and-structs/destructors.md)

- [方法](../../programming-guide/classes-and-structs/methods.md)

- [屬性](../../programming-guide/classes-and-structs/properties.md)

- [索引子](../../programming-guide/indexers/index.md)

- [運算子](../operators/index.md)

- [事件](../../programming-guide/events/index.md)

- [委派](../../programming-guide/delegates/index.md)

- [類別](../../programming-guide/classes-and-structs/classes.md)

- [介面](../../programming-guide/interfaces/index.md)

- [結構](../../programming-guide/classes-and-structs/structs.md)

- [列舉](../../programming-guide/enumeration-types.md)

## <a name="example"></a>範例

下列範例示範如何宣告類別欄位、建構函式和方法。 它也會示範物件具現化和列印執行個體資料。 在此範例中，宣告兩個類別。 第一個類別 `Child`，包含兩個私用欄位 (`name` 和 `age`)、兩個公用建構函式和一個公用方法。 第二個類別 `StringTest` 是用來包含 `Main`。

[!code-csharp[csrefKeywordsTypes#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#5)]

## <a name="comments"></a>註解

請注意，在上述範例中，只能透過 `Child` 類別的公用方法來存取私用欄位 (`name` 和 `age`)。 例如，您無法使用如下的陳述式，從 `Main` 方法列印子系的名稱︰

```csharp
Console.Write(child1.name);   // Error
```

只有在 `Main` 已是類別的成員時，才能從 `Main` 存取 `Child` 的 private 成員。

類型已宣告在存取修飾詞未預設為 `private` 的類別內，因此，如果已移除關鍵字，則此範例中的資料成員仍然會是 `private`。

最後，請注意到針對使用無參數建構函式 (`child3`) 建立的物件，`age` 欄位預設已初始化為零。

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 關鍵字](./index.md)
- [參考型別](./reference-types.md)

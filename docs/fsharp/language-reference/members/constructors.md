---
title: 建構函式 (F#)
description: '了解如何定義及使用 F # 中的建構函式，建立和初始化類別和結構的物件。'
ms.date: 05/16/2016
ms.openlocfilehash: 1773c111e0398aa83951afe14979d8a4ebc4907f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="constructors"></a>建構函式

本主題描述如何定義及使用建構函式來建立和初始化類別和結構的物件。


## <a name="construction-of-class-objects"></a>類別物件的建構
類別類型的物件具有建構函式。 有兩種類型的建構函式。 其中一個是主要的建構函式，其參數的型別名稱的後方括號括住。 您可以指定其他、 選擇性的其他建構函式使用`new`關鍵字。 任何這類其他建構函式必須呼叫主要建構函式。

主要建構函式包含`let`和`do`繫結，都會出現在類別定義的開頭。 A`let`繫結宣告私用欄位和方法的類別;`do`繫結執行程式碼。 如需有關`let`繫結，在類別建構函式，請參閱[`let`類別中的繫結](let-bindings-in-classes.md)。 如需有關`do`繫結中建構函式，請參閱[`do`類別中的繫結](do-bindings-in-classes.md)。

不論您想要呼叫的建構函式是主要建構函式或其他建構函式，您可以建立物件，使用`new`運算式，或沒有包含選擇性`new`關鍵字。 初始化您的物件，以及建構函式引數，藉由列出的順序的引數，並以逗號分隔並括在括號內，或使用括號括住的具名引數和值。 您也可以設定屬性的物件上之物件的建構期間使用的屬性名稱，並指派值，就如同您使用名為建構函式引數。

下列程式碼說明具有建構函式和建立物件的各種方法的類別。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3501.fs)]

輸出如下。

```console
Initialized object that has coordinates (1, 2, 3)
Initialized object that has coordinates (4, 5, 6)
Initialized object that has coordinates (7, 8, 9)
Initialized object that has coordinates (0, 0, 0)
```

## <a name="construction-of-structures"></a>建立結構
結構遵循類別的所有規則。 因此，您可以擁有的主要建構函式，而且您可以使用，以提供其他建構函式`new`。 不過，沒有結構和類別之間的一個重要的差異： 結構可以具有預設建構函式 （也就是一個不含引數），即使沒有主要建構函式定義。 預設建構函式所有的欄位初始化成為該型別，通常是零或它的對等的預設值。 您為結構定義任何建構函式必須具有至少一個引數，如此他們不會衝突的預設建構函式。

此外，結構通常會有使用所建立的欄位`val`關鍵字; 類別也可以有這些欄位。 結構和類別定義使用的欄位`val`關鍵字也可以初始化其他建構函式中使用記錄運算式，如下列程式碼所示。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

如需詳細資訊，請參閱[明確欄位：`val`關鍵字](explicit-fields-the-val-keyword.md)。


## <a name="executing-side-effects-in-constructors"></a>在建構函式中執行的副作用
類別中的主要建構函式可以執行中的程式碼`do`繫結。 不過，如果您有執行程式碼中的其他建構函式，而不`do`繫結嗎？ 若要這樣做，您使用`then`關鍵字。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

仍然執行主要建構函式的副作用。 因此，輸出如下所示。

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

## <a name="self-identifiers-in-constructors"></a>建構函式中的自我識別項
其他成員，您會提供每個成員的定義中的目前物件的名稱。 您也可以使類別定義的第一行上自我識別項，利用`as`緊接建構函式參數的關鍵字。 下列範例說明這種語法。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

在其他建構函式，您也可以定義自我識別項將放入`as`子句之後的建構函式參數。 下列範例說明這種語法。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

當您嘗試在完整定義之前使用物件時，可能會發生問題。 因此，使用的自我識別項會導致編譯器發出警告，並且插入額外檢查以確保物件初始化之前，不會存取物件的成員。 您應該只使用自我識別項中的`do`繫結的主要建構函式，或之後`then`其他建構函式中的關鍵字。

自我識別項名稱不一定要`this`。 它可以是任何有效的識別項。


## <a name="assigning-values-to-properties-at-initialization"></a>將值指派給在初始化屬性
您可以初始化程式碼中的類別物件的屬性指派值，藉由附加一份格式的指派`property = value`的建構函式的引數清單。 這會顯示在以下程式碼範例中。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

先前的程式碼的下列版本說明一般引數、 選擇性引數和一個建構函式呼叫中的屬性設定的組合。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]
    
## <a name="constructors-in-inherited-class"></a>繼承的類別中建構函式
繼承自基底類別具有建構函式時，您必須在繼承子句中指定其引數。 如需詳細資訊，請參閱[建構函式和繼承](../inheritance.md#constructors-and-inheritance)。

## <a name="static-constructors-or-type-constructors"></a>靜態建構函式或類型建構函式
除了指定程式碼建立物件、 靜態`let`和`do`繫結可以用來撰寫執行之前的類型第一次用來執行初始設定類型層級的類別類型中。 如需詳細資訊，請參閱[`let`類別中的繫結](let-bindings-in-classes.md)和[`do`類別中的繫結](do-bindings-in-classes.md)。

## <a name="see-also"></a>另請參閱
[成員](index.md)

---
title: 'with expression-c # 參考'
description: '瞭解執行 c # 記錄之非破壞性變化的 with 運算式'
ms.date: 11/10/2020
f1_keywords:
- with_CSharpKeyword
helpviewer_keywords:
- with expression [C#]
- with operator [C#]
ms.openlocfilehash: 7948df3c6260e297cdb2fa380f1790a55e0abb58
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94445813"
---
# <a name="with-expression-c-reference"></a>with expression (c # 參考) 

在 c # 9.0 和更新版本中提供， `with` 運算式會產生其 [記錄](../../whats-new/csharp-9.md#record-types) 運算元的複本，並已修改指定的屬性和欄位：

:::code language="csharp" source="snippets/with-expression/BasicExample.cs" :::

如先前的範例所示，您可以使用 [物件初始化運算式](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) 語法來指定要修改的成員及其新值。 在 `with` 運算式中，左邊運算元必須是記錄類型。

如果是參考型別成員，則在複製記錄時，只會複製實例的參考。 複製和原始記錄都可以存取相同的參考型別實例。 下列範例示範了該行為：

:::code language="csharp" source="snippets/with-expression/ExampleWithReferenceType.cs" :::

任何記錄類型都有 *複製* 的函式。 這是具有包含記錄類型之單一參數的函式。 它會將其引數的狀態複製到新的記錄實例。 在評估運算式時 `with` ，會呼叫複製函式以根據原始記錄具現化新的記錄實例。 之後，會根據指定的修改更新新的實例。 根據預設，複製的函式是隱含的，也就是編譯器產生的。 如果您需要自訂記錄複製語義，請使用所需的行為明確宣告複製的函式。 下列範例會使用明確的複製函式來更新上述範例。 複製記錄時，新的複製行為是複製清單專案，而不是清單參考：

:::code language="csharp" source="snippets/with-expression/UserDefinedCopyConstructor.cs" :::

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱下列 [記錄功能的建議事項附注](~/_csharplang/proposals/csharp-9.0/records.md)：

- [`with` 表達](~/_csharplang/proposals/csharp-9.0/records.md#with-expression)
- [複製和複製成員](~/_csharplang/proposals/csharp-9.0/records.md#copy-and-clone-members)

## <a name="see-also"></a>請參閱

- [C# 參考資料](../index.md)
- [C# 運算子與運算式](index.md)

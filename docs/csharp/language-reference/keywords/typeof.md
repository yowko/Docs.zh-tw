---
title: typeof - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- typeof
- typeof_CSharpKeyword
helpviewer_keywords:
- typeof keyword [C#]
ms.assetid: 0c08d880-515e-46bb-8cd2-48b8dd62c08d
ms.openlocfilehash: 7962a3d0a5885e64701cb9d9a4d689cd982b9830
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422548"
---
# <a name="typeof-c-reference"></a>typeof (C# 參考)

用來取得類型的 <xref:System.Type?displayProperty=nameWithType> 物件。 `typeof` 運算式有下列形式：

```csharp
System.Type type = typeof(int);
```

## <a name="remarks"></a>備註

若要取得運算式的執行階段類型，您可以使用 .NET Framework 方法 <xref:System.Object.GetType%2A>，如下列範例所示︰

```csharp
int i = 0;
System.Type type = i.GetType();
```

無法多載 `typeof` 運算子。

`typeof` 運算子也可以用於開放式泛型型別。 在規格中，具有多個型別參數的類型必須具有適當數目的逗號。 例如，<xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWIthType> 有兩個型別引數，因此您會使用一個逗號：

```csharp
Type t = typeof(System.Collection.Generic.Dictionary<,>);
```

下列範例示範如何判斷方法的傳回型別是否為泛型 <xref:System.Collections.Generic.IEnumerable%601>。 如果傳回型別不是 <xref:System.Collections.Generic.IEnumerable%601> 泛型型別，<xref:System.Type.GetInterface%2A?displayProperty=nameWithType> 會傳回 `null`。

[!code-csharp[typeof_3.cs](~/samples/snippets/csharp/keywords/typeof/typeof_3.cs)]

## <a name="example"></a>範例

[!code-csharp[csrefKeywordsOperator#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#12)] 

## <a name="example"></a>範例

這個範例使用 <xref:System.Object.GetType%2A> 方法，判斷用來包含數值計算結果的類型。 這取決於所產生數字的儲存需求。

[!code-csharp[csrefKeywordsOperator#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#13)]

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的 [typeof 運算子](~/_csharplang/spec/expressions.md#the-typeof-operator)。 語言規格是 C# 語法及用法的限定來源。

## <a name="see-also"></a>另請參閱

- <xref:System.Type?displayProperty=nameWithType>
- [C# 參考](../../../csharp/language-reference/index.md)
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)
- [is](../../../csharp/language-reference/keywords/is.md)

---
title: dynamic - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- dynamic_CSharpKeyword
helpviewer_keywords:
- dynamic [C#]
- dynamic keyword [C#]
ms.assetid: 9e797102-cc83-4964-bf58-afe4f54d16bc
ms.openlocfilehash: 7ac9c04da277af6a03a6a8994763451146adefc8
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243305"
---
# <a name="dynamic-c-reference"></a>dynamic (C# 參考)

`dynamic` 類型可讓發生它的作業略過編譯時期類型檢查。 相反地，這些作業會在執行階段解決。 `dynamic` 類型會簡化 Office Automation API 這類 COM API 的存取、IronPython 程式庫這類動態 API 的存取，以及 HTML 文件物件模型 (DOM) 的存取。

在大多數情況下，`dynamic` 類型的行為與 `object` 類型類似。 不過，不會解決包含 `dynamic` 類型之運算式的作業，或編譯器不會對其進行類型檢查。 編譯器會將作業資訊封裝在一起，而且稍後在執行階段會使用這項資訊來評估作業。 在此程序期間，會將 `dynamic` 類型的變數編譯為 `object` 類型的變數。 因此，`dynamic` 類型只存在於編譯時期，而非執行階段。

下列範例會對照 `dynamic` 類型的變數與 `object` 類型的變數。 若要在編譯時期驗證每個變數的類型，請將滑鼠指標放在 `WriteLine` 陳述式中的 `dyn` 或 `obj` 上方。 IntelliSense 會顯示「動態」來表示 `dyn`，並顯示「物件」來表示 `obj`。

[!code-csharp[csrefKeywordsTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#21)]

`WriteLine` 陳述式會顯示執行階段類型 `dyn` 和 `obj`。 此時，兩者都有相同的類型：整數。 會產生下列輸出：

`System.Int32`

`System.Int32`

若要查看 `dyn` 與 `obj` 在編譯時期的差異，請在上述範例的宣告與 `WriteLine` 陳述式之間新增下列兩行。

```csharp
dyn = dyn + 3;
obj = obj + 3;
```

 嘗試新增運算式 `obj + 3` 中的整數和物件時報告編譯器錯誤。 不過，不會回報 `dyn + 3` 的錯誤。 在編譯時期不會檢查包含 `dyn` 的運算式，因為 `dyn` 的類型是 `dynamic`。

## <a name="context"></a>內容

在下列情況下，`dynamic` 關鍵字可能會直接出現，或作為建構類型的元件︰

- 在宣告中，作為屬性、欄位、索引子、參數、傳回值、區域變數或類型條件約束的類型。 下列類別定義在數個不同宣告中使用 `dynamic`。

    [!code-csharp[csrefKeywordsTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#22)]

- 在明確類型轉換中，作為轉換的目標類型。

    [!code-csharp[csrefKeywordsTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#23)]

- 在任何內容中，其中類型作為值 (例如 `is` 運算子或 `as` 運算子右側) 或作為部分建構類型之 `typeof` 的引數。 例如，`dynamic` 可以用於下列運算式中。

    [!code-csharp[csrefKeywordsTypes#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#24)]

## <a name="example"></a>範例

下列範例會在數個宣告中使用 `dynamic`。 `Main` 方法也會對照編譯時期類型檢查與執行階段類型檢查。

[!code-csharp[csrefKeywordsTypes#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic2.cs#25)]

如需詳細資訊和範例，請參閱[使用動態類型](../../../csharp/programming-guide/types/using-type-dynamic.md)。

## <a name="see-also"></a>另請參閱

- <xref:System.Dynamic.ExpandoObject?displayProperty=nameWithType>  
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>  
- [使用動態型別](../../../csharp/programming-guide/types/using-type-dynamic.md)  
- [object](../../../csharp/language-reference/keywords/object.md)  
- [is](../../../csharp/language-reference/keywords/is.md)  
- [as](../../../csharp/language-reference/keywords/as.md)  
- [typeof](../../../csharp/language-reference/keywords/typeof.md)  
- [如何：使用模式比對、is 和 as 運算子，安全地進行轉換](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)  
- [逐步解說：建立和使用動態物件](../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)

---
title: static 修飾詞 - C# 參考
ms.date: 01/22/2020
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: e7671e9db488a7b50f4ed736864d6fa8d95eef1a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744657"
---
# <a name="static-c-reference"></a>static (C# 參考)

使用 `static` 修飾詞來宣告靜態成員，而靜態成員屬於類型本身，而不是特定物件。 `static` 修飾詞可以用來宣告 `static` 類別。 在類別、介面和結構中，您可以將 `static` 修飾詞加入至欄位、方法、屬性、運算子、事件和函數。 `static` 修飾詞不能與索引子或完成項搭配使用。 如需詳細資訊，請參閱[靜態類別和靜態類別成員](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)。

## <a name="example"></a>範例

下列類別宣告為 `static`，並且只包含 `static` 方法：

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

常數或類型宣告隱含為 `static` 成員。 無法透過實例參考 `static` 成員。 相反地，它是透過型別名稱來參考。 例如，請參考下列類別：

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

若要參考 `static` 成員 `x`，請使用完整名稱 `MyBaseC.MyStruct.x`，除非可以從相同的範圍存取該成員：

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

雖然類別的實例包含類別的所有實例欄位的個別複本，但每個 `static` 欄位只有一個複本。

您無法使用[`this`](this.md)來參考 `static` 方法或屬性存取子。

如果 `static` 關鍵字套用至類別，則類別的所有成員都必須 `static`。

類別、介面和 `static` 類別可能會有 `static` 的構造函式。 在程式啟動和類別具現化的某個時間點，會呼叫 `static` 的函式。

> [!NOTE]
> `static` 關鍵字的使用方式比在 C++ 中受到更多限制。 若要與 C++ 關鍵字進行比較，請參閱[儲存類別 (C++)](/cpp/cpp/storage-classes-cpp#static)。

若要示範 `static` 成員，請考慮代表公司員工的類別。 假設此類別包含可計算員工人數的方法以及可儲存員工人數的欄位。 方法和欄位都不屬於任何一個員工實例。 相反地，它們屬於整個員工的類別。 它們應該宣告為類別的 `static` 成員。

## <a name="example"></a>範例

這個範例會讀取新員工的名稱和識別碼，並將員工計數器遞加一，然後顯示新員工和新員工人數的資訊。 此程式會從鍵盤讀取目前的員工人數。

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example"></a>範例

這個範例顯示您可以使用尚未宣告的另一個 `static` 欄位來初始化 `static` 欄位。 除非您明確地將值指派給 `static` 欄位，否則結果會是未定義的。

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 關鍵字](index.md)
- [修飾詞](index.md)
- [靜態類別和靜態類別成員](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)

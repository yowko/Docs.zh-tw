---
description: static 修飾詞 - C# 參考
title: static 修飾詞 - C# 參考
ms.date: 09/25/2020
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: 239163fc2f91ccbfe8b1c111a358db87d36a8308
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654635"
---
# <a name="static-c-reference"></a>static (C# 參考)

此頁面涵蓋 `static` 修飾詞關鍵字。 `static`關鍵字也是指示詞的一部分 [`using static`](using-static.md) 。

使用 `static` 修飾詞來宣告靜態成員，而靜態成員屬於類型本身，而不是特定物件。 `static`修飾詞可以用來宣告 `static` 類別。 在類別、介面和結構中，您可以將修飾詞加入 `static` 至欄位、方法、屬性、運算子、事件和函式。 `static`修飾元無法與索引子或完成項一起使用。 如需詳細資訊，請參閱 [靜態類別和靜態類別成員](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)。

從 c # 8.0 開始，您可以將 `static` 修飾詞加入至 [區域函數](../../programming-guide/classes-and-structs/local-functions.md)。 靜態區域函式無法捕捉本機變數或實例狀態。

從 c # 9.0 開始，您可以將 `static` 修飾詞加入至 [lambda 運算式](../operators/lambda-expressions.md) 或 [匿名方法](../operators/delegate-operator.md)。 靜態 lambda 或匿名方法無法捕捉本機變數或實例狀態。

## <a name="example---static-class"></a>範例-靜態類別

下列類別宣告為 `static`，並且只包含 `static` 方法：

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

常數或型別宣告是隱含的 `static` 成員。 `static`無法透過實例參考成員。 相反地，它是透過型別名稱來參考。 例如，請參考下列類別：

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

若要參考該 `static` 成員 `x` ，請使用完整名稱， `MyBaseC.MyStruct.x` 除非該成員可以從相同範圍存取：

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

雖然類別的實例包含類別的所有實例欄位的個別複本，但每個欄位只有一個複本 `static` 。

您無法使用 [`this`](this.md) 參考 `static` 方法或屬性存取子。

如果 `static` 關鍵字套用至類別，則類別的所有成員都必須是 `static` 。

類別、介面和 `static` 類別可能具有函式 `static` 。 在 `static` 程式啟動和具現化類別之間的某個時間點，會呼叫一個函數。

> [!NOTE]
> `static` 關鍵字的使用方式比在 C++ 中受到更多限制。 若要與 C++ 關鍵字進行比較，請參閱[儲存類別 (C++)](/cpp/cpp/storage-classes-cpp#static)。

若要示範 `static` 成員，請考慮代表公司員工的類別。 假設此類別包含可計算員工人數的方法以及可儲存員工人數的欄位。 方法和欄位都不屬於任何一個員工實例。 相反地，它們屬於整個員工的類別。 它們應該宣告為 `static` 類別的成員。

## <a name="example---static-field-and-method"></a>範例-靜態欄位和方法

這個範例會讀取新員工的名稱和識別碼，並將員工計數器遞加一，然後顯示新員工和新員工人數的資訊。 此程式會從鍵盤讀取目前的員工數目。

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example---static-initialization"></a>範例-靜態初始化

此範例顯示您可以使用尚未宣告的 `static` 其他欄位來初始化欄位 `static` 。 在您明確指派值給欄位之前，將不會定義結果 `static` 。

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- [C # 參考](../index.md)
- [C # 程式設計指南](../../programming-guide/index.md)
- [C # 關鍵字](index.md)
- [修飾詞](index.md)
- [using static 指示詞](using-static.md)
- [靜態類別和靜態類別成員](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)

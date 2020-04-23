---
title: static 修飾詞 - C# 參考
ms.date: 04/22/2020
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: 771bcfdac4c4bf27c15da4bc374d804405317a78
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102056"
---
# <a name="static-c-reference"></a>static (C# 參考)

此頁涵蓋`static`修改器關鍵字。 關鍵字`static`也是指令的[`using static`](using-static.md)一部分。

使用 `static` 修飾詞來宣告靜態成員，而靜態成員屬於類型本身，而不是特定物件。 修改`static`器可用於聲明`static`類。 在類、介面和結構中,您可以將`static`修改器添加到欄位、方法、屬性、運算符、事件和建構函數。 修改`static`器不能與索引器或終結器一起使用。 有關詳細資訊,請參閱[靜態類和靜態類成員](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)。

## <a name="example---static-class"></a>範例 ─靜態類別

下列類別宣告為 `static`，並且只包含 `static` 方法：

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

常量或類型聲明是隱式`static`成員。 無法透過`static`實例引用成員。 相反,它是通過類型名稱引用的。 例如，請參考下列類別：

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

要參考`static``x`成員 ,請使用完全限定的`MyBaseC.MyStruct.x`名稱, 除非成員可以從同一作用網域存取:

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

雖然類的實例包含類所有實例欄位的單獨副本,但每個`static`欄位只有一個副本。

不能用於[`this`](this.md)引用`static`方法或屬性訪問器。

如果關鍵字`static`應用於類,則類別的所有成員必須`static`為 。

類、介面和`static`類可能`static`具有構造函數。 在`static`程式啟動和類實例化之間的某個點調用構造函數。

> [!NOTE]
> `static` 關鍵字的使用方式比在 C++ 中受到更多限制。 若要與 C++ 關鍵字進行比較，請參閱[儲存類別 (C++)](/cpp/cpp/storage-classes-cpp#static)。

要演示`static`成員,請考慮代表公司員工的類。 假設此類別包含可計算員工人數的方法以及可儲存員工人數的欄位。 方法和欄位都不屬於任何一個員工實例。 相反,它們屬於整個員工階層。 應聲明它們為`static`類的成員。

## <a name="example---static-field-and-method"></a>範例 ─靜態欄位與方法

這個範例會讀取新員工的名稱和識別碼，並將員工計數器遞加一，然後顯示新員工和新員工人數的資訊。 此程式從鍵盤讀取當前員工人數。

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example---static-initialization"></a>範例 ─ 靜態初始化

此示例顯示可以使用尚未聲明的另一`static``static`個 欄位初始化欄位。 在顯式為欄位分配值之前,`static`結果將未定義。

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 編程指南](../../programming-guide/index.md)
- [C# 關鍵字](index.md)
- [修飾詞](index.md)
- [使用靜態指令](using-static.md)
- [靜態類別和靜態類別成員](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)

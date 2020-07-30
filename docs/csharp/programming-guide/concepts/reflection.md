---
title: 反映 (C#)
description: '反映會提供描述 c # 中元件、模組和類型的物件。 如果您的程式碼包含屬性，反映可讓您存取它們。'
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: 4d4f4c082dd2d58e212bae53524e5dd4fd06fb75
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302798"
---
# <a name="reflection-c"></a>反映 (C#)

反映提供 <xref:System.Type> 描述元件、模組和類型的物件（類型為）。 您可以使用反映來動態建立類型的執行個體、將類型繫結至現有的物件，或從現有的物件取得類型，並叫用其方法或存取其欄位及屬性。 如果您在程式碼中使用屬性，則反映可讓您存取它們。 如需詳細資訊，請參閱[屬性](../../../standard/attributes/index.md)。

以下是使用繼承自基類的所有類型之方法的簡單反映範例， <xref:System.Object.GetType> `Object` 以取得變數的類型：

> [!NOTE]
> 請確定您在 `using System;` `using System.Reflection;` *.cs*檔案的頂端新增和。

```csharp
// Using GetType to obtain type information:
int i = 42;
Type type = i.GetType();
Console.WriteLine(type);
```

輸出為： `System.Int32` 。

下列範例使用反映以取得所載入組件的完整名稱。

```csharp
// Using Reflection to get information of an Assembly:
Assembly info = typeof(int).Assembly;
Console.WriteLine(info);
```

輸出為： `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e` 。

> [!NOTE]
> C# 關鍵字 `protected` 和 `internal` 在 IL 中沒有任何意義，而且不會用於反映 API 中。 IL 中的對應詞彙是「系列」** 和「組件」**。 若要使用反映來識別 `internal` 方法，請使用 <xref:System.Reflection.MethodBase.IsAssembly%2A> 屬性。 若要識別 `protected internal` 方法，請使用 <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>。

## <a name="reflection-overview"></a>反映總覽

反映在下列情況下十分有用：

- 當您需要存取程式中繼資料中的屬性時。 如需詳細資訊，請參閱[擷取儲存於屬性中的資訊](../../../standard/attributes/retrieving-information-stored-in-attributes.md)。
- 如需檢查和具現化組件中的類型。
- 如需在執行階段建置新類型。 使用 <xref:System.Reflection.Emit> 中的類別。
- 對於執行晚期繫結，存取在執行階段建立的類型上的方法。 請參閱[動態載入和使用類型](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md)主題。

## <a name="related-sections"></a>相關章節

其他資訊：

- [反射](../../../framework/reflection-and-codedom/reflection.md)
- [檢視類型資訊](../../../framework/reflection-and-codedom/viewing-type-information.md)
- [反映和泛用類型](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)
- <xref:System.Reflection.Emit>
- [擷取儲存於屬性中的資訊](../../../standard/attributes/retrieving-information-stored-in-attributes.md)

## <a name="see-also"></a>另請參閱

- [C # 程式設計指南](../index.md)
- [.NET 中的組件](../../../standard/assembly/index.md)

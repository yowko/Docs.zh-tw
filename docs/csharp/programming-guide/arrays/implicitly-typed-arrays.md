---
title: 隱含類型陣列 - C# 程式設計手冊
description: 'C # 中的隱含型別陣列型別是從陣列初始化運算式中的元素推斷而來。 在查詢運算式中使用隱含類型陣列。'
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], implicitly-typed
- implicitly-typed arrays [C#]
- C# language, implicitly typed arrays
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
ms.openlocfilehash: 1f14f68207dfb79c92eaa01ac2a8ffaa08facc03
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474705"
---
# <a name="implicitly-typed-arrays-c-programming-guide"></a>隱含類型陣列 (C# 程式設計手冊)

您可以建立隱含型別陣列，其中陣列執行個體的類型是從陣列初始設定式中所指定的項目推斷而來。 任何隱含型別變數的規則也適用於隱含型別陣列。 如需詳細資訊，請參閱[隱含型別區域變數](../classes-and-structs/implicitly-typed-local-variables.md)。

隱含型別的陣列以及匿名型別與物件和集合初始設定式通常用於查詢運算式中。

下列範例示範如何建立隱含型別陣列：

[!code-csharp[csProgGuideLINQ#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#37)]

在上述範例中，請注意，使用隱含型別陣列時，在初始化陳述式左邊未使用方括弧。 也請注意不規則陣列是使用 `new []` 進行初始化，就像一維陣列一樣。

## <a name="implicitly-typed-arrays-in-object-initializers"></a>物件初始設定式中的隱含型別陣列

當您建立包含陣列的匿名型別時，在類型的物件初始設定式中，陣列必須是隱含型別。 在下列範例中，`contacts` 是隱含型別的匿名型別陣列，且每個都會包含名為 `PhoneNumbers` 的陣列。 請注意，`var` 關鍵字未用於物件初始設定式內。

[!code-csharp[csProgGuideLINQ#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#38)]

## <a name="see-also"></a>另請參閱

- [C # 程式設計指南](../index.md)
- [隱含類型區域變數](../classes-and-structs/implicitly-typed-local-variables.md)
- [陣列](./index.md)
- [匿名類型](../classes-and-structs/anonymous-types.md)
- [物件和集合初始設定式](../classes-and-structs/object-and-collection-initializers.md)
- [var](../../language-reference/keywords/var.md)
- [C# 中的 LINQ](../../linq/index.md)

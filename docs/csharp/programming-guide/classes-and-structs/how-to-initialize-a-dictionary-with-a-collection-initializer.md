---
title: 如何使用集合初始設定式來初始化字典 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 12/20/2018
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: acd426b7652705ff395df9a81cde8ef549af0e31
ms.sourcegitcommit: d09c77414e9e4fc72c79b04deee7a756a120674e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54084689"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a>如何：使用集合初始設定式來初始化字典 (C# 程式設計手冊)

<xref:System.Collections.Generic.Dictionary%602> 包含索引鍵/值組的集合。 其 <xref:System.Collections.Generic.Dictionary%602.Add*> 方法採用兩個參數，其中之一供索引鍵之用，而另一個則供值之用。 若要初始化 <xref:System.Collections.Generic.Dictionary%602> 或任何其 `Add` 方法採用多個參數的所有集合，其中一個方式是將每個參數集以大括弧括住，如下列範例所示。 另一個選項是使用索引子初始設定式，也會顯示在下列範例中。

## <a name="example"></a>範例

在下列程式碼範例中，<xref:System.Collections.Generic.Dictionary%602> 會使用類型 `StudentName` 的執行個體進行初始化。  第一個初始化使用 `Add` 方法和兩個引數。 編譯器會針對每組 `int` 索引鍵和 `StudentName` 值產生 `Add` 呼叫。 第二個使用 `Dictionary` 類別的公用讀取/寫入索引子方法：

[!code-csharp-interactive[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToDictionaryInitializer.cs#HowToDictionaryInitializer)]  

請注意，在第一個宣告中，該集合的每個項目中都有兩組大括弧。 最內層括號會括住 `StudentName` 的物件初始設定式，最外層括號會括住機碼值組，這組值會新增至 `students` <xref:System.Collections.Generic.Dictionary%602>。 最後，會以括號括住目錄的整個集合初始設定式。 在第二個初始化中，指派左側是索引鍵，右側是其值，並使用 `StudentName` 的物件初始設定式。

## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [物件和集合初始設定式](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)

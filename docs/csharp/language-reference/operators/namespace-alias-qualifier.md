---
description: ':: 運算子 - C# 參考'
title: ':: 運算子 - C# 參考'
ms.date: 08/09/2019
f1_keywords:
- ::_CSharpKeyword
- global_CSharpKeyword
- global
helpviewer_keywords:
- ':: operator [C#]'
- namespace alias qualifier [C#]
- namespace [C#]
- global keyword [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: 6c901ce083dde6f2e28520fafe3313071ae792c8
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89118321"
---
# <a name="-operator-c-reference"></a>:: 運算子 (C# 參考)

使用命名空間別名辨識符號 `::` 來存取別名命名空間的成員。 您只能在 `::` 兩個識別碼之間使用限定詞。 左邊的識別碼可以是下列任何別名：

- 使用 [using alias](../keywords/using-directive.md)指示詞建立的命名空間別名：

  ```csharp
  using forwinforms = System.Drawing;
  using forwpf = System.Windows;
  
  public class Converters
  {
      public static forwpf::Point Convert(forwinforms::Point point) => new forwpf::Point(point.X, point.Y);
  }
  ```

- [外部別名](../keywords/extern-alias.md)。
- `global` 別名，這是全域命名空間別名。 全域命名空間是包含未在具名命名空間中宣告之命名空間和型別的命名空間。 與 `::` 限定詞搭配使用時，`global` 別名一律會參考全域命名空間，即使有使用者定義的 `global` 命名空間別名也一樣。

  下列範例使用 `global` 別名來存取 .NET <xref:System> 命名空間，這是全域命名空間的成員。 如果沒有 `global` 別名，則會存取使用者定義的 `System` 命名空間，這是 `MyCompany.MyProduct` 命名空間的成員：

  ```csharp
  namespace MyCompany.MyProduct.System
  {
      class Program
      {
          static void Main() => global::System.Console.WriteLine("Using global alias");
      }

      class Console
      {
          string Suggestion => "Consider renaming this class";
      }
  }
  ```

  > [!NOTE]
  > `global` 關鍵字只有在它是 `::` 限定詞的左邊識別碼時，才是全域命名空間別名。

您也可以使用[ `.` 權杖](member-access-operators.md#member-access-expression-)來存取別名命名空間的成員。 不過， `.` 標記也用來存取類型成員。 `::` 限定詞可確保其左邊的識別碼一律會參考命名空間別名，即使存在具有相同名稱的型別或命名空間也一樣。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[命名空間別名限定詞](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers)一節。

## <a name="see-also"></a>另請參閱

- [C# 參考資料](../index.md)
- [C# 運算子與運算式](index.md)
- [使用命名空間](../../programming-guide/namespaces/using-namespaces.md)

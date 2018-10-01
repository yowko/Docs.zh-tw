---
title: 識別碼名稱
description: 了解 C# 程式設計語言中有效識別碼名稱的規則。
ms.date: 08/21/2018
ms.openlocfilehash: e5ff83661c9a86273760f32a795f7de6dbc7bf1d
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43877869"
---
# <a name="identifier-names"></a>識別碼名稱

**識別碼**是您為類型 (類別、介面、結構、委派或列舉)、成員、變數或命名空間指派的名稱。 有效的識別碼必須遵守下列規則：

- 識別碼必須以字母或 `_` 開頭。
- 識別碼可能包含 Unicode 字母字元、十進位數字字元、Unicode 連接字元、 Unicode 組合字元或 Unicode 格式化字元。 如需 Unicode 類別的詳細資訊，請參閱 [Unicode 類別資料庫](https://www.unicode.org/reports/tr44/)。
您可以使用識別碼上的 `@` 前置詞，宣告與 C# 關鍵字符合的識別碼。 `@` 不含在識別碼名稱內。 例如，`@if` 會宣告名為 `if` 的識別碼。 這些[逐字識別碼](../../language-reference/tokens/verbatim.md)的主要目的是與使用其他語言宣告的識別碼達成互通性。

如需有效識別碼的完整定義，請參閱 [C# 語言規格中的識別碼主題](../../../../_csharplang/spec/lexical-structure.md#identifiers)。

## <a name="naming-conventions"></a>命名規範

除了規則外，一些識別碼[命名慣例](../../../standard/design-guidelines/naming-guidelines.md)也用於 .NET API 中。 依照慣例，C# 程式針對類型名稱、命名空間和所有公用成員使用 `PascalCase`。 此外，常見慣例如下：

- 以大寫 `I` 開頭的介面名稱。
- 以單字 `Attribute` 結尾的屬性類型。
- 列舉類型會針對非旗標使用單一名詞，並針對旗標使用複數名詞。
- 識別碼不應包含連續兩個 `_` 字元。 這些名稱保留給編譯器產生的識別碼。

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>請參閱

- [C# 程式設計指南](../index.md)
- [C# 程式內部](../inside-a-program/index.md)
- [C# 參考](../../language-reference/index.md)
- [類別](../classes-and-structs/classes.md)
- [結構](../classes-and-structs/structs.md)
- [命名空間](../namespaces/index.md)
- [介面](../interfaces/index.md)
- [委派](../delegates/index.md)

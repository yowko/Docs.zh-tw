---
ms.openlocfilehash: 150882f3e4c9ff7abe811e09da94b8141de75778
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2020
ms.locfileid: "97366830"
---
### <a name="exclude-specific-types-and-their-derived-types"></a>排除特定類型及其衍生類型

您可以從分析中排除特定類型及其衍生類型。 例如，若要指定規則不應該在名為的型別和其衍生型別內的任何方法上執行 `MyType` ，請將下列機碼值組新增至專案中的 *editorconfig* 檔案：

```ini
dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType
```

選項值中允許的符號名稱格式 (以 `|`) 分隔：

- 僅限類型名稱 (包含名稱的所有類型，不論包含的類型或命名空間) 。
- 符號 [檔識別碼格式](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings)的完整名稱，加上選擇性的前置詞 `T:` 。

範例：

| 選項值 | 摘要 |
| --- | --- |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType` | 符合所有名稱 `MyType` 和所有衍生類型的類型。 |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType1|MyType2` | 會比對所有名稱為 `MyType1` 或的型別 `MyType2` ，以及它們的所有衍生類型。 |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = M:NS.MyType` | `MyType`使用指定的完整名稱和其所有衍生型別比對特定型別。 |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = M:NS1.MyType1|M:NS2.MyType2` | 符合特定 `MyType1` 型別和 `MyType2` 個別的完整名稱，以及它們的所有衍生類型。 |

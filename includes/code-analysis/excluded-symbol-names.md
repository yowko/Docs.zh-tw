---
ms.openlocfilehash: 83644b9205d650da68c910095dd1d22a14940c44
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2020
ms.locfileid: "97366841"
---
### <a name="exclude-specific-symbols"></a>排除特定符號

您可以從分析中排除特定符號，例如類型和方法。 例如，若要指定規則不應該在名為的型別內的任何程式碼上執行 `MyType` ，請將下列機碼值組新增至專案中的 *editorconfig* 檔案：

```ini
dotnet_code_quality.CAXXXX.excluded_symbol_names = MyType
```

選項值中允許的符號名稱格式 (以 `|`) 分隔：

- 符號名稱僅 (包含名稱的所有符號，不論包含的類型或命名空間) 。
- 符號 [檔識別碼格式](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings)的完整名稱。 每個符號名稱都需要符號種類的前置詞，例如 `M:` for 方法、 `T:` 類型和 `N:` 命名空間。
- `.ctor` 針對函式和靜態函式 `.cctor` 。

範例：

| 選項值 | 摘要 |
| --- | --- |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = MyType` | 符合所有名稱為 `MyType` 的符號。 |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = MyType1|MyType2` | 符合所有名稱為 `MyType1` 或 `MyType2` 的符號。 |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = M:NS.MyType.MyMethod(ParamType)` | 符合特定方法 `MyMethod` 與指定的完整簽章。 |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = M:NS1.MyType1.MyMethod1(ParamType)|M:NS2.MyType2.MyMethod2(ParamType)` | 符合特定方法 `MyMethod1` 和 `MyMethod2` 個別的完整簽章。 |

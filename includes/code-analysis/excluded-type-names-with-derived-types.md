---
ms.openlocfilehash: 4125df1d64fe7f3f2eb1eb4a821ed46c8270c95f
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97531899"
---
### <a name="exclude-specific-types-and-their-derived-types"></a><span data-ttu-id="e4992-101">排除特定類型及其衍生類型</span><span class="sxs-lookup"><span data-stu-id="e4992-101">Exclude specific types and their derived types</span></span>

<span data-ttu-id="e4992-102">您可以從分析中排除特定類型及其衍生類型。</span><span class="sxs-lookup"><span data-stu-id="e4992-102">You can exclude specific types and their derived types from analysis.</span></span> <span data-ttu-id="e4992-103">例如，若要指定規則不應該在名為的型別和其衍生型別內的任何方法上執行 `MyType` ，請將下列機碼值組新增至專案中的 *editorconfig* 檔案：</span><span class="sxs-lookup"><span data-stu-id="e4992-103">For example, to specify that the rule should not run on any methods within types named `MyType` and their derived types, add the following key-value pair to an *.editorconfig* file in your project:</span></span>

```ini
dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType
```

<span data-ttu-id="e4992-104">選項值中允許的符號名稱格式 (以 `|`) 分隔：</span><span class="sxs-lookup"><span data-stu-id="e4992-104">Allowed symbol name formats in the option value (separated by `|`):</span></span>

- <span data-ttu-id="e4992-105">僅限類型名稱 (包含名稱的所有類型，不論包含的類型或命名空間) 。</span><span class="sxs-lookup"><span data-stu-id="e4992-105">Type name only (includes all types with the name, regardless of the containing type or namespace).</span></span>
- <span data-ttu-id="e4992-106">符號 [檔識別碼格式](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings)的完整名稱，加上選擇性的前置詞 `T:` 。</span><span class="sxs-lookup"><span data-stu-id="e4992-106">Fully qualified names in the symbol's [documentation ID format](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings), with an optional `T:` prefix.</span></span>

<span data-ttu-id="e4992-107">範例：</span><span class="sxs-lookup"><span data-stu-id="e4992-107">Examples:</span></span>

| <span data-ttu-id="e4992-108">選項值</span><span class="sxs-lookup"><span data-stu-id="e4992-108">Option Value</span></span> | <span data-ttu-id="e4992-109">摘要</span><span class="sxs-lookup"><span data-stu-id="e4992-109">Summary</span></span> |
| --- | --- |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType` | <span data-ttu-id="e4992-110">符合所有名稱 `MyType` 和所有衍生類型的類型。</span><span class="sxs-lookup"><span data-stu-id="e4992-110">Matches all types named `MyType` and all of their derived types.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType1|MyType2` | <span data-ttu-id="e4992-111">會比對所有名稱為 `MyType1` 或的型別 `MyType2` ，以及它們的所有衍生類型。</span><span class="sxs-lookup"><span data-stu-id="e4992-111">Matches all types named either `MyType1` or `MyType2` and all of their derived types.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = M:NS.MyType` | <span data-ttu-id="e4992-112">`MyType`使用指定的完整名稱和其所有衍生型別比對特定型別。</span><span class="sxs-lookup"><span data-stu-id="e4992-112">Matches specific type `MyType` with given fully qualified name and all of its derived types.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = M:NS1.MyType1|M:NS2.MyType2` | <span data-ttu-id="e4992-113">符合特定 `MyType1` 型別和 `MyType2` 個別的完整名稱，以及它們的所有衍生類型。</span><span class="sxs-lookup"><span data-stu-id="e4992-113">Matches specific types `MyType1` and `MyType2` with the respective fully qualified names, and all of their derived types.</span></span> |

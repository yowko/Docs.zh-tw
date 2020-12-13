---
ms.openlocfilehash: 83644b9205d650da68c910095dd1d22a14940c44
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2020
ms.locfileid: "97366841"
---
### <a name="exclude-specific-symbols"></a><span data-ttu-id="2a826-101">排除特定符號</span><span class="sxs-lookup"><span data-stu-id="2a826-101">Exclude specific symbols</span></span>

<span data-ttu-id="2a826-102">您可以從分析中排除特定符號，例如類型和方法。</span><span class="sxs-lookup"><span data-stu-id="2a826-102">You can exclude specific symbols, such as types and methods, from analysis.</span></span> <span data-ttu-id="2a826-103">例如，若要指定規則不應該在名為的型別內的任何程式碼上執行 `MyType` ，請將下列機碼值組新增至專案中的 *editorconfig* 檔案：</span><span class="sxs-lookup"><span data-stu-id="2a826-103">For example, to specify that the rule should not run on any code within types named `MyType`, add the following key-value pair to an *.editorconfig* file in your project:</span></span>

```ini
dotnet_code_quality.CAXXXX.excluded_symbol_names = MyType
```

<span data-ttu-id="2a826-104">選項值中允許的符號名稱格式 (以 `|`) 分隔：</span><span class="sxs-lookup"><span data-stu-id="2a826-104">Allowed symbol name formats in the option value (separated by `|`):</span></span>

- <span data-ttu-id="2a826-105">符號名稱僅 (包含名稱的所有符號，不論包含的類型或命名空間) 。</span><span class="sxs-lookup"><span data-stu-id="2a826-105">Symbol name only (includes all symbols with the name, regardless of the containing type or namespace).</span></span>
- <span data-ttu-id="2a826-106">符號 [檔識別碼格式](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings)的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="2a826-106">Fully qualified names in the symbol's [documentation ID format](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings).</span></span> <span data-ttu-id="2a826-107">每個符號名稱都需要符號種類的前置詞，例如 `M:` for 方法、 `T:` 類型和 `N:` 命名空間。</span><span class="sxs-lookup"><span data-stu-id="2a826-107">Each symbol name requires a symbol-kind prefix, such as `M:` for methods, `T:` for types, and `N:` for namespaces.</span></span>
- <span data-ttu-id="2a826-108">`.ctor` 針對函式和靜態函式 `.cctor` 。</span><span class="sxs-lookup"><span data-stu-id="2a826-108">`.ctor` for constructors and `.cctor` for static constructors.</span></span>

<span data-ttu-id="2a826-109">範例：</span><span class="sxs-lookup"><span data-stu-id="2a826-109">Examples:</span></span>

| <span data-ttu-id="2a826-110">選項值</span><span class="sxs-lookup"><span data-stu-id="2a826-110">Option Value</span></span> | <span data-ttu-id="2a826-111">摘要</span><span class="sxs-lookup"><span data-stu-id="2a826-111">Summary</span></span> |
| --- | --- |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = MyType` | <span data-ttu-id="2a826-112">符合所有名稱為 `MyType` 的符號。</span><span class="sxs-lookup"><span data-stu-id="2a826-112">Matches all symbols named `MyType`.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = MyType1|MyType2` | <span data-ttu-id="2a826-113">符合所有名稱為 `MyType1` 或 `MyType2` 的符號。</span><span class="sxs-lookup"><span data-stu-id="2a826-113">Matches all symbols named either `MyType1` or `MyType2`.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = M:NS.MyType.MyMethod(ParamType)` | <span data-ttu-id="2a826-114">符合特定方法 `MyMethod` 與指定的完整簽章。</span><span class="sxs-lookup"><span data-stu-id="2a826-114">Matches specific method `MyMethod` with the specified fully qualified signature.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = M:NS1.MyType1.MyMethod1(ParamType)|M:NS2.MyType2.MyMethod2(ParamType)` | <span data-ttu-id="2a826-115">符合特定方法 `MyMethod1` 和 `MyMethod2` 個別的完整簽章。</span><span class="sxs-lookup"><span data-stu-id="2a826-115">Matches specific methods `MyMethod1` and `MyMethod2` with the respective fully qualified signatures.</span></span> |

---
ms.openlocfilehash: ada458ffeeba95d4989507f90c789b159f359797
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065133"
---
### <a name="ca1417-outattribute-on-string-parameter-for-pinvoke"></a><span data-ttu-id="75cb6-101">CA1417： P/Invoke 的字串參數上的 OutAttribute</span><span class="sxs-lookup"><span data-stu-id="75cb6-101">CA1417: OutAttribute on string parameter for P/Invoke</span></span>

<span data-ttu-id="75cb6-102">預設會啟用 .NET 程式碼分析器規則 [CA1417](/visualstudio/code-quality/ca1417) ，從 .net 5.0 開始。</span><span class="sxs-lookup"><span data-stu-id="75cb6-102">.NET code analyzer rule [CA1417](/visualstudio/code-quality/ca1417) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="75cb6-103">它會產生任何平台叫用的組建警告 [ (P/Invoke) ](../../../../docs/standard/native-interop/pinvoke.md) 方法定義，其中 <xref:System.String> 參數是以傳值方式傳遞，並以標記 <xref:System.Runtime.InteropServices.OutAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="75cb6-103">It produces a build warning for any [Platform Invoke (P/Invoke)](../../../../docs/standard/native-interop/pinvoke.md) method definitions where a <xref:System.String> parameter is passed by value and marked with <xref:System.Runtime.InteropServices.OutAttribute>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="75cb6-104">變更描述</span><span class="sxs-lookup"><span data-stu-id="75cb6-104">Change description</span></span>

<span data-ttu-id="75cb6-105">從 .NET 5.0 開始，.NET SDK 包含 [.net source 程式碼分析器](../../../../docs/fundamentals/productivity/code-analysis.md)。</span><span class="sxs-lookup"><span data-stu-id="75cb6-105">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../docs/fundamentals/productivity/code-analysis.md).</span></span> <span data-ttu-id="75cb6-106">預設會啟用這些規則中的數個，包括 [CA1417](/visualstudio/code-quality/ca1417)。</span><span class="sxs-lookup"><span data-stu-id="75cb6-106">Several of these rules are enabled, by default, including [CA1417](/visualstudio/code-quality/ca1417).</span></span> <span data-ttu-id="75cb6-107">如果您的專案包含違反此規則的程式碼，而且設定為將警告視為錯誤，這項變更可能會中斷您的組建。</span><span class="sxs-lookup"><span data-stu-id="75cb6-107">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="75cb6-108">規則 CA1417 會旗標 [P/Invoke](../../../../docs/standard/native-interop/pinvoke.md) 方法定義，其中 <xref:System.String> 參數標記為 <xref:System.Runtime.InteropServices.OutAttribute> 屬性，並以傳值方式傳遞。</span><span class="sxs-lookup"><span data-stu-id="75cb6-108">Rule CA1417 flags [P/Invoke](../../../../docs/standard/native-interop/pinvoke.md) method definitions where a <xref:System.String> parameter is marked with the <xref:System.Runtime.InteropServices.OutAttribute> attribute and is passed by value.</span></span> <span data-ttu-id="75cb6-109">例如：</span><span class="sxs-lookup"><span data-stu-id="75cb6-109">For example:</span></span>

```csharp
[DllImport("MyLibrary")]
private static extern void PIMethod([Out] string s);
```

<span data-ttu-id="75cb6-110">.NET 執行時間會維護名為實習集區的資料表，其中包含程式中每個唯一常值字串的單一參考。</span><span class="sxs-lookup"><span data-stu-id="75cb6-110">The .NET runtime maintains a table, called the intern pool, that contains a single reference to each unique literal string in a program.</span></span> <span data-ttu-id="75cb6-111">如果以傳值方式將標記為的留用字串 <xref:System.Runtime.InteropServices.OutAttribute> 以傳值方式傳遞至 P/Invoke 方法，則可以 destabilized 執行時間。</span><span class="sxs-lookup"><span data-stu-id="75cb6-111">If an interned string marked with <xref:System.Runtime.InteropServices.OutAttribute> is passed by value to a P/Invoke method, the runtime can be destabilized.</span></span> <span data-ttu-id="75cb6-112">如需有關字串暫留的詳細資訊，請參閱的備註 <xref:System.String.Intern(System.String)?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="75cb6-112">For more information about string interning, see the remarks for <xref:System.String.Intern(System.String)?displayProperty=nameWithType>.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="75cb6-113">引進的版本</span><span class="sxs-lookup"><span data-stu-id="75cb6-113">Version introduced</span></span>

<span data-ttu-id="75cb6-114">5.0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="75cb6-114">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="75cb6-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="75cb6-115">Recommended action</span></span>

- <span data-ttu-id="75cb6-116">如果您需要將修改過的字串資料封送處理回呼叫端，請改以傳址方式傳遞字串。</span><span class="sxs-lookup"><span data-stu-id="75cb6-116">If you need to marshal modified string data back to the caller, pass the string by reference instead.</span></span>

  ```csharp
  [DllImport("MyLibrary")]
  private static extern void PIMethod(out string s);
  ```

- <span data-ttu-id="75cb6-117">如果您不需要將修改過的字串資料封送處理回呼叫端，只要移除 <xref:System.Runtime.InteropServices.OutAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="75cb6-117">If you don't need to marshal modified string data back to the caller, simply remove the <xref:System.Runtime.InteropServices.OutAttribute>.</span></span>

  ```csharp
  [DllImport("MyLibrary")]
  private static extern void PIMethod(string s);
  ```

  <span data-ttu-id="75cb6-118">如需詳細資訊，請參閱 [CA1417](/visualstudio/code-quality/ca1417)。</span><span class="sxs-lookup"><span data-stu-id="75cb6-118">For more information, see [CA1417](/visualstudio/code-quality/ca1417).</span></span>

- <span data-ttu-id="75cb6-119">若要完全停用程式碼分析，請 `EnableNETAnalyzers` `false` 在您的專案檔中將設定為。</span><span class="sxs-lookup"><span data-stu-id="75cb6-119">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="75cb6-120">如需詳細資訊，請參閱 [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers)。</span><span class="sxs-lookup"><span data-stu-id="75cb6-120">For more information, see [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

#### <a name="category"></a><span data-ttu-id="75cb6-121">類別</span><span class="sxs-lookup"><span data-stu-id="75cb6-121">Category</span></span>

<span data-ttu-id="75cb6-122">程式碼分析</span><span class="sxs-lookup"><span data-stu-id="75cb6-122">Code analysis</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="75cb6-123">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="75cb6-123">Affected APIs</span></span>

<span data-ttu-id="75cb6-124">無法透過 API 分析偵測。</span><span class="sxs-lookup"><span data-stu-id="75cb6-124">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->

---
ms.openlocfilehash: c7500550cd9714a9788a7dea68af04823f000f7f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614376"
---
### <a name="stack-traces-obtained-when-using-portable-pdbs-now-include-source-file-and-line-information-if-requested"></a><span data-ttu-id="56246-101">使用可攜式 PDB 時取得的堆疊追蹤，現已包含來源檔案與程式碼資訊 (若要求)</span><span class="sxs-lookup"><span data-stu-id="56246-101">Stack traces obtained when using portable PDBs now include source file and line information if requested</span></span>

#### <a name="details"></a><span data-ttu-id="56246-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="56246-102">Details</span></span>

<span data-ttu-id="56246-103">從 .NET Framework 4.7.2 開始，如果要求，使用可攜式 PDB 時取得的堆疊追蹤會包含來源檔案與程式碼資訊。</span><span class="sxs-lookup"><span data-stu-id="56246-103">Starting with .NET Framework 4.7.2, stack traces obtained when using portable PDBs include source file and line information when requested.</span></span> <span data-ttu-id="56246-104">在 .NET Framework 4.7.2 之前的版本中，即使明確要求，使用可攜式 PDB 時也無法取得來源檔案和程式碼資訊。</span><span class="sxs-lookup"><span data-stu-id="56246-104">In versions prior to .NET Framework 4.7.2, source file and line information would be unavailable when using portable PDBs even if explicitly requested.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="56246-105">建議</span><span class="sxs-lookup"><span data-stu-id="56246-105">Suggestion</span></span>

<span data-ttu-id="56246-106">若為以 .NET Framework 4.7.2 為目標的應用程式，如果不需要，您可以透過將下列內容新增至 `app.config` 檔案的 `<runtime>` 區段，選擇使用可攜式 PDB 時不包含來源檔案和程式碼資訊︰</span><span class="sxs-lookup"><span data-stu-id="56246-106">For applications that target the .NET Framework 4.7.2, you can opt out of the source file and line information when using portable PDBs if it is not desirable by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=true" />
</runtime>
```

<span data-ttu-id="56246-107">若為以舊版 .NET Framework 為目標但卻在 .NET Framework 4.7.2 或更新版本上執行的應用程式，則可將下列內容新增至 `app.config` 檔案的 `<runtime>` 區段，選擇使用可攜式 PDB 時包含來源檔案和程式碼資訊︰</span><span class="sxs-lookup"><span data-stu-id="56246-107">For applications that target earlier versions of the .NET Framework but run on the .NET Framework 4.7.2 or later, you can opt in to the source file and line information when using portable PDBs by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=false" />
</runtime>
```

| <span data-ttu-id="56246-108">名稱</span><span class="sxs-lookup"><span data-stu-id="56246-108">Name</span></span>    | <span data-ttu-id="56246-109">值</span><span class="sxs-lookup"><span data-stu-id="56246-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="56246-110">影響範圍</span><span class="sxs-lookup"><span data-stu-id="56246-110">Scope</span></span>   | <span data-ttu-id="56246-111">Edge</span><span class="sxs-lookup"><span data-stu-id="56246-111">Edge</span></span>        |
| <span data-ttu-id="56246-112">版本</span><span class="sxs-lookup"><span data-stu-id="56246-112">Version</span></span> | <span data-ttu-id="56246-113">4.7.2</span><span class="sxs-lookup"><span data-stu-id="56246-113">4.7.2</span></span>       |
| <span data-ttu-id="56246-114">類型</span><span class="sxs-lookup"><span data-stu-id="56246-114">Type</span></span>    | <span data-ttu-id="56246-115">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="56246-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="56246-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="56246-116">Affected APIs</span></span>

- <xref:System.Diagnostics.StackTrace.%23ctor(System.Boolean)>
- <xref:System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Boolean)>
- <xref:System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Int32,System.Boolean)>

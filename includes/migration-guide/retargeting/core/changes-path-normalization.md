---
ms.openlocfilehash: 04c4fb4c8e9da8c58a5e26f78a7b13aa6a0df4a0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614340"
---
### <a name="changes-in-path-normalization"></a><span data-ttu-id="002b1-101">路徑正規化的變更</span><span class="sxs-lookup"><span data-stu-id="002b1-101">Changes in path normalization</span></span>

#### <a name="details"></a><span data-ttu-id="002b1-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="002b1-102">Details</span></span>

<span data-ttu-id="002b1-103">從以 .NET Framework 4.6.2 為目標的應用程式開始，執行階段正規化路徑的方式已變更。正規化路徑涉及修改識別路徑或檔案的字串，使它符合目標作業系統上的有效路徑。</span><span class="sxs-lookup"><span data-stu-id="002b1-103">Starting with apps that target the .NET Framework 4.6.2, the way in which the runtime normalizes paths has changed.Normalizing a path involves modifying the string that identifies a path or file so that it conforms to a valid path on the target operating system.</span></span> <span data-ttu-id="002b1-104">正規化通常牽涉到︰</span><span class="sxs-lookup"><span data-stu-id="002b1-104">Normalization typically involves:</span></span>

- <span data-ttu-id="002b1-105">規範化元件和目錄分隔符號。</span><span class="sxs-lookup"><span data-stu-id="002b1-105">Canonicalizing component and directory separators.</span></span>
- <span data-ttu-id="002b1-106">將目前的目錄套用到相對路徑。</span><span class="sxs-lookup"><span data-stu-id="002b1-106">Applying the current directory to a relative path.</span></span>
- <span data-ttu-id="002b1-107">評估路徑中的相對目錄 (.) 或上層目錄 (..)。</span><span class="sxs-lookup"><span data-stu-id="002b1-107">Evaluating the relative directory (.) or the parent directory (..) in a path.</span></span>
- <span data-ttu-id="002b1-108">修剪指定的字元。</span><span class="sxs-lookup"><span data-stu-id="002b1-108">Trimming specified characters.</span></span>
<span data-ttu-id="002b1-109">從以 .NET Framework 4.6.2 為目標的應用程式開始，預設會啟用路徑正規化的下列變更：</span><span class="sxs-lookup"><span data-stu-id="002b1-109">Starting with apps that target the .NET Framework 4.6.2, the following changes in path normalization are enabled by default:</span></span>
  - <span data-ttu-id="002b1-110">執行階段會延後至作業系統的 [GetFullPathName](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamew) 函式再進行路徑正規化。</span><span class="sxs-lookup"><span data-stu-id="002b1-110">The runtime defers to the operating system's [GetFullPathName](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamew) function to normalize paths.</span></span>
- <span data-ttu-id="002b1-111">正規化不再涉及修剪目錄區段的結尾 (例如目錄名稱結尾的空格)。</span><span class="sxs-lookup"><span data-stu-id="002b1-111">Normalization no longer involves trimming the end of directory segments (such as a space at the end of a directory name).</span></span>
- <span data-ttu-id="002b1-112">支援完全信任的裝置路徑語法，包括 `\\.\` 以及適用於 mscorlib.dll 中之檔案 I/O API 的 `\\?\`。</span><span class="sxs-lookup"><span data-stu-id="002b1-112">Support for device path syntax in full trust, including `\\.\` and, for file I/O APIs in mscorlib.dll, `\\?\`.</span></span>
- <span data-ttu-id="002b1-113">執行階段不會驗證裝置語法路徑。</span><span class="sxs-lookup"><span data-stu-id="002b1-113">The runtime does not validate device syntax paths.</span></span>
- <span data-ttu-id="002b1-114">支援使用裝置語法存取替代資料流。</span><span class="sxs-lookup"><span data-stu-id="002b1-114">The use of device syntax to access alternate data streams is supported.</span></span>
<span data-ttu-id="002b1-115">這些變更可改善效能，同時允許方法存取先前無法存取的路徑。</span><span class="sxs-lookup"><span data-stu-id="002b1-115">These changes improve performance while allowing methods to access previously inaccessible paths.</span></span> <span data-ttu-id="002b1-116">此變更不會影響以 .NET Framework 4.6.1 和舊版為目標但執行於 .NET Framework 4.6.2 或更新版本下的應用程式。</span><span class="sxs-lookup"><span data-stu-id="002b1-116">Apps that target the .NET Framework 4.6.1 and earlier versions but are running under the .NET Framework 4.6.2 or later are unaffected by this change.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="002b1-117">建議</span><span class="sxs-lookup"><span data-stu-id="002b1-117">Suggestion</span></span>

<span data-ttu-id="002b1-118">以 .NET Framework 4.6.2 或更新版本為目標的應用程式可透過在應用程式設定檔的 `<runtime>` 區段中新增下列內容來選擇退出此變更，並使用舊版行為：</span><span class="sxs-lookup"><span data-stu-id="002b1-118">Apps that target the .NET Framework 4.6.2 or later can opt out of this change and use legacy normalization by adding the following to the `<runtime>` section of the application configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
</runtime>
```

<span data-ttu-id="002b1-119">以 .NET Framework 4.6.1 或更早版本為目標，但在 .NET Framework 4.6.2 或更新版本上執行的應用程式，可以藉由在應用程式設定檔的 `<runtime>` 區段新增下行，就能啟用路徑正規化的變更：</span><span class="sxs-lookup"><span data-stu-id="002b1-119">Apps that target the .NET Framework 4.6.1 or earlier but are running on the .NET Framework 4.6.2 or later can enable the changes to path normalization by adding the following line to the `<runtime>` section of the application .configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />
</runtime>
```

| <span data-ttu-id="002b1-120">名稱</span><span class="sxs-lookup"><span data-stu-id="002b1-120">Name</span></span>    | <span data-ttu-id="002b1-121">值</span><span class="sxs-lookup"><span data-stu-id="002b1-121">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="002b1-122">影響範圍</span><span class="sxs-lookup"><span data-stu-id="002b1-122">Scope</span></span>   | <span data-ttu-id="002b1-123">Minor</span><span class="sxs-lookup"><span data-stu-id="002b1-123">Minor</span></span>       |
| <span data-ttu-id="002b1-124">版本</span><span class="sxs-lookup"><span data-stu-id="002b1-124">Version</span></span> | <span data-ttu-id="002b1-125">4.6.2</span><span class="sxs-lookup"><span data-stu-id="002b1-125">4.6.2</span></span>       |
| <span data-ttu-id="002b1-126">類型</span><span class="sxs-lookup"><span data-stu-id="002b1-126">Type</span></span>    | <span data-ttu-id="002b1-127">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="002b1-127">Retargeting</span></span> |

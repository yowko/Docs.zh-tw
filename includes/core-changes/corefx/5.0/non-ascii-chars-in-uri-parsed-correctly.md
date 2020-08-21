---
ms.openlocfilehash: faf9459ab9002e6149560e2a3452265fa246bf6b
ms.sourcegitcommit: ef86c24c418439b8bb5e3e7d64bbdbe5e11c3e9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2020
ms.locfileid: "88720180"
---
### <a name="uri-paths-with-non-ascii-characters-parse-correctly-on-unix"></a><span data-ttu-id="db63a-101">在 Unix 上正確剖析非 ASCII 字元的 URI 路徑</span><span class="sxs-lookup"><span data-stu-id="db63a-101">URI paths with non-ASCII characters parse correctly on Unix</span></span>

<span data-ttu-id="db63a-102">修正了類別中的 bug <xref:System.Uri?displayProperty=fullName> ，讓包含非 ASCII 字元的絕對 URI 路徑現在在 Unix 平臺上正確地進行剖析。</span><span class="sxs-lookup"><span data-stu-id="db63a-102">A bug was fixed in the <xref:System.Uri?displayProperty=fullName> class such that absolute URI paths that contain non-ASCII characters now parse correctly on Unix platforms.</span></span>

#### <a name="change-description"></a><span data-ttu-id="db63a-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="db63a-103">Change description</span></span>

<span data-ttu-id="db63a-104">在舊版的 .NET 中，包含非 ASCII 字元的絕對 URI 路徑在 Unix 平臺上不正確地剖析，而且會複製路徑的區段。</span><span class="sxs-lookup"><span data-stu-id="db63a-104">In previous versions of .NET, absolute URI paths that contain non-ASCII characters are parsed incorrectly on Unix platforms, and segments of the path are duplicated.</span></span> <span data-ttu-id="db63a-105"> (絕對路徑是以 "/" 開頭的路徑。 ) 已修正 .NET 5.0 的剖析問題。</span><span class="sxs-lookup"><span data-stu-id="db63a-105">(Absolute paths are those that start with "/".) The parsing issue has been fixed for .NET 5.0.</span></span> <span data-ttu-id="db63a-106">如果您從舊版的 .NET 移至 .NET 5.0 或更新版本，則會取得 <xref:System.Uri.AbsoluteUri?displayProperty=nameWithType> 、 <xref:System.Uri.ToString?displayProperty=nameWithType> 和其他成員所產生的不同值 <xref:System.Uri> 。</span><span class="sxs-lookup"><span data-stu-id="db63a-106">If you move from a previous version of .NET to .NET 5.0 or later, you'll get different values produced by <xref:System.Uri.AbsoluteUri?displayProperty=nameWithType>, <xref:System.Uri.ToString?displayProperty=nameWithType>, and other <xref:System.Uri> members.</span></span>

<span data-ttu-id="db63a-107">在 Unix 上執行時，請考慮下列程式碼的輸出。</span><span class="sxs-lookup"><span data-stu-id="db63a-107">Consider the output of the following code when run on Unix.</span></span>

```csharp
var myUri = new Uri("/üri");

Console.WriteLine($"AbsoluteUri: {myUri.AbsoluteUri}");
Console.WriteLine($"ToString: {myUri.ToString()}");
```

<span data-ttu-id="db63a-108">先前 .NET 版本的輸出：</span><span class="sxs-lookup"><span data-stu-id="db63a-108">Output on previous .NET version:</span></span>

```text
AbsoluteUri: /%C3%BCri/%C3%BCri
ToString: /üri/üri
```

<span data-ttu-id="db63a-109">.NET 5.0 或更新版本的輸出：</span><span class="sxs-lookup"><span data-stu-id="db63a-109">Output on .NET 5.0 or later version:</span></span>

```text
AbsoluteUri: /%C3%BCri
ToString: /üri
```

#### <a name="version-introduced"></a><span data-ttu-id="db63a-110">引進的版本</span><span class="sxs-lookup"><span data-stu-id="db63a-110">Version introduced</span></span>

<span data-ttu-id="db63a-111">5.0</span><span class="sxs-lookup"><span data-stu-id="db63a-111">5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="db63a-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="db63a-112">Recommended action</span></span>

<span data-ttu-id="db63a-113">如果您有需要的程式碼，以及重複路徑區段的帳戶，您可以移除該程式碼。</span><span class="sxs-lookup"><span data-stu-id="db63a-113">If you have code that expects and accounts for the duplicated path segments, you can remove that code.</span></span>

#### <a name="category"></a><span data-ttu-id="db63a-114">類別</span><span class="sxs-lookup"><span data-stu-id="db63a-114">Category</span></span>

<span data-ttu-id="db63a-115">Core .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="db63a-115">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="db63a-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="db63a-116">Affected APIs</span></span>

- <xref:System.Uri?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Uri`

-->

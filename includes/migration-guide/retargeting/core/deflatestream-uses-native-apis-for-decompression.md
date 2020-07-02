---
ms.openlocfilehash: 7e42a294b151d07a6fdc61308cdf92df7a31a1d6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614352"
---
### <a name="deflatestream-uses-native-apis-for-decompression"></a><span data-ttu-id="6d6d2-101">DeflateStream 使用原生 API 解壓縮</span><span class="sxs-lookup"><span data-stu-id="6d6d2-101">DeflateStream uses native APIs for decompression</span></span>

#### <a name="details"></a><span data-ttu-id="6d6d2-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="6d6d2-102">Details</span></span>

<span data-ttu-id="6d6d2-103">從 .NET Framework 4.7.2 開始，`T:System.IO.Compression.DeflateStream` 類別中的解壓縮實作已變更為預設使用原生 Windows API。</span><span class="sxs-lookup"><span data-stu-id="6d6d2-103">Starting with the .NET Framework 4.7.2, the implementation of decompression in the `T:System.IO.Compression.DeflateStream` class has changed to use native Windows APIs by default.</span></span> <span data-ttu-id="6d6d2-104">一般而言，這會導致顯著的效能改善。</span><span class="sxs-lookup"><span data-stu-id="6d6d2-104">Typically, this results in a substantial performance improvement.</span></span> <span data-ttu-id="6d6d2-105">所有以 .NET Framework 4.7.2 或更高版本為目標的 .NET 應用程式都會使用原生實作。這項變更可能會導致行為的某些差異，包括：</span><span class="sxs-lookup"><span data-stu-id="6d6d2-105">All .NET applications targeting the .NET Framework version 4.7.2 or higher use the native implementation.This change might result in some differences in behavior, which include:</span></span>

- <span data-ttu-id="6d6d2-106">例外狀況訊息可能會不同。</span><span class="sxs-lookup"><span data-stu-id="6d6d2-106">Exception messages may be different.</span></span> <span data-ttu-id="6d6d2-107">不過，擲回的例外狀況類型維持不變。</span><span class="sxs-lookup"><span data-stu-id="6d6d2-107">However, the type of exception thrown remains the same.</span></span>
- <span data-ttu-id="6d6d2-108">某些特殊情況下，例如記憶體不足無法完成作業，可能會以不同的方式處理。</span><span class="sxs-lookup"><span data-stu-id="6d6d2-108">Some special situations, such as not having enough memory to complete an operation, may be handled differently.</span></span>
- <span data-ttu-id="6d6d2-109">剖析 gzip 標頭的已知差異 (注意：只有針對解壓縮設定的 `GZipStream` 會受到影響)：</span><span class="sxs-lookup"><span data-stu-id="6d6d2-109">There are known differences for parsing gzip header (note: only `GZipStream` set for decompression is affected):</span></span>
- <span data-ttu-id="6d6d2-110">剖析無效標頭時的例外狀況，可能會在不同的時間擲回。</span><span class="sxs-lookup"><span data-stu-id="6d6d2-110">Exceptions when parsing invalid headers may be thrown at different times.</span></span>
- <span data-ttu-id="6d6d2-111">原生實作強制執行的 gzip 標頭內某些保留旗標值 (亦即 [FLG](http://www.zlib.org/rfc-gzip.html#header-trailer))，會根據規格設定，這可能會造成它擲回略過先前無效值的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6d6d2-111">The native implementation enforces that values for some reserved flags inside the gzip header (i.e. [FLG](http://www.zlib.org/rfc-gzip.html#header-trailer)) are set according to the specification, which may cause it to throw an exception where previously invalid values were ignored.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6d6d2-112">建議</span><span class="sxs-lookup"><span data-stu-id="6d6d2-112">Suggestion</span></span>

<span data-ttu-id="6d6d2-113">如果使用原生 API 解壓縮對您的應用程式行為有不良影響，您可以在 app.config 檔案的 `runtime` 區段中新增 `Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression` 參數，並將它設定為 `true`，選擇不使用這項功能：</span><span class="sxs-lookup"><span data-stu-id="6d6d2-113">If decompression with native APIs has adversely affected the behavior of your app, you can opt out of this feature by adding the `Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression` switch to the `runtime` section of your app.config file and setting it to `true`:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression=true" />
  </runtime>
</configuration>
```

| <span data-ttu-id="6d6d2-114">名稱</span><span class="sxs-lookup"><span data-stu-id="6d6d2-114">Name</span></span>    | <span data-ttu-id="6d6d2-115">值</span><span class="sxs-lookup"><span data-stu-id="6d6d2-115">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6d6d2-116">影響範圍</span><span class="sxs-lookup"><span data-stu-id="6d6d2-116">Scope</span></span>   | <span data-ttu-id="6d6d2-117">Minor</span><span class="sxs-lookup"><span data-stu-id="6d6d2-117">Minor</span></span>       |
| <span data-ttu-id="6d6d2-118">版本</span><span class="sxs-lookup"><span data-stu-id="6d6d2-118">Version</span></span> | <span data-ttu-id="6d6d2-119">4.7.2</span><span class="sxs-lookup"><span data-stu-id="6d6d2-119">4.7.2</span></span>       |
| <span data-ttu-id="6d6d2-120">類型</span><span class="sxs-lookup"><span data-stu-id="6d6d2-120">Type</span></span>    | <span data-ttu-id="6d6d2-121">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="6d6d2-121">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="6d6d2-122">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="6d6d2-122">Affected APIs</span></span>

- <xref:System.IO.Compression.DeflateStream?displayProperty=nameWithType>
- <xref:System.IO.Compression.GZipStream?displayProperty=nameWithType>

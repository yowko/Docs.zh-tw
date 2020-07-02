---
ms.openlocfilehash: 148312743dd274728b178951548889dc3a680528
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614341"
---
### <a name="change-in-path-separator-character-in-fullname-property-of-ziparchiveentry-objects"></a><span data-ttu-id="6b18e-101">ZipArchiveEntry 物件的 FullName 屬性中路徑分隔符號字元變更</span><span class="sxs-lookup"><span data-stu-id="6b18e-101">Change in path separator character in FullName property of ZipArchiveEntry objects</span></span>

#### <a name="details"></a><span data-ttu-id="6b18e-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="6b18e-102">Details</span></span>

<span data-ttu-id="6b18e-103">針對以 .NET Framework 4.6.1 和更新版本為目標的應用程式，在方法的多載所建立之物件的屬性中，路徑分隔符號已從反斜線（" \" ）變更為正斜線（"/"） <xref:System.IO.Compression.ZipArchiveEntry.FullName> <xref:System.IO.Compression.ZipArchiveEntry> <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A> 。</span><span class="sxs-lookup"><span data-stu-id="6b18e-103">For apps that target the .NET Framework 4.6.1 and later versions, the path separator character has changed from a backslash ("\") to a forward slash ("/") in the <xref:System.IO.Compression.ZipArchiveEntry.FullName> property of <xref:System.IO.Compression.ZipArchiveEntry>  objects created by overloads of the <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A> method.</span></span> <span data-ttu-id="6b18e-104">這項變更使得 .NET 實作遵守 [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) (.ZIP 檔案格式規格) 的 4.4.17.1 小節，並允許在非 Windows 系統上解壓縮 ZIP 封存。</span><span class="sxs-lookup"><span data-stu-id="6b18e-104">The change brings the .NET implementation into conformity with section 4.4.17.1 of the [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) and allows .ZIP archives to be decompressed on non-Windows systems.</span></span><br /><span data-ttu-id="6b18e-105">在非 Windows 作業系統 (例如 Macintosh) 上解壓縮以舊版 .NET Framework 為目標的應用程式所建立的 ZIP 檔案，會無法保留目錄結構。</span><span class="sxs-lookup"><span data-stu-id="6b18e-105">Decompressing a zip file created by an app that targets a previous version of the .NET Framework on non-Windows operating systems such as the Macintosh fails to preserve the directory structure.</span></span> <span data-ttu-id="6b18e-106">例如，在 Macintosh 上，它會建立一組檔案，其檔案名稱會串連目錄路徑，以及任何反斜線 () 字元和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="6b18e-106">For example, on the Macintosh, it creates a set of files whose filename concatenates the directory path, along with any backslash ("") characters, and the filename.</span></span> <span data-ttu-id="6b18e-107">因此，解壓縮檔案的目錄結構會無法保留。</span><span class="sxs-lookup"><span data-stu-id="6b18e-107">As a result, the directory structure of decompressed files is not preserved.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6b18e-108">建議</span><span class="sxs-lookup"><span data-stu-id="6b18e-108">Suggestion</span></span>

<span data-ttu-id="6b18e-109">這項變更對的影響。在 Windows 作業系統上，由 .NET Framework 命名空間中的 Api 解壓縮的 ZIP 檔案 <xref:System.IO?displayProperty=nameWithType> 應該很小，因為這些 api 可以順暢地處理正斜線（"/"）或反斜線（" \" ）做為路徑分隔符號。</span><span class="sxs-lookup"><span data-stu-id="6b18e-109">The impact of this change on .ZIP files that are decompressed on the Windows operating system by APIs in the .NET Framework <xref:System.IO?displayProperty=nameWithType> namespace should be minimal, since these APIs can seamlessly handle either a forward slash ("/") or a backslash ("\") as the path separator character.</span></span><br /><span data-ttu-id="6b18e-110">如果不需要這項變更，您可以新增設定至 [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 應用程式佈建檔的區段，以退出宣告。</span><span class="sxs-lookup"><span data-stu-id="6b18e-110">If this change is undesirable, you can opt out of it by adding a configuration setting to the [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file.</span></span> <span data-ttu-id="6b18e-111">下列範例顯示 `<runtime>` 區段及 `Switch.System.IO.Compression.ZipFile.UseBackslash` 選擇退出參數：</span><span class="sxs-lookup"><span data-stu-id="6b18e-111">The following example shows both the `<runtime>` section and the `Switch.System.IO.Compression.ZipFile.UseBackslash` opt-out switch:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />
</runtime>
```

<span data-ttu-id="6b18e-112">此外，以舊版 .NET Framework 為目標但在 .NET Framework 4.6.1 和更新版本上執行的應用程式，可以藉由新增設定至 [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 應用程式佈建檔的區段，來加入宣告此行為。</span><span class="sxs-lookup"><span data-stu-id="6b18e-112">In addition, apps that target previous versions of the .NET Framework but are running on the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding a configuration setting to the [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file.</span></span> <span data-ttu-id="6b18e-113">下圖顯示 `<runtime>` 區段及 `Switch.System.IO.Compression.ZipFile.UseBackslash` 選擇加入參數。</span><span class="sxs-lookup"><span data-stu-id="6b18e-113">The following shows both the `<runtime>` section and the `Switch.System.IO.Compression.ZipFile.UseBackslash` opt-in switch.</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />
</runtime>
```

| <span data-ttu-id="6b18e-114">名稱</span><span class="sxs-lookup"><span data-stu-id="6b18e-114">Name</span></span>    | <span data-ttu-id="6b18e-115">值</span><span class="sxs-lookup"><span data-stu-id="6b18e-115">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6b18e-116">影響範圍</span><span class="sxs-lookup"><span data-stu-id="6b18e-116">Scope</span></span>   | <span data-ttu-id="6b18e-117">Edge</span><span class="sxs-lookup"><span data-stu-id="6b18e-117">Edge</span></span>        |
| <span data-ttu-id="6b18e-118">版本</span><span class="sxs-lookup"><span data-stu-id="6b18e-118">Version</span></span> | <span data-ttu-id="6b18e-119">4.6.1</span><span class="sxs-lookup"><span data-stu-id="6b18e-119">4.6.1</span></span>       |
| <span data-ttu-id="6b18e-120">類型</span><span class="sxs-lookup"><span data-stu-id="6b18e-120">Type</span></span>    | <span data-ttu-id="6b18e-121">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="6b18e-121">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="6b18e-122">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="6b18e-122">Affected APIs</span></span>

- <xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String)?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String,System.IO.Compression.CompressionLevel,System.Boolean)?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String,System.IO.Compression.CompressionLevel,System.Boolean,System.Text.Encoding)?displayProperty=nameWithType>

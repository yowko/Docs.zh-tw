---
title: 風險降低：ZipArchiveEntry.FullName 路徑分隔符號
ms.date: 03/30/2017
helpviewer_keywords:
- application compatibility
- ',NET Framework application compatibility'
- .NET Framework 4.6.1
- .NET Framework 4.6.1 retargeting changes
- retargeting changes
ms.assetid: 8d575722-4fb6-49a2-8a06-f72d62dc3766
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 908ac7c441dbb7f6c70b9fafc701d403fc153222
ms.sourcegitcommit: 26f4a7697c32978f6a328c89dc4ea87034065989
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/28/2019
ms.locfileid: "66251079"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a><span data-ttu-id="f5a08-102">風險降低：ZipArchiveEntry.FullName 路徑分隔符號</span><span class="sxs-lookup"><span data-stu-id="f5a08-102">Mitigation: ZipArchiveEntry.FullName Path Separator</span></span>
<span data-ttu-id="f5a08-103">從以 .NET Framework 4.6.1 為目標的應用程式開始，<xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> 屬性中使用的路徑分隔符號，已從舊版 .NET Framework 中使用的反斜線 ("\\") 變更為正斜線 ("/")。</span><span class="sxs-lookup"><span data-stu-id="f5a08-103">Starting with apps that target the .NET Framework 4.6.1, the path separator used in the <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> property has changed from the backslash ("\\") used in previous versions of the .NET Framework to a forward slash ("/").</span></span>   <span data-ttu-id="f5a08-104">呼叫 <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> 方法的其中一個多載會建立 <xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> 物件。</span><span class="sxs-lookup"><span data-stu-id="f5a08-104"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> objects are created by calling one of the overloads of the <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="f5a08-105">影響</span><span class="sxs-lookup"><span data-stu-id="f5a08-105">Impact</span></span>  
 <span data-ttu-id="f5a08-106">這項變更使得 .NET 實作遵守 [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) (.ZIP 檔案格式規格) 的 4.4.17.1 小節，並允許在非 Windows 系統上解壓縮 ZIP 封存。</span><span class="sxs-lookup"><span data-stu-id="f5a08-106">The change brings the .NET implementation into conformity with section 4.4.17.1 of the [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) and allows .ZIP archives to be decompressed on non-Windows systems.</span></span>  
  
 <span data-ttu-id="f5a08-107">在非 Windows 作業系統 (例如 Macintosh) 上解壓縮以舊版 .NET Framework 為目標的應用程式所建立的 ZIP 檔案，會無法保留目錄結構。</span><span class="sxs-lookup"><span data-stu-id="f5a08-107">Decompressing a zip file created  by an app that targets a previous version of the .NET Framework on non-Windows operating systems such as the Macintosh fails to preserve the directory structure.</span></span> <span data-ttu-id="f5a08-108">例如，在 Macintosh 上，它會建立一組檔案，其檔案名稱會串連目錄路徑，以及任何反斜線 (\\) 字元和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="f5a08-108">For example, on the Macintosh, it creates a set of files whose filename concatenates the directory path, along with any backslash ("\\") characters, and the filename.</span></span> <span data-ttu-id="f5a08-109">因此，解壓縮檔案的目錄結構會無法保留。</span><span class="sxs-lookup"><span data-stu-id="f5a08-109">As a result, the directory structure of decompressed files is not preserved.</span></span>  
  
 <span data-ttu-id="f5a08-110">對於 Windows 作業系統上由 .NET Framework <xref:System.IO> 命名空間中的 API 解壓縮的 .ZIP 檔案而言，此變更的影響應該很小，因為這些 API 可以將斜線 ("/") 或反斜線 ("\\") 當做路徑分隔符號字元順利地處理。</span><span class="sxs-lookup"><span data-stu-id="f5a08-110">The impact of this change on .ZIP files that are decompressed on the Windows operating system by APIs in the .NET Framework <xref:System.IO> namespace should be minimal, since these APIs can seamlessly handle either a slash ("/") or a backslash ("\\") as the path separator character.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="f5a08-111">緩和</span><span class="sxs-lookup"><span data-stu-id="f5a08-111">Mitigation</span></span>  
 <span data-ttu-id="f5a08-112">如果不需要此行為，您可以在應用程式組態檔的 [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段加入一個組態設定以選擇退出。</span><span class="sxs-lookup"><span data-stu-id="f5a08-112">If this behavior is undesirable, you can opt out of by adding a configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file.</span></span> <span data-ttu-id="f5a08-113">下圖顯示 `<runtime>` 區段及選擇退出參數。</span><span class="sxs-lookup"><span data-stu-id="f5a08-113">The following shows both the `<runtime>` section and the opt-out switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 <span data-ttu-id="f5a08-114">此外，以舊版 .NET Framework 為目標但在 .NET Framework 4.6.1 和更新版本下執行的應用程式，可以藉由將組態設定新增到應用程式設定檔的 [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段，以選擇加入這項行為。</span><span class="sxs-lookup"><span data-stu-id="f5a08-114">In addition, apps that target previous versions of the .NET Framework but are running on the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding a configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file.</span></span> <span data-ttu-id="f5a08-115">下圖顯示 `<runtime>` 區段及選擇加入參數。</span><span class="sxs-lookup"><span data-stu-id="f5a08-115">The following shows both the `<runtime>` section and the opt-in switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f5a08-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5a08-116">See also</span></span>

- [<span data-ttu-id="f5a08-117">重定目標變更</span><span class="sxs-lookup"><span data-stu-id="f5a08-117">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
- [<span data-ttu-id="f5a08-118">4.6.1 中的應用程式相容性</span><span class="sxs-lookup"><span data-stu-id="f5a08-118">Application Compatibility in 4.6.1</span></span>](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)

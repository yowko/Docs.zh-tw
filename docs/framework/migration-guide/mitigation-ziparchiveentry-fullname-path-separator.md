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
ms.openlocfilehash: 3f6c7f258fd5dbf01db4d79b73b88ddd7484f9b2
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102615"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a><span data-ttu-id="3b111-102">風險降低：ZipArchiveEntry.FullName 路徑分隔符號</span><span class="sxs-lookup"><span data-stu-id="3b111-102">Mitigation: ZipArchiveEntry.FullName Path Separator</span></span>

<span data-ttu-id="3b111-103">從以 .NET 框架 4.6.1 為目標<xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType>的應用開始, 屬性中使用的路徑分隔符從早期版本的 .NET\\Framework 中使用的反 斜杠("/")更改為向前斜杠 ("/")。</span><span class="sxs-lookup"><span data-stu-id="3b111-103">Starting with apps that target the .NET Framework 4.6.1, the path separator used in the <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> property has changed from the backslash ("\\") used in previous versions of .NET Framework to a forward slash ("/").</span></span> <span data-ttu-id="3b111-104">呼叫 <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> 方法的其中一個多載會建立 <xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> 物件。</span><span class="sxs-lookup"><span data-stu-id="3b111-104"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> objects are created by calling one of the overloads of the <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="3b111-105">影響</span><span class="sxs-lookup"><span data-stu-id="3b111-105">Impact</span></span>  
 <span data-ttu-id="3b111-106">這項變更使得 .NET 實作遵守 [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) (.ZIP 檔案格式規格) 的 4.4.17.1 小節，並允許在非 Windows 系統上解壓縮 ZIP 封存。</span><span class="sxs-lookup"><span data-stu-id="3b111-106">The change brings the .NET implementation into conformity with section 4.4.17.1 of the [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) and allows .ZIP archives to be decompressed on non-Windows systems.</span></span>  
  
 <span data-ttu-id="3b111-107">解壓縮由應用創建的 zip 檔案,該檔針對非 Windows 作業系統(如 MacOS)上的早期版本的 .NET Framework,無法保留目錄結構。</span><span class="sxs-lookup"><span data-stu-id="3b111-107">Decompressing a zip file created by an app that targets a previous version of .NET Framework on non-Windows operating systems such as MacOS fails to preserve the directory structure.</span></span> <span data-ttu-id="3b111-108">例如,在 MacOS 上,它創建一組檔,其檔名串聯目錄路徑、任何反斜杠\\(") 字元「和檔名。</span><span class="sxs-lookup"><span data-stu-id="3b111-108">For example, on MacOS, it creates a set of files whose file name concatenates the directory path, any backslash ("\\") characters, and the filename.</span></span> <span data-ttu-id="3b111-109">因此，解壓縮檔案的目錄結構會無法保留。</span><span class="sxs-lookup"><span data-stu-id="3b111-109">As a result, the directory structure of decompressed files is not preserved.</span></span>  
  
 <span data-ttu-id="3b111-110">此更改對的影響。在 .NET<xref:System.IO>框架 命名空間中由 API 在 Windows 作業系統上解壓縮的 ZIP 檔應最小,因為這些 API 可以無縫地\\處理斜杠("/")或反斜 杠("")作為路徑分隔符。</span><span class="sxs-lookup"><span data-stu-id="3b111-110">The impact of this change on .ZIP files that are decompressed on the Windows operating system by APIs in .NET Framework <xref:System.IO> namespace should be minimal, since these APIs can seamlessly handle either a slash ("/") or a backslash ("\\") as the path separator character.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="3b111-111">降低</span><span class="sxs-lookup"><span data-stu-id="3b111-111">Mitigation</span></span>  
 <span data-ttu-id="3b111-112">如果此行為不可取,則可以通過將配置設置添加到應用程式配置檔的[\<運行時>](../configure-apps/file-schema/runtime/runtime-element.md)部分來選擇宣告。</span><span class="sxs-lookup"><span data-stu-id="3b111-112">If this behavior is undesirable, you can opt out of by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file.</span></span> <span data-ttu-id="3b111-113">下圖顯示 `<runtime>` 區段及選擇退出參數。</span><span class="sxs-lookup"><span data-stu-id="3b111-113">The following shows both the `<runtime>` section and the opt-out switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 <span data-ttu-id="3b111-114">此外,面向 .NET Framework 的早期版本並在 .NET Framework 4.6.1 和更高版本上運行的應用可以通過將配置設置添加到應用程式配置檔的[\<運行時>](../configure-apps/file-schema/runtime/runtime-element.md)部分來選擇加入此行為。</span><span class="sxs-lookup"><span data-stu-id="3b111-114">In addition, apps that target previous versions of .NET Framework but are running on .NET Framework 4.6.1 and later versions can opt in to this behavior by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file.</span></span> <span data-ttu-id="3b111-115">下圖顯示 `<runtime>` 區段及選擇加入參數。</span><span class="sxs-lookup"><span data-stu-id="3b111-115">The following shows both the `<runtime>` section and the opt-in switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3b111-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b111-116">See also</span></span>

- [<span data-ttu-id="3b111-117">應用程式相容性</span><span class="sxs-lookup"><span data-stu-id="3b111-117">Application compatibility</span></span>](application-compatibility.md)

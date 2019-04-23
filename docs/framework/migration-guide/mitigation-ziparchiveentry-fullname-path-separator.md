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
ms.openlocfilehash: eba871215f33e4d3b50054e9ceaa92be090d0143
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125103"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a>風險降低：ZipArchiveEntry.FullName 路徑分隔符號
從以 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 為目標的應用程式開始，<xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> 屬性中使用的路徑分隔符號已從舊版 .NET Framework 中使用的反斜線 ("\\") 變更為正斜線 ("/")。   <xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> 物件會透過呼叫 <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> 方法的其中一個多載來建立。  
  
## <a name="impact"></a>影響  
 這項變更使得 .NET 實作遵守 [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) (.ZIP 檔案格式規格) 的 4.4.17.1 小節，並允許在非 Windows 系統上解壓縮 ZIP 封存。  
  
 在非 Windows 作業系統 (例如 Macintosh) 上解壓縮以舊版 .NET Framework 為目標的應用程式所建立的 ZIP 檔案，會無法保留目錄結構。 例如，在 Macintosh 上，它會建立一組檔案，其檔案名稱會串連目錄路徑，以及任何反斜線 (\\) 字元和檔案名稱。 因此，解壓縮檔案的目錄結構會無法保留。  
  
 對於 Windows 作業系統上由 .NET Framework <xref:System.IO> 命名空間中的 API 解壓縮的 .ZIP 檔案而言，此變更的影響應該很小，因為這些 API 可以將斜線 ("/") 或反斜線 ("\\") 當做路徑分隔符號字元順利地處理。  
  
## <a name="mitigation"></a>緩和  
 如果不需要此行為，您可以在應用程式組態檔的 [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段加入一個組態設定以選擇退出。 下圖顯示 `<runtime>` 區段及選擇退出參數。  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 此外，以舊版 .NET Framework 為目標但在 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 和更新版本下執行的應用程式，可以藉由在應用程式組態檔的 [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段加入一個組態設定，以選擇加入這項行為。 下圖顯示 `<runtime>` 區段及選擇加入參數。  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a>另請參閱

- [重定目標變更](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
- [4.6.1 中的應用程式相容性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)

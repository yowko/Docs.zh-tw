---
title: 風險降低：ZipArchiveEntry.FullName 路徑分隔符號
description: 瞭解 ZipArchiveEntry 的路徑分隔符號如何從以 .NET Framework 4.6.1 為目標的應用程式開始變更。
ms.date: 03/30/2017
helpviewer_keywords:
- application compatibility
- ',NET Framework application compatibility'
- .NET Framework 4.6.1
- .NET Framework 4.6.1 retargeting changes
- retargeting changes
ms.assetid: 8d575722-4fb6-49a2-8a06-f72d62dc3766
ms.openlocfilehash: 6e2c0908098f8487f7d429274fe7ad797bedfda1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96283441"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a>風險降低：ZipArchiveEntry.FullName 路徑分隔符號

從以 .NET Framework 4.6.1 為目標的應用程式開始，屬性中使用的路徑分隔符號 <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> 已從反斜線 ( " \\ " ) （在舊版 .NET Framework 中使用）變更為正斜線 ( "/" ) 。 呼叫 <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> 方法的其中一個多載會建立 <xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> 物件。  
  
## <a name="impact"></a>影響  

 這項變更使得 .NET 實作遵守 [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) (.ZIP 檔案格式規格) 的 4.4.17.1 小節，並允許在非 Windows 系統上解壓縮 ZIP 封存。  
  
 在非 Windows 作業系統（例如 MacOS）上解壓縮以舊版 .NET Framework 為目標的應用程式所建立的 zip 檔案，會無法保留目錄結構。 例如，在 MacOS 上，它會建立一組檔案，其檔案名會串連目錄路徑、任何反斜線 ( " \\ " ) 字元和檔案名。 因此，解壓縮檔案的目錄結構會無法保留。  
  
 這項變更的影響。.NET Framework 命名空間中的 Api 在 Windows 作業系統上解壓縮的 ZIP 檔案 <xref:System.IO> 應該是最基本的，因為這些 api 可以順暢地處理斜線 ( "/" ) 或反斜線 ( " \\ " ) 作為路徑分隔符號。  
  
## <a name="mitigation"></a>降低  

 如果不想要這種行為，您可以將設定設定新增至 [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) 應用程式佈建檔的區段，退出。 下圖顯示 `<runtime>` 區段及選擇退出參數。  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 此外，以舊版 .NET Framework 但在 .NET Framework 4.6.1 和更新版本上執行的應用程式，可以藉由將設定設定新增至 [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) 應用程式佈建檔的區段，來加入宣告這項行為。 下圖顯示 `<runtime>` 區段及選擇加入參數。  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a>另請參閱

- [應用程式相容性](application-compatibility.md)

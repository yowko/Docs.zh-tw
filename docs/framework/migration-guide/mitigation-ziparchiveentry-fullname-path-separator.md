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
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a>風險降低：ZipArchiveEntry.FullName 路徑分隔符號

從以 .NET 框架 4.6.1 為目標<xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType>的應用開始, 屬性中使用的路徑分隔符從早期版本的 .NET\\Framework 中使用的反 斜杠("/")更改為向前斜杠 ("/")。 呼叫 <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> 方法的其中一個多載會建立 <xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> 物件。  
  
## <a name="impact"></a>影響  
 這項變更使得 .NET 實作遵守 [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) (.ZIP 檔案格式規格) 的 4.4.17.1 小節，並允許在非 Windows 系統上解壓縮 ZIP 封存。  
  
 解壓縮由應用創建的 zip 檔案,該檔針對非 Windows 作業系統(如 MacOS)上的早期版本的 .NET Framework,無法保留目錄結構。 例如,在 MacOS 上,它創建一組檔,其檔名串聯目錄路徑、任何反斜杠\\(") 字元「和檔名。 因此，解壓縮檔案的目錄結構會無法保留。  
  
 此更改對的影響。在 .NET<xref:System.IO>框架 命名空間中由 API 在 Windows 作業系統上解壓縮的 ZIP 檔應最小,因為這些 API 可以無縫地\\處理斜杠("/")或反斜 杠("")作為路徑分隔符。  
  
## <a name="mitigation"></a>降低  
 如果此行為不可取,則可以通過將配置設置添加到應用程式配置檔的[\<運行時>](../configure-apps/file-schema/runtime/runtime-element.md)部分來選擇宣告。 下圖顯示 `<runtime>` 區段及選擇退出參數。  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 此外,面向 .NET Framework 的早期版本並在 .NET Framework 4.6.1 和更高版本上運行的應用可以通過將配置設置添加到應用程式配置檔的[\<運行時>](../configure-apps/file-schema/runtime/runtime-element.md)部分來選擇加入此行為。 下圖顯示 `<runtime>` 區段及選擇加入參數。  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a>另請參閱

- [應用程式相容性](application-compatibility.md)

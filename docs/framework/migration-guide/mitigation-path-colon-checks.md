---
title: 風險降低︰路徑冒號檢查
description: 瞭解 .NET Framework 4.6.2 中所做的變更，以支援 (冒號) 檢查適當的磁片磁碟機分隔符號語法。
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
ms.openlocfilehash: 03f1c7249549aae7e3bef986c97fb5f320fbeb2f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96283454"
---
# <a name="mitigation-path-colon-checks"></a>風險降低︰路徑冒號檢查

從以 .NET Framework 4.6.2 為目標的應用程式開始，為了支援先前不支援的路徑 (就長度和格式兩方面) 而有數項變更。 特別是提供更正確的適當磁碟機分隔符號語法 (冒號) 檢查。  
  
## <a name="impact"></a>影響  

 這些變更會封鎖 <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> 和 <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> 方法先前支援的一些 URI 路徑。  
  
## <a name="mitigation"></a>降低  

 若要解決 <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> 和 <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> 方法不再支援的先前可接受路徑問題，您可以執行下列動作：  
  
- 從 URL 手動移除配置。 例如，從 URL 移除 `file://`。  
  
- 將 URI 傳遞給 <xref:System.Uri> 建構函式，並擷取 <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> 屬性的值。  
  
- 藉由將 `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> 參數設定為 `true`，以選擇退出新的路徑正規化。  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
    </runtime>  
    ```  
  
## <a name="see-also"></a>另請參閱

- [應用程式相容性](application-compatibility.md)

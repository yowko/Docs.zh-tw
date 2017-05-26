---
title: "風險降低︰路徑冒號檢查 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: b5e2426fc81c8fd38994a4124cf71af8ec445bfb
ms.contentlocale: zh-tw
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-path-colon-checks"></a>風險降低︰路徑冒號檢查
從以 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 為目標的應用程式開始，為了支援先前所不支援的路徑 (就長度和格式兩方面) 而有數項變更。 特別是提供更正確的適當磁碟機分隔符號語法 (冒號) 檢查。  
  
## <a name="impact"></a>影響  
 這些變更會封鎖 <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=fullName> 和 <xref:System.IO.Path.GetPathRoot%2A?displayProperty=fullName> 方法先前所支援的某些 URI 路徑。  
  
## <a name="mitigation"></a>緩和  
 為解決先前接受的路徑不再受 <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=fullName> 和 <xref:System.IO.Path.GetPathRoot%2A?displayProperty=fullName> 方法支援的問題，您可以採取以下措施：  
  
-   從 URL 手動移除配置。 例如，從 URL 移除 `file://`。  
  
-   將 URI 傳遞至 <xref:System.Uri> 建構函式，並擷取 <xref:System.Uri.LocalPath%2A?displayProperty=fullName> 屬性的值。  
  
-   藉由將 `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> 參數設為 `true`，以選擇退出新的路徑正規化。  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
    </runtime>  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [重定目標變更](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)


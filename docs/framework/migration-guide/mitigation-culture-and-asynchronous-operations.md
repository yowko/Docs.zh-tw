---
title: "風險降低：文化特性和非同步作業 | Microsoft Docs"
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
ms.assetid: d2cdb578-9923-47df-9ffd-5865333ac1a4
caps.latest.revision: 4
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: c2dbf60cacf47be3c448b5683b771840ef85ddaf
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-culture-and-asynchronous-operations"></a>風險降低：文化特性和非同步作業
若是以 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 和更新版本為目標的應用程式，<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> 和 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 會儲存在執行緒的 <xref:System.Threading.ExecutionContext> 中，以提供給不同的非同步作業。  
  
## <a name="impact"></a>影響  
 由於這項變更，<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> 或 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 的變更會反映在後續以非同步方式執行的工作中。 這有別於舊版的 .NET Framework 將所有非同步工作中的 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> 與 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 重設為系統預設值的行為。  
  
## <a name="mitigation"></a>緩和  
 受此變更影響的應用程式可透過下列任一種方式應變：  
  
-   在非同步工作的第一個作業時明確設定 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> 或 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 屬性。  
  
-   在應用程式的組態檔中加入下列 `AppContextSwitchOverrides` 元素，以選擇加入不要流動 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> 和 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 的舊有行為：  
  
    ```xml  
  
    <configuration>  
        <runtime>  
            <AppContextSwitchOverrides value="Switch.System.Globalization.NoAsyncCurrentCulture=true" />  
        </runtime>  
    </configuration>  
  
    ```  
  
-   以程式設計方式設定下列相容性參數，以選擇加入不要流動 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> 和 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 的舊有行為：  
  
    ```csharp  
    AppContext.SetSwitch("Switch.System.Globalization.NoAsyncCurrentCulture", true);  
    ```  
  
    ```vb  
    AppContext.SetSwitch("Switch.System.Globalization.NoAsyncCurrentCulture", true)  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [重定目標變更](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)

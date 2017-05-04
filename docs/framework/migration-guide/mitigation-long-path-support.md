---
title: "風險降低︰長路徑支援 | Microsoft Docs"
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
ms.assetid: 3cbe2d77-6e2c-4665-a6c5-7000b9ad6890
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 40b4b94ac3058dda88b44c82110d4c749566e2b2
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-long-path-support"></a>風險降低︰長路徑支援
從以 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 為目標的應用程式開始，如果路徑或完整檔案名稱超過 260 (或 `MAX_PATH`) 個字元，檔案系統 I/O 方法不會再自動擲回 <xref:System.IO.PathTooLongException>。 現在可支援長達 32K 個字元的長路徑。  
  
## <a name="impact"></a>影響  
 重新編譯為以 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 為目標的應用程式和先前因為路徑超過 260 個字元而自動擲回 <xref:System.IO.PathTooLongException> 的應用程式，現在只有在下列情況下才會擲回 <xref:System.IO.PathTooLongException>：  
  
-   路徑的長度超過 <xref:System.Int16.MaxValue?displayProperty=fullName> (32,767) 個字元。  
  
-   作業系統傳回 `COR_E_PATHTOOLONG` 或其對應項。  
  
 以 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]和更舊版本為目標之應用程式的舊行為，是每當路徑超過 260 個字元時，執行階段就會自動擲回 <xref:System.IO.PathTooLongException>。  
  
## <a name="mitigation"></a>緩和  
 對於以 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 為目標的應用程式，如果不需要長路徑支援，您可以透過將下列內容加入至 app.config 檔案的 [\<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段以選擇退出︰  
  
```xml  
  
<runtime>   
   <AppContextSwitchOverrides value="Switch.System.IO.BlockLongPaths=true" />   
</runtime>  
  
```  
  
 對於以舊版 .NET Framework 為目標但卻在 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 或更新版本上執行的應用程式，則可將下列內容加入至 app.config 檔案的 [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段，以選擇加入長路徑支援：  
  
```xml  
  
<runtime>   
   <AppContextSwitchOverrides value="Switch.System.IO.BlockLongPaths=false" />   
</runtime>  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [重定目標變更](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)

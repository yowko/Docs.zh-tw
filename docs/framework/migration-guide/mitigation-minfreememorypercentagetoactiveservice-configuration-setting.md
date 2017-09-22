---
title: "風險降低：minFreeMemoryPercentageToActiveService 組態設定"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7875f26-0da8-4afe-9846-7a21778f757b
caps.latest.revision: 4
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f7f228890476d45517a21bc09806538139c5e389
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-minfreememorypercentagetoactiveservice-configuration-setting"></a>風險降低：minFreeMemoryPercentageToActiveService 組態設定
在 [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] 中，如果 Web 伺服器上的可用記憶體少於 [minFreeMemoryPercentageToActivateService](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) 組態設定所指定的百分比，則會擲回例外狀況。 在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中，已忽略這項設定。  
  
## <a name="impact"></a>影響  
 在大部分情況下，觀察 [minFreeMemoryPercentageToActivateService](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) 設定的影響是可取的：由於避免了在記憶體有限的系統上啟動 Windows Communication Foundation (WCF) 服務時可能發生的 <xref:System.OutOfMemoryException> 例外狀況，因此改善系統穩定性。  
  
 但在某些情況下，之前順利啟動的服務可能無法啟動。 在這種情況下，會顯示詳細的錯誤訊息：  
  
```Output  
Memory gates checking failed because the free memory (nnnn bytes) is less than nn% of total memory. As a result, the service will not be available for incoming requests. To resolve this, either reduce the load on the machine or adjust the value of minFreeMemoryPercentageToActivateService on the serviceHostingEnvironment config element.  
```  
  
## <a name="mitigation"></a>緩和  
 若要還原成忽略 [minFreeMemoryPercentageToActivateService](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) 設定的前一個行為，請依照下列方式修改 web.config 檔案：  
  
```  
<serviceHostingEnvironment multipleSiteBindingsEnabled="true"   
                           minFreeMemoryPercentageToActivateService="0">  
   <serviceActivations>  
   ...  
   </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
## <a name="see-also"></a>另請參閱  
 [執行階段變更](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-5-1.md)


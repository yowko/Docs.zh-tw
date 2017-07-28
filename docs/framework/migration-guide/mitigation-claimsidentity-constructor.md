---
title: "風險降低︰ClaimsIdentity 建構函式 | Microsoft Docs"
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
ms.assetid: 946903f1-0fbf-4f67-805b-1eb48352024d
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 84016664708b9b7fc61a9535e5f7910417caa6f1
ms.contentlocale: zh-tw
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-claimsidentity-constructor"></a>風險降低︰ClaimsIdentity 建構函式
從 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 開始，<xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=fullName> 建構函式設定 <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> 屬性的方式變得不同。 如果 <xref:System.Security.Principal.IIdentity> 引數是 <xref:System.Security.Claims.ClaimsIdentity> 物件，而該 <xref:System.Security.Claims.ClaimsIdentity> 物件的 <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> 屬性不是 `null`，則會使用 <xref:System.Security.Claims.ClaimsIdentity.Clone%2A?displayProperty=fullName> 方法附加 <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> 屬性。 在 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 中，<xref:System.Security.Claims.ClaimsIdentity.Actor%2A> 屬性是附加為現有參考。  
  
## <a name="impact"></a>影響  
 從 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 開始，新的 <xref:System.Security.Claims.ClaimsIdentity> 物件的 <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> 屬性不等於建構函式的 <xref:System.Security.Principal.IIdentity> 引數的 <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> 屬性。 在 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 和先前的版本中則是相等的。  
  
## <a name="mitigation"></a>緩和  
 如果不想要這種行為，您可以將應用程式組態檔中的 `Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity` 參數設為 `true` 來還原舊版行為。 您會需要將下列內容加入 web.config 檔案的 [\<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段︰  
  
```xml  
<configuration>  
   <runtime>  
      <AppContextSwitchOverrides value="Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity=true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱  
 [重定目標變更](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)


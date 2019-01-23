---
title: 組件繫結重新導向安全性使用權限
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
author: mcleblanc
ms.author: markl
ms.openlocfilehash: d4483d11903d61135585a2b6c2c33eff48300151
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616010"
---
# <a name="assembly-binding-redirection-security-permission"></a>組件繫結重新導向安全性使用權限
在應用程式組態檔中進行明確的組件繫結重新導向必須擁有安全性權限。 這適用於 .NET Framework 組件和協力廠商組件的重新導向。 藉由設定授與權限<xref:System.Security.Permissions.SecurityPermissionFlag>加上旗標上<xref:System.Security.Permissions.SecurityPermission>。 Managed 組件預設會有任何權限。  
  
 安全性權限會授與信任的區域 （本機電腦） 和內部網路區域中執行的應用程式。 在 [網際網路] 區域中執行的應用程式的嚴格禁止執行組件繫結重新導向。  
  
 如果由元件發行者所控制的發行者原則檔中或在電腦組態檔是由系統管理員所控制的方式執行組件重新導向，則不需要的權限。 不過，需要的權限來明確忽略發行者原則使用的應用程式[ \<apply ="no"/ >](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)應用程式組態檔中的項目。  
  
 下表顯示的預設安全性設定**BindingRedirects**旗標。  
  
|區域|BindingRedirects 旗標設定|  
|----------|-----------------------------------|  
|受信任的區域 （本機電腦）|**ON**|  
|內部網路區域|**ON**|  
|網際網路區域|**OFF**|  
|不受信任的區域|**OFF**|  
  
 系統管理員可以變更這些安全性設定，以支援或限制特定電腦的特定案例。 沒有變更工具**BindingRedirects**旗標設定預設值; 系統管理員必須手動編輯使用者的電腦上的 Security.config 檔。  
  
## <a name="see-also"></a>另請參閱
- [發行者原則檔和並排顯示執行](https://msdn.microsoft.com/library/97a042be-4d72-40c3-91c0-76fd36bdf133)
- [如何：啟用和停用自動繫結重新導向](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
- [並存執行](../../../docs/framework/deployment/side-by-side-execution.md)

---
title: 組件繫結重新導向安全性使用權限
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ef9295028aeb7bfcc6df88e9c8bb7f80e2a31368
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="assembly-binding-redirection-security-permission"></a>組件繫結重新導向安全性使用權限
在應用程式組態檔中進行明確的組件繫結重新導向必須擁有安全性權限。 這適用於 .NET Framework 組件和協力廠商組件的重新導向。 藉由設定授與權<xref:System.Security.Permissions.SecurityPermissionFlag>加上旗標上<xref:System.Security.Permissions.SecurityPermission>。 根據預設，managed 組件具有任何權限。  
  
 安全性權限會授與信任的區域 （本機電腦） 和內部網路區域中執行的應用程式。 網際網路區域中執行的應用程式絕對禁止執行組件繫結重新導向。  
  
 如果由元件發行者的發行者原則檔中或在電腦組態檔由系統管理員所控制的方式執行組件重新導向，則不需要權限。 不過，需要的權限來明確忽略發行者原則使用的應用程式[ \<p 套用 ="否"/ >](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)應用程式組態檔中的項目。  
  
 下表顯示的預設安全性設定**方式是**旗標。  
  
|區域|設定的方式是旗標|  
|----------|-----------------------------------|  
|受信任的區域 （本機電腦）|**ON**|  
|內部網路區域|**ON**|  
|網際網路區域|**關閉**|  
|不受信任的區域|**關閉**|  
  
 系統管理員可以變更這些安全性設定，以支援或限制特定電腦的特定案例。 沒有變更工具**方式是**旗標預設值，從設定系統管理員必須手動編輯使用者的電腦上的 Security.config 檔。  
  
## <a name="see-also"></a>另請參閱  
 [發行者原則檔和-並存執行](http://msdn.microsoft.com/library/97a042be-4d72-40c3-91c0-76fd36bdf133)  
 [如何：啟用和停用自動繫結重新導向](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)  
 [並存執行](../../../docs/framework/deployment/side-by-side-execution.md)

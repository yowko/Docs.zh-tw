---
title: 組件繫結重新導向安全性使用權限
description: 瞭解 .NET 中的應用程式佈建檔內明確元件系結重新導向所需的安全性許可權。
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
ms.openlocfilehash: ea2b735b2c98b588903c4393f21c6b743910854a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552371"
---
# <a name="assembly-binding-redirection-security-permission"></a>組件繫結重新導向安全性使用權限
在應用程式組態檔中進行明確的組件繫結重新導向必須擁有安全性權限。 這適用於 .NET Framework 組件和協力廠商組件的重新導向。 藉由在上設定旗標來授與許可權 <xref:System.Security.Permissions.SecurityPermissionFlag> <xref:System.Security.Permissions.SecurityPermission> 。 Managed 元件預設沒有任何許可權。  
  
 安全性許可權會授與在信任區域 (本機電腦) 和內部網路區域中執行的應用程式。 在網際網路區域中執行的應用程式，完全禁止執行元件系結重新導向。  
  
 如果在元件發行者所控制的發行者原則檔中，或由系統管理員所控制的電腦設定檔中執行元件重新導向，則不需要此許可權。 但是，應用程式需要許可權，才能使用 [\<publisherPolicy apply="no"/>](./file-schema/runtime/publisherpolicy-element.md) 應用程式佈建檔中的專案明確地忽略發行者原則。  
  
 下表顯示 **BindingRedirects** 旗標的預設安全性設定。  
  
|區域|BindingRedirects 旗標設定|  
|----------|-----------------------------------|  
|受信任的區域 (本機電腦) |**ON**|  
|內部網路區域|**ON**|  
|網際網路區域|**OFF**|  
|不受信任的區域|**OFF**|  
  
 系統管理員可以變更這些安全性設定，以支援或限制指定電腦上的特定案例。 沒有從預設值變更 **BindingRedirects** 旗標設定的工具;系統管理員必須手動編輯使用者電腦上的 Security.config 檔案。  
  
## <a name="see-also"></a>另請參閱

- [發行者原則檔和並存執行](/previous-versions/dotnet/netframework-4.0/06d2bae3(v=vs.100))
- [作法：啟用和停用自動繫結重新導向](how-to-enable-and-disable-automatic-binding-redirection.md)
- [並存執行](../deployment/side-by-side-execution.md)

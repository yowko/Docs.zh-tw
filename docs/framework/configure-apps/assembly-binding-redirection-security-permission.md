---
title: 組件繫結重新導向安全性使用權限
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
ms.openlocfilehash: b59689e78f901637674c0a1df28ed74411e8e7c7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921379"
---
# <a name="assembly-binding-redirection-security-permission"></a>組件繫結重新導向安全性使用權限
在應用程式組態檔中進行明確的組件繫結重新導向必須擁有安全性權限。 這適用於 .NET Framework 組件和協力廠商組件的重新導向。 許可權是藉由<xref:System.Security.Permissions.SecurityPermissionFlag> <xref:System.Security.Permissions.SecurityPermission>在上設定旗標來授與。 受控元件預設沒有任何許可權。  
  
 安全性許可權會授與在 [信任的區域 (本機電腦)] 和 [內部網路] 區域中執行的應用程式。 在網際網路區域中執行的應用程式, 絕對不會被禁止執行元件系結重新導向。  
  
 如果在元件發行者所控制的發行者原則檔中, 或在系統管理員所控制的電腦設定檔中執行元件重新導向, 則不需要許可權。 不過, 應用程式必須具備許可權, 才能使用應用程式佈建檔中的[ \<publisherPolicy apply = "no"/>](./file-schema/runtime/publisherpolicy-element.md)元素明確忽略發行者原則。  
  
 下表顯示**BindingRedirects**旗標的預設安全性設定。  
  
|區域|BindingRedirects 旗標設定|  
|----------|-----------------------------------|  
|信任的區域 (本機電腦)|**的**|  
|內部網路區域|**的**|  
|網際網路區域|**OFF**|  
|不受信任的區域|**OFF**|  
  
 系統管理員可以變更這些安全性設定, 以支援或限制指定電腦上的特定案例。 沒有任何工具可變更**BindingRedirects**旗標設定的預設值;系統管理員必須手動編輯使用者電腦上的安全 .config 檔案。  
  
## <a name="see-also"></a>另請參閱

- [發行者原則檔和並存執行](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/06d2bae3(v=vs.100))
- [如何：啟用和停用自動繫結重新導向](how-to-enable-and-disable-automatic-binding-redirection.md)
- [並存執行](../deployment/side-by-side-execution.md)

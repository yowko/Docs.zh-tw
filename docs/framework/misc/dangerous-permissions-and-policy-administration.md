---
title: "危險使用權限和原則管理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- permissions [.NET Framework], policy administration
- security [.NET Framework], dangerous permissions
- code security, dangerous permissions
- secure coding, dangerous permissions
- permissions [.NET Framework], dangerous
ms.assetid: 1929e854-23a0-4bb1-94be-e8aa3b609e32
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0c8a01cbae2077838a8eef3f2f673e7d9d646717
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="dangerous-permissions-and-policy-administration"></a>危險使用權限和原則管理
.NET Framework 為幾個受保護作業提供了使用權限，這些受保護作業也可能會讓安全性系統受到危害。 您只能在必要時將這些危險的使用權限授與給可靠的程式碼。 如果將這些使用權限授與給惡意程式碼，通常就沒有任何方法可以抵禦這些惡意程式碼。  
  
> [!NOTE]
>  在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]中，.NET Framework 安全性模型和術語已有重大變更。 如需有關這些變更的詳細資訊，請參閱[安全性變更](../../../docs/framework/security/security-changes.md)。  
  
 下表說明危險的使用權限。  
  
|權限|潛在風險|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|允許 Managed 程式碼呼叫進入 Unmanaged 程式碼，後者通常具有危險。|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|不用進行驗證，程式碼就可以執行任何動作。|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|失效的辨識項可以騙過安全性原則。|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|修改安全性原則的能力可以使安全性停用。|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|使用序列化可能會規避存取範圍機制。 如需詳細資訊，請參閱 [安全性和序列化](../../../docs/framework/misc/security-and-serialization.md)。|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|設定目前主體的能力可以欺騙以角色為基礎的安全性。|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|執行緒的操作有危險，因為安全性狀態與執行緒有關聯。|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|可以使用私用成員使存取範圍機制無效。|  
  
## <a name="see-also"></a>另請參閱  
 [安全程式碼撰寫方針](../../../docs/standard/security/secure-coding-guidelines.md)

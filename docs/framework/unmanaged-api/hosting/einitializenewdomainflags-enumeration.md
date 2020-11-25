---
title: EInitializeNewDomainFlags 列舉
ms.date: 03/30/2017
api_name:
- EInitializeNewDomainFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EInitializeNewDomainFlags
helpviewer_keywords:
- EInitializeNewDomainFlags enumeration [.NET Framework hosting]
ms.assetid: 3a120ab2-f5ef-4c9b-8595-d3ed7247c342
ms.openlocfilehash: 8350b507609e63c060cda08514200d386c37a6b3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724321"
---
# <a name="einitializenewdomainflags-enumeration"></a>EInitializeNewDomainFlags 列舉

讓主機提供執行時間的相關資訊，以初始化應用程式域的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|沒有旗標。|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|通知 common language runtime (CLR) 主機將不會變更方法中應用程式域的安全性狀態 <xref:System.AppDomainManager.InitializeNewDomain%2A> 。|  
  
## <a name="remarks"></a>備註  

 [ICLRDomainManager：： SetAppDomainManagerType](iclrdomainmanager-setappdomainmanagertype-method.md)方法接受型別為的參數 `EInitializeNewDomainFlags` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** MSCorEE.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載列舉](hosting-enumerations.md)
- [SetAppDomainManagerType 方法](iclrdomainmanager-setappdomainmanagertype-method.md)

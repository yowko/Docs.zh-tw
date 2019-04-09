---
title: IAssemblyCache::CreateAssemblyCacheItem 方法
ms.date: 03/30/2017
api_name:
- IAssemblyCache.CreateAssemblyCacheItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::CreateAssemblyCacheItem
helpviewer_keywords:
- IAssemblyCache::CreateAssemblyCacheItem method [.NET Framework fusion]
- CreateAssemblyCacheItem method [.NET Framework fusion]
ms.assetid: 017a7ba5-aaaf-44e2-9cbe-ceebef259df0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 648b641cbd2ec97305674451df06ce5be6a93a49
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183686"
---
# <a name="iassemblycachecreateassemblycacheitem-method"></a>IAssemblyCache::CreateAssemblyCacheItem 方法
取得新的參考[IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)物件。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CreateAssemblyCacheItem (  
    [in]  DWORD dwFlags,  
    [in]  PVOID pvReserved,  
    [out] IAssemblyCacheItem **ppAsmItem,  
    [in, optional] LPCWSTR pszAssemblyName  
);  
```  
  
## <a name="parameters"></a>參數  
 `dwFlags`  
 [in]支援下列值： 旗標。 支援下列值：  
  
-   IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)  
  
-   IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)  
  
 `pvReserved`  
 [in]保留供未來擴充。 `pvReserved` 必須是 null 參考。  
  
 `ppAsmItem`  
 [out]傳回`IAssemblyCacheItem`指標。  
  
 `pszAssemblyName`  
 [in，選用]Uncanonicalized 的逗點分隔`name=value`組。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Fusion.h  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IAssemblyCache 介面](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
- [IAssemblyCacheItem 介面](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)

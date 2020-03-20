---
title: IHostMAlloc::DebugAlloc 方法
ms.date: 03/30/2017
api_name:
- IHostMAlloc.DebugAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::DebugAlloc
helpviewer_keywords:
- DebugAlloc method [.NET Framework hosting]
- IHostMAlloc::DebugAlloc method [.NET Framework hosting]
ms.assetid: 0bfbc527-bea2-43ce-b041-69186f4440dd
topic_type:
- apiref
ms.openlocfilehash: 20ad5485b8603cc7de1c27c00d53c8939871d525
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178029"
---
# <a name="ihostmallocdebugalloc-method"></a>IHostMAlloc::DebugAlloc 方法
請求主機從堆中分配指定數量的記憶體，並另外跟蹤記憶體的分配位置。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DebugAlloc (  
    [in]  SIZE_T  cbSize,
    [in]  EMemoryCriticalLevel dwCriticalLevel,
    [in]  char*   pszFileName,
    [in]  int     iLineNo,
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a>參數  
 `cbSize`  
 [在]當前記憶體分配請求的大小（以位元組為單位）。  
  
 `dwCriticalLevel`  
 [在][EMemory臨界級別值](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md)之一，指示分配失敗的影響。  
  
 `pszFileName`  
 [在]正在調試的可執行檔的代碼檔。  
  
 `iLineNo`  
 [在]請求分配`pszFileName`中的行號。  
  
 `ppMem`  
 [出]指向已分配的記憶體的指標，如果無法完成請求，則為 null。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`DebugAlloc`已成功返回。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入到進程中，或者 CLR 處於無法成功運行託管代碼或成功處理調用的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|調用方不擁有鎖。|  
|HOST_E_ABANDONED|當阻塞的執行緒或光纖等待事件時，事件已被取消。|  
|E_FAIL|發生了未知的災難性故障。 當方法返回E_FAIL時，CLR 在進程中不再可用。 對託管方法的後續調用返回HOST_E_CLRNOTAVAILABLE。|  
|E_OUTOFMEMORY|沒有足夠的記憶體來完成分配請求。|  
  
## <a name="remarks"></a>備註  
 CLR 通過調用[IHostMemoryManagerManager：：createMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)方法獲取指向[IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)實例的介面指標。 `DebugAlloc`允許運行時獲取代碼檔資訊，供調試期間使用。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** MSCorEE.h  
  
 **庫：** 作為資源包含在 MSCorEE.dll 中  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IHostMemoryManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [IHostMalloc 介面](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)

---
title: ICLRReferenceAssemblyEnum::Get 方法
ms.date: 03/30/2017
api_name:
- ICLRReferenceAssemblyEnum.Get
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRReferenceAssemblyEnum::Get
helpviewer_keywords:
- ICLRReferenceAssemblyEnum::Get method [.NET Framework hosting]
- Get method, ICLRReferenceAssemblyEnum interface [.NET Framework hosting]
ms.assetid: f21c1612-9c5d-4abc-a337-577086d29c17
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d8cfb2f18bcceed3a125ac7876122c02d2267698
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436451"
---
# <a name="iclrreferenceassemblyenumget-method"></a>ICLRReferenceAssemblyEnum::Get 方法
在提供的索引取得組件識別。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwIndex`  
 [in]要傳回之組件識別的以零為起始的索引。  
  
 `pwzBuffer`  
 [out]包含組件識別資料緩衝區。  
  
 `pcchBufferSize`  
 [in、 out]大小`pwzBuffer`緩衝區。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`Get` 已成功傳回。|  
|ERROR_INSUFFICIENT_BUFFER|`pwzBuffer` 為太小。|  
|ERROR_NO_MORE_ITEMS|列舉包含的任何項目。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已逾時。|  
|HOST_E_NOT_OWNER|呼叫端未擁有鎖定。|  
|HOST_E_ABANDONED|事件已取消時封鎖的執行緒或 fiber 等候它。|  
|E_FAIL|發生未知的嚴重失敗。 若方法會傳回 E_FAIL，CLR 就不會再處理序內。 裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 `Get` 通常會呼叫兩次。 第一次呼叫所提供的 null 值`pwzBuffer`，並設定`pcchBufferSize`大小適用於`pwzBuffer`。 第二個呼叫可提供適當大小`pwzBuffer`，而且包含在完成時的標準的組件識別資料。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICLRAssemblyReferenceList 介面](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [ICLRReferenceAssemblyEnum 介面](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)

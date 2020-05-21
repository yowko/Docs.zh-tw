---
title: ICorRuntimeHost::CloseEnum 方法
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CloseEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CloseEnum
helpviewer_keywords:
- CloseEnum method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::CloseEnum method [.NET Framework hosting]
ms.assetid: f7ce7e8c-0a3e-4587-a180-063e2b85940e
topic_type:
- apiref
ms.openlocfilehash: a5a86df3ac1f50ca624490ad80a6fed903433436
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762366"
---
# <a name="icorruntimehostcloseenum-method"></a>ICorRuntimeHost::CloseEnum 方法
將網域列舉值重設回定義域清單的開頭。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CloseEnum (  
    [in] HCORENUM hEnum  
);  
```  
  
## <a name="parameters"></a>參數  
 `hEnum`  
 在要重設的列舉值。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|作業成功。|  
|S_FALSE|作業無法完成。|  
|E_FAIL|發生未知的嚴重失敗。 如果方法傳回 E_FAIL，則 common language runtime （CLR）就無法在進程中使用。 後續對任何裝載 Api 的呼叫都會傳回 HOST_E_CLRNOTAVAILABLE。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：** 1.0、1。1  
  
## <a name="see-also"></a>另請參閱

- [CorBindToRuntimeEx 函式](corbindtoruntimeex-function.md)
- [ICorRuntimeHost 介面](icorruntimehost-interface.md)

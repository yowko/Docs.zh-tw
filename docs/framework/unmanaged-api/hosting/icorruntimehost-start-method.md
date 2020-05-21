---
title: ICorRuntimeHost::Start 方法
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::Start
helpviewer_keywords:
- Start method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Start method [.NET Framework hosting]
ms.assetid: c66f3ac5-6489-484a-9bed-c31b711cee01
topic_type:
- apiref
ms.openlocfilehash: ccad76e1c8a49222d4f527f8b7b18d4e40ff8cae
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83760403"
---
# <a name="icorruntimehoststart-method"></a>ICorRuntimeHost::Start 方法
啟動 common language runtime （CLR）。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Start ();  
```  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|作業成功。|  
|S_FALSE|作業無法完成。|  
|E_FAIL|發生未知的嚴重失敗。 如果方法傳回 E_FAIL，就無法在進程中使用 CLR。 後續對任何裝載 Api 的呼叫都會傳回 HOST_E_CLRNOTAVAILABLE。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
  
## <a name="remarks"></a>備註  
 通常不需要呼叫 `Start` 方法，因為 CLR 會在第一次要求執行 managed 程式碼時自動啟動。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：** 1.0、1。1  
  
## <a name="see-also"></a>另請參閱

- [ICorRuntimeHost 介面](icorruntimehost-interface.md)

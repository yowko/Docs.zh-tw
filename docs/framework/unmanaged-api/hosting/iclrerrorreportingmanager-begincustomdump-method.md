---
title: ICLRErrorReportingManager::BeginCustomDump 方法
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager.BeginCustomDump
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager::BeginCustomDump
helpviewer_keywords:
- ICLRErrorReportingManager::BeginCustomDump method [.NET Framework hosting]
- BeginCustomDump method
ms.assetid: 93424a87-ba13-4fa1-b4dc-69d44437b7ae
topic_type:
- apiref
ms.openlocfilehash: 4c83ffaf920abe005ba987e0a744e13aa0d3c016
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615666"
---
# <a name="iclrerrorreportingmanagerbegincustomdump-method"></a>ICLRErrorReportingManager::BeginCustomDump 方法
指定錯誤報表的自訂堆積傾印設定。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT BeginCustomDump (  
    [in] ECustomDumpFlavor dwFlavor,  
    [in] DWORD dwNumItems,  
    [in, size_is(dwNumItems), length_is(dwNumItems)] CustomDumpItem items[],  
    DWORD dwReserved  
);  
```  
  
## <a name="parameters"></a>參數  
 `dwFlavor`  
 在[ECustomDumpFlavor](ecustomdumpflavor-enumeration.md)值，指出要在其上建立自訂堆積傾印的堆積傾印類型。  
  
 `dwNumItems`  
 在陣列的長度 `items` 。 如果 `dwFlavor` 不是 DUMP_FLAVOR_Mini， `dwNumItems` 應該是零。  
  
 `items`  
 在[CustomDumpItem](customdumpitem-structure.md)實例的陣列，指定要加入至迷你傾印的專案。 如果 `dwFlavor` 不是 DUMP_FLAVOR_Mini， `items` 應該是 null。  
  
 `dwReserved`  
 在保留供日後使用。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|說明|  
|-------------|-----------------|  
|S_OK|此方法已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|已封鎖的執行緒或光纖在等候時取消了事件。|  
|E_FAIL|發生不明的嚴重失敗。 在方法傳回 E_FAIL 之後，CLR 就無法在進程內使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 `BeginCustomDump`方法會設定自訂堆積傾印設定。 [EndCustomDump](iclrerrorreportingmanager-endcustomdump-method.md)方法會清除自訂堆積傾印設定，並釋放任何相關聯的狀態。 這應該在自訂堆積傾印完成後呼叫。  
  
> [!IMPORTANT]
> 呼叫失敗 `EndCustomDump` 會造成記憶體流失。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [CustomDumpItem 結構](customdumpitem-structure.md)
- [ECustomDumpFlavor 列舉](ecustomdumpflavor-enumeration.md)
- [ICLRErrorReportingManager 介面](iclrerrorreportingmanager-interface.md)

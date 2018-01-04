---
title: "METAHOST_POLICY_FLAGS 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: METAHOST_POLICY_FLAGS
api_location: mscoree.dll
api_type: COM
f1_keywords: METAHOST_POLICY_FLAGS
helpviewer_keywords: METAHOST_POLICY_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 3bb4b526-0118-42e2-ba59-c95648528ce9
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 80abed08cc7659d4218dce445be81481bb5a665b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="metahostpolicyflags-enumeration"></a>METAHOST_POLICY_FLAGS 列舉
提供通用於大多數的執行階段主機的繫結原則。 這個列舉型別由[iclrmetahostpolicy:: Getrequestedruntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)方法。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum {  
    METAHOST_POLICY_HIGHCOMPAT              = 0x00,  
    METAHOST_POLICY_APPLY_UPGRADE_POLICY    = 0x08,  
    METAHOST_POLICY_EMULATE_EXE_LAUNCH      = 0x10,  
    METAHOST_POLICY_SHOW_ERROR_DIALOG       = 0x20,  
    METAHOST_POLICY_USE_PROCESS_IMAGE_PATH  = 0x40,  
    METAHOST_POLICY_ENSURE_SKU_SUPPORTED    = 0x80,  
    METAHOST_POLICY_IGNORE_ERROR_MODE       = 0x1000  
  
} METAHOST_POLICY_FLAGS;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`METAHOST_POLICY_HIGHCOMPAT`|定義設定高相容性原則，它不會考慮任何 common language runtime (CLR) 會載入目前的處理序。 相反地，將它視為已安裝的 Clr 和喜好設定的元件，為衍生自本身的組件檔、 宣告建置針對版本或組態檔。|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|無法找到完全相符，根據 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft 內容時，就將升級的原則套用至版本繫結結果\\。NETFramework\Policy\Upgrades。 這會有相同的效果[RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md)。|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|如同啟動新的處理序的呼叫所提供的映像，則會傳回繫結結果。 目前，`GetRequestedRuntime`會略過的可載入執行階段組，並針對集合的已安裝執行階段繫結。 這個旗標可讓主機判斷 EXE 會繫結至啟動時的執行階段。|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|錯誤對話方塊會顯示如果`GetRequestedRuntime`找不到相容的輸入參數的執行階段。 開頭為[!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]，此錯誤的對話方塊中可採用的 Windows 功能 對話方塊，詢問使用者是否想要啟用適當的功能的形式。|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|`GetRequestedRuntime`使用處理序映像 （和任何對應的組態檔） 做為其他繫結程序的輸入。 根據預設，`GetRequestedRuntime`不會回到處理程序映像路徑 (通常用來啟動處理序 EXE) 來判斷要繫結至執行階段時。|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|`GetRequestedRuntime`必須檢查組態檔中不未提供任何資訊時，是否已安裝適當的 SKU。 這可讓沒有組態檔來執行正常失敗比預設安裝的.NET framework 的較小 Sku 上的應用程式。 根據預設，`GetRequestedRuntime`不會檢查除非在組態檔中指定 SKU 屬性，是否已安裝適當的 SKU`<supportedRuntime />`項目。|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|`GetRequestedRuntime`必須檢查組態檔中不未提供任何資訊時，是否已安裝適當的 SKU。 這可讓沒有組態檔來執行正常失敗比預設安裝的.NET framework 的較小 Sku 上的應用程式。 根據預設，`GetRequestedRuntime`不會檢查除非在組態檔中指定 SKU 屬性，是否已安裝適當的 SKU`<supportedRuntime />`項目。|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|`GetRequestedRuntime`應忽略 SEM_FAILCRITICALERRORS (藉由呼叫設定[SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkId=255242)函式)，並顯示錯誤對話方塊。 根據預設，SEM_FAILCRITICALERRORS 會隱藏錯誤對話方塊。 它可能有已繼承自另一個處理序，並無訊息的錯誤可能是您的案例，不需要。|  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Metahost.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
 [GetRequestedRuntime 方法](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)

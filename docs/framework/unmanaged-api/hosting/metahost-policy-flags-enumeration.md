---
title: METAHOST_POLICY_FLAGS 列舉
ms.date: 03/30/2017
api_name:
- METAHOST_POLICY_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- METAHOST_POLICY_FLAGS
helpviewer_keywords:
- METAHOST_POLICY_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 3bb4b526-0118-42e2-ba59-c95648528ce9
topic_type:
- apiref
ms.openlocfilehash: a028d2a8116de4df79f662ee8b2768e6e070428a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141394"
---
# <a name="metahost_policy_flags-enumeration"></a>METAHOST_POLICY_FLAGS 列舉
提供大部分執行時間主機通用的系結原則。 [ICLRMetaHostPolicy：： GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)方法會使用這個列舉。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`METAHOST_POLICY_HIGHCOMPAT`|定義高相容性原則，這不會考慮任何載入目前進程中的 common language runtime （CLR）。 相反地，它只會考慮已安裝的 CLRs 和元件的喜好設定，衍生自元件檔本身、宣告的內建版本或設定檔。|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|根據 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\的內容，在找不到完全相符的情況下，將升級原則套用至版本系結結果。NETFramework\Policy\Upgrades. 這與[RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md)的效果相同。|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|會傳回系結結果，就像提供給呼叫的影像是在新進程中啟動一樣。 目前，`GetRequestedRuntime` 會忽略一組可載入的執行時間，並針對一組已安裝的執行時間進行系結。 此旗標可讓主機判斷 EXE 在啟動時將系結至哪個執行時間。|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|如果 `GetRequestedRuntime` 找不到與輸入參數相容的執行時間，就會顯示錯誤對話方塊。 從 .NET Framework 4.5 開始，這個錯誤對話方塊可能會採用 Windows 功能對話方塊的形式，詢問使用者是否要啟用適當的功能。|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|`GetRequestedRuntime` 會使用處理程式映射（以及任何對應的設定檔）做為系結程式的額外輸入。 根據預設，在決定要系結的執行時間時，`GetRequestedRuntime` 不會切換回進程影像路徑（通常是用來啟動進程的 EXE）。|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|當設定檔中沒有可用的資訊時，`GetRequestedRuntime` 必須檢查是否已安裝適當的 SKU。 這可讓沒有設定檔的應用程式在較小的 Sku 上正常地失敗，而不是 .NET Framework 的預設安裝。 根據預設，除非在設定檔案 `<supportedRuntime />` 元素中指定 SKU 屬性，否則 `GetRequestedRuntime` 不會檢查是否已安裝適當的 SKU。|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|`GetRequestedRuntime` 應該忽略 SEM_FAILCRITICALERRORS （藉由呼叫[SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242)函數來設定），並顯示 [錯誤] 對話方塊。 根據預設，SEM_FAILCRITICALERRORS 會隱藏 [錯誤] 對話方塊。 它可能已繼承自另一個進程，而在您的案例中可能不需要無訊息錯誤。|  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Metahost。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [GetRequestedRuntime 方法](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)

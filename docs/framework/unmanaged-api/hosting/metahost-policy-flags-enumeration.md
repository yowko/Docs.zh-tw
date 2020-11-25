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
ms.openlocfilehash: 16fb112cf5b209091001872567c95bb0b3a8ab61
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729989"
---
# <a name="metahost_policy_flags-enumeration"></a>METAHOST_POLICY_FLAGS 列舉

提供大部分執行時間主機通用的系結原則。 此列舉是由 [ICLRMetaHostPolicy：： GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) 方法所使用。  
  
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
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`METAHOST_POLICY_HIGHCOMPAT`|定義高相容性原則，此原則不會考慮載入至目前進程 (CLR) 的任何 common language runtime。 相反地，它只會考慮已安裝的 Clr 和元件的喜好設定，衍生自元件檔本身、宣告的內建版本或設定檔案。|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|根據 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft的內容，在找不到完全相符的情況下，將升級原則套用至版本系結結果 \\ 。NETFramework\Policy\Upgrades. 這與 [RUNTIME_INFO_UPGRADE_VERSION](runtime-info-flags-enumeration.md)的效果相同。|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|如果提供給呼叫的影像在新的進程中啟動，則會傳回系結結果。 目前會 `GetRequestedRuntime` 忽略一組可載入的執行時間，並針對一組已安裝的執行時間進行系結。 這個旗標可讓主機判斷 EXE 在啟動時將系結至哪個執行時間。|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|如果找不 `GetRequestedRuntime` 到與輸入參數相容的執行時間，則會顯示 [錯誤] 對話方塊。 從 .NET Framework 4.5 開始，此錯誤對話方塊可採用 Windows 功能對話方塊的形式，詢問使用者是否想要啟用適當的功能。|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|`GetRequestedRuntime` 使用處理程式映射 (和任何對應的設定檔) 作為系結程式的額外輸入。 根據預設，不 `GetRequestedRuntime` 會切換回進程映射路徑 (通常是在判斷要系結的執行時間時，用來啟動進程) 的 EXE。|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|`GetRequestedRuntime` 當設定檔中沒有任何可用的資訊時，必須檢查是否已安裝適當的 SKU。 這可讓沒有設定檔的應用程式在較 .NET Framework 預設安裝的較小 Sku 上正常失敗。 根據預設，不 `GetRequestedRuntime` 會檢查是否已安裝適當的 sku，除非在設定檔元素中指定了 sku 屬性 `<supportedRuntime />` 。|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|`GetRequestedRuntime` 應該略過 SEM_FAILCRITICALERRORS (透過呼叫 [SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) 函數) 來設定，並顯示錯誤對話方塊。 依預設，SEM_FAILCRITICALERRORS 會隱藏 [錯誤] 對話方塊。 它可能已繼承自另一個進程，而在您的案例中，可能不需要無訊息錯誤。|  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Metahost。h  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載列舉](hosting-enumerations.md)
- [GetRequestedRuntime 方法](iclrmetahostpolicy-getrequestedruntime-method.md)

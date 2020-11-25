---
title: ICLRRuntimeInfo::GetInterface 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetInterface
helpviewer_keywords:
- GetInterface method [.NET Framework hosting]
- ICLRRuntimeInfo::GetInterface method [.NET Framework hosting]
ms.assetid: cc7b0e5b-48c3-4509-8ebb-611ddb1f7ec2
topic_type:
- apiref
ms.openlocfilehash: 192163ed8af680e39f7f3a03aee3f46546bc7450
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732069"
---
# <a name="iclrruntimeinfogetinterface-method"></a>ICLRRuntimeInfo::GetInterface 方法

將 CLR 載入目前的進程，並傳回執行時間介面指標，例如 [ICLRRuntimeHost](iclrruntimehost-interface.md)、 [ICLRStrongName](iclrstrongname-interface.md)和 [IMetaDataDispenserEx](../metadata/imetadatadispenser-interface.md)。  
  
 這個方法會取代已 `CorBindTo` 被取代的 [CLR 裝載](deprecated-clr-hosting-functions.md) 函式區段中的所有 * 函數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetInterface(  
[in]  REFCLSID rclsid,  
[in]  REFIID   riid,  
[out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a>參數  

 `rclsid`  
 在Coclass 的 CLSID 介面。  
  
 `riid`  
 在所要求介面的 IID `rclsid` 。  
  
 `ppUnk`  
 擴展查詢的介面指標。  
  
## <a name="return-value"></a>傳回值  

 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功完成命令。|  
|E_POINTER|`ppUnk` 為 null。|  
|E_OUTOFMEMORY|可用的記憶體不足，無法處理要求。|  
|CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND|不同的執行時間已系結至舊版 CLR 第2版啟用原則。|  
  
## <a name="remarks"></a>備註  

 這個方法會使 CLR 載入但未初始化。  
  
 下表顯示和支援的組合 `rclsid` `riid` 。  
  
|`rclsid`|`riid`|  
|--------------|------------|  
|CLSID_CorMetaDataDispenser|IID_IMetaDataDispenser，IID_IMetaDataDispenserEx|  
|CLSID_CorMetaDataDispenserRuntime|IID_IMetaDataDispenser，IID_IMetaDataDispenserEx|  
|CLSID_CorRuntimeHost|IID_ICorRuntimeHost|  
|CLSID_CLRRuntimeHost|IID_ICLRRuntimeHost|  
|CLSID_TypeNameFactory|IID_ITypeNameFactory|  
|CLSID_CLRDebuggingLegacy|IID_ICorDebug|  
|||  
|CLSID_CLRStrongName|IID_ICLRStrongName|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRRuntimeInfo 介面](iclrruntimeinfo-interface.md)
- [裝載介面](hosting-interfaces.md)
- [裝載](index.md)

---
title: ICLRMetaHost::EnumerateLoadedRuntimes 方法
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.EnumerateLoadedRuntimes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::EnumerateLoadedRuntimes
helpviewer_keywords:
- EnumerateLoadedRuntimes method [.NET Framework hosting]
- ICLRMetaHost::EnumerateLoadedRuntimes method [.NET Framework hosting]
ms.assetid: 22fc0a3f-dce4-4766-9a3c-9fab15f4b4ca
topic_type:
- apiref
ms.openlocfilehash: 98184dd6ea16df066905039b028acd689ff3f290
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730431"
---
# <a name="iclrmetahostenumerateloadedruntimes-method"></a>ICLRMetaHost::EnumerateLoadedRuntimes 方法

傳回列舉，其中包含在給定進程中載入的每個 common language runtime (CLR) 版本的有效 [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 介面指標。 這個方法會取代 [GetVersionFromProcess](getversionfromprocess-function.md) 函數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumerateLoadedRuntimes (  
    [in] HANDLE hndProcess,  
    [out, retval] IEnumUnknown **ppEnumerator  
);  
```  
  
## <a name="parameters"></a>參數  

 `hndProcess`  
 在檢查載入的執行時間之進程的控制碼。  
  
 `ppEnumerator`  
 擴展 <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 介面的列舉，對應至進程載入的每個 CLR。  
  
## <a name="return-value"></a>傳回值  

 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功完成命令。|  
|E_POINTER|`ppEnumerator` 為 null。|  
  
## <a name="remarks"></a>備註  

 這個方法會列出所有載入的執行時間，即使它們是使用已被取代的函式（例如 [CorBindToRuntime](corbindtoruntime-function.md)）載入的。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRMetaHost 介面](iclrmetahost-interface.md)
- [裝載](index.md)

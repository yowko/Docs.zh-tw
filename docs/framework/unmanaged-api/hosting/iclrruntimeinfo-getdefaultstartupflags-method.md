---
title: ICLRRuntimeInfo::GetDefaultStartupFlags 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetDefaultStartupFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::GetDefaultStartupFlags method [.NET Framework hosting]
- GetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 35c2173e-3b0b-4b2a-950d-e0a01c6df052
topic_type:
- apiref
ms.openlocfilehash: 2f828a3720f7313ee9cb851c6adae78bd5ea4fe8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732084"
---
# <a name="iclrruntimeinfogetdefaultstartupflags-method"></a>ICLRRuntimeInfo::GetDefaultStartupFlags 方法

取得將用來啟動執行時間的啟動旗標和主機設定檔案。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetDefaultStartupFlags(  
     [out]  DWORD *pdwStartupFlags,  
     [out, size_is(*pcchHostConfigFile)] LPWSTR pwzHostConfigFile,  
     [in, out]  DWORD *pcchHostConfigFile);  
```  
  
## <a name="parameters"></a>參數  

 `pdwStartupFlags`  
 擴展目前設定之主機啟動旗標的指標。  
  
 `pwzHostConfigFile`  
 擴展目前主機設定檔的目錄路徑指標。  
  
 `pcchHostConfigFile`  
 [in，out]在輸入時，為的大小 `pwzHostConfigFile` ，以避免緩衝區溢位。 如果 `pwzHostConfigFile` 是 null，則方法會針對預先配置傳回所需的大小 `pwzHostConfigFile` 。  
  
## <a name="return-value"></a>傳回值  

 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功完成命令。|  
  
## <a name="remarks"></a>備註  

 這個方法會傳回 (和) 的預設旗標值 `STARTUP_CONCURRENT_GC` `NULL` ，或是之前呼叫 [ICLRRuntimeInfo：： SetDefaultStartupFlags 方法](iclrruntimeinfo-setdefaultstartupflags-method.md)所提供的值，或是由任何方法所設定的值（ `CorBind*` 如果系結至這個執行時間）。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRRuntimeInfo 介面](iclrruntimeinfo-interface.md)
- [裝載介面](hosting-interfaces.md)
- [裝載](index.md)

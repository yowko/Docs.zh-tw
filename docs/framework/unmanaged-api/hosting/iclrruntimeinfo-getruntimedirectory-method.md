---
title: ICLRRuntimeInfo::GetRuntimeDirectory 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetRuntimeDirectory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetRuntimeDirectory
helpviewer_keywords:
- GetRuntimeDirectory method [.NET Framework hosting]
- ICLRRuntimeInfo::GetRuntimeDirectory method [.NET Framework hosting]
ms.assetid: 4401546e-4d48-453f-a1fb-b2ebda54df5c
topic_type:
- apiref
ms.openlocfilehash: d744abf5c502e9b9510cf9fd6479149b6c2177cc
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762210"
---
# <a name="iclrruntimeinfogetruntimedirectory-method"></a>ICLRRuntimeInfo::GetRuntimeDirectory 方法
取得與這個介面相關聯之 common language runtime （CLR）的安裝目錄。  
  
 這個方法會取代 .NET Framework 版本2.0、3.0 和3.5 中提供的[GetCORSystemDirectory](getcorsystemdirectory-function.md)函數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetRuntimeDirectory(  
[out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
[in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a>參數  
 `pwzBuffer`  
 脫銷傳回 CLR 安裝目錄。 安裝路徑是完整的;例如，"c:\windows\microsoft.net\framework\v1.0.3705 \\ "。  
  
 `pchBuffer`  
 [in、out]指定的大小 `pwzBuffer` ，以避免緩衝區溢位。 如果 `pwzBuffer` 為 null，則會傳回 `pchBuffer` 所需的大小 `pwzBuffer` 。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|已成功完成命令。|  
|E_POINTER|`pwzBuffer` 或 `pchBuffer` 為 null。|  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRRuntimeInfo 介面](iclrruntimeinfo-interface.md)
- [裝載](index.md)

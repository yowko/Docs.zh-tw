---
title: ICLRRuntimeInfo::SetDefaultStartupFlags 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.SetDefaultStartupFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::SetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::SetDefaultStartupFlags method [.NET Framework hosting]
- SetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 98ae174f-bff0-48f1-9e05-6cb63b451824
topic_type:
- apiref
ms.openlocfilehash: aa02d42511a863434fef236f90afae2c5417a78d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504013"
---
# <a name="iclrruntimeinfosetdefaultstartupflags-method"></a>ICLRRuntimeInfo::SetDefaultStartupFlags 方法
設定將用來啟動執行時間的啟動旗標和主機設定檔。 這個方法會取代 `startupFlags` [CorBindToRuntimeEx](corbindtoruntimeex-function.md)和[CorBindToRuntimeHost](corbindtoruntimehost-function.md)函式中的參數使用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetDefaultStartupFlags(  
           [in]  DWORD dwStartupFlags,  
           [in]  LPCWSTR pwzHostConfigFile);  
```  
  
## <a name="parameters"></a>參數  
 `dwStartupFlags`  
 在要設定的主機啟動旗標。 使用與[CorBindToRuntimeEx](corbindtoruntimeex-function.md)和[CorBindToRuntimeHost](corbindtoruntimehost-function.md)函數相同的旗標。  
  
 `pwzHostConfigFile`  
 在要設定的主機設定檔的目錄路徑。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT，以及指出方法失敗的 HRESULT 錯誤。  
  
|HRESULT|說明|  
|-------------|-----------------|  
|S_OK|已成功完成命令。|  
  
## <a name="remarks"></a>備註  
 多執行緒主機應該同步處理這個方法的呼叫。 否則，執行緒 A 可能會 `SetStartupFlags` 線上程 b 完成的呼叫之後 `SetStartupFlags` 和執行緒 b 啟動執行時間之前呼叫方法。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRRuntimeInfo 介面](iclrruntimeinfo-interface.md)
- [裝載介面](hosting-interfaces.md)
- [Hosting](index.md)

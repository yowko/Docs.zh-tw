---
title: ICLRRuntimeInfo::LoadLibrary 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.LoadLibrary
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::LoadLibrary
helpviewer_keywords:
- ICLRRuntimeInfo::LoadLibrary method [.NET Framework hosting]
- LoadLibrary method [.NET Framework hosting]
ms.assetid: 4517ada3-4417-4ac5-a150-73da7a87c686
topic_type:
- apiref
ms.openlocfilehash: 09c80c3a56d86943ebe00e5222bb5452ab44e150
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762171"
---
# <a name="iclrruntimeinfoloadlibrary-method"></a>ICLRRuntimeInfo::LoadLibrary 方法
從[ICLRRuntimeInfo](iclrruntimeinfo-interface.md)介面所代表的 common language RUNTIME （CLR）載入 .NET Framework 程式庫。  
  
 這個方法會取代[LoadLibraryShim](loadlibraryshim-function.md)函數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT LoadLibrary(  
     [in]  LPCWSTR pwzDllName,  
     [out, retval] HMODULE *phndModule);  
```  
  
## <a name="parameters"></a>參數  
 `pwzDllName`  
 在要載入之元件的名稱。  
  
 `phndModule`  
 脫銷載入之元件的控制碼。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|已成功完成命令。|  
|E_POINTER|`pwzDllName` 或 `phndModule` 為 null。|  
|E_OUTOFMEMORY|沒有足夠的記憶體可用來處理要求。|  
  
## <a name="remarks"></a>備註  
 這個方法只會載入包含在 .NET Framework 可轉散發套件中的 Dll。 它無法載入使用者產生的元件。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRRuntimeInfo 介面](iclrruntimeinfo-interface.md)
- [裝載介面](hosting-interfaces.md)
- [裝載](index.md)

---
title: ICLRDebugging::CanUnloadNow 方法
ms.date: 03/30/2017
api_name:
- ICLRDebugging.CanUnloadNow Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging::CanUnloadNow
helpviewer_keywords:
- CanUnloadNow method [.NET Framework debugging]
- ICLRDebugging::CanUnloadNow method [.NET Framework debugging]
ms.assetid: 62e0630c-8cb7-45d2-b622-5a472abfd8cf
topic_type:
- apiref
ms.openlocfilehash: 41b2e009f8f017a72147232015ea2357ae922ca1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793644"
---
# <a name="iclrdebuggingcanunloadnow-method"></a>ICLRDebugging::CanUnloadNow 方法
判斷[ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md)介面所提供的程式庫是否仍在使用中，或是否可以卸載。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CanUnloadNow(HMODULE hModule);  
```  
  
## <a name="parameters"></a>參數  
 `hmodule`  
 在目標進程中模組的基底位址。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`hmodule` 所參考的模組可以卸載。|  
|S_FALSE|`hmodule` 所參考的模組仍在使用中。|  
|COR_E_NOT_CLR|指出的模組不是 CLR 模組。|  
  
## <a name="exceptions"></a>例外狀況  
  
## <a name="remarks"></a>備註  
 這個方法會檢查是否已釋放 `ICorDebug*` 介面的所有實例，而且目前沒有任何執行緒在[ICLRDebugging：： OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md)方法的呼叫中。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)

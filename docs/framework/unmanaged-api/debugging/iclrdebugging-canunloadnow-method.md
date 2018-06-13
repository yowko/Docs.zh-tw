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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 557b53df3669bb0567e4d1261124ac725c796c70
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407470"
---
# <a name="iclrdebuggingcanunloadnow-method"></a>ICLRDebugging::CanUnloadNow 方法
決定是否由應用程式提供的文件庫[ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md)介面仍在使用或卸載。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CanUnloadNow(HMODULE hModule);  
```  
  
#### <a name="parameters"></a>參數  
 `hmodule`  
 [in]目標處理序模組的基底位址。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT 以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|所參考的模組`hmodule`可以卸載。|  
|S_FALSE|所參考的模組`hmodule`仍在使用中。|  
|COR_E_NOT_CLR|指定的模組不是 CLR 模組。|  
  
## <a name="exceptions"></a>例外狀況  
  
## <a name="remarks"></a>備註  
 這個方法會檢查是否所有的執行個體`ICorDebug*`已發行的介面，任何執行緒目前的呼叫中[iclrdebugging:: Openvirtualprocess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md)方法。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)

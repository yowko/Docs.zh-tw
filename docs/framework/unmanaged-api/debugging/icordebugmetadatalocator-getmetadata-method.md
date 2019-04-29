---
title: ICorDebugMetaDataLocator::GetMetaData 方法
ms.date: 03/30/2017
api_name:
- ICorDebugMetaDataLocator.GetMetaData
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMetaDataLocator::GetMetaData
helpviewer_keywords:
- ICorDebugMetaDataLocator::GetMetaData method [.NET Framework debugging]
- GetMetaData method, ICorDebugMetaDataLocator interface [.NET Framework debugging]
ms.assetid: f9b0ff22-54db-45eb-9cc3-508000a3141d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c29e581a77ac90882d102cfee2c715e9c309e1a3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780886"
---
# <a name="icordebugmetadatalocatorgetmetadata-method"></a>ICorDebugMetaDataLocator::GetMetaData 方法
要求偵錯工具傳回完整路徑到模組，其需要中繼資料以完成偵錯工具的要求。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetMetaData(  
      [in] LPCWSTR wszImagePath,  
      [in] DWORD   dwImageTimeStamp,  
      [in] DWORD   dwImageSize,  
      [in] ULONG32 cchPathBuffer,  
      [out] ULONG32 * pcchPathBuffer,  
      [out, size_is(cchPathBuffer), length_is(*pcchPathBuffer)]  
               WCHAR wszPathBuffer[]  
      );  
```  
  
## <a name="parameters"></a>參數  
 `wszImagePath`  
 [in] 以 null 結束的字串，表示檔案的完整路徑。 如果沒有提供的完整路徑的名稱和副檔名的檔案 (*檔名*。*延伸模組*)。  
  
 `dwImageTimeStamp`  
 [in] 從映像的 PE 檔標頭的時間戳記。 這個參數可能可以用於符號伺服器 ([SymSrv](/windows/desktop/debug/using-symsrv)) 查閱。  
  
 `dwImageSize`  
 [in] 從 PE 檔標頭的映像大小。 此參數可能會用於 SymSrv 查閱。  
  
 `cchPathBuffer`  
 [in] 在 `wszPathBuffer` 中的字元計數。  
  
 `pcchPathBuffer`  
 [out] `WCHAR` 的計數，寫入 `wszPathBuffer`。  
  
 如果此方法會傳回 E_NOT_SUFFICIENT_BUFFER，包含 `WCHAR` 的計數需要儲存路徑。  
  
 `wszPathBuffer`  
 [out] 偵錯工具會將包含要求的中繼資料檔案的完整路徑複製到其中的緩衝區指標。  
  
 `ofReadOnly`加上旗標，從[CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)列舉型別用來要求此檔案中的中繼資料的唯讀存取。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。 所有其他失敗的 HRESULT 表示無法擷取檔案。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功完成命令。 `wszPathBuffer` 包含檔案的完整路徑，而且是以 null 結束。|  
|E_NOT_SUFFICIENT_BUFFER|目前的大小 `wszPathBuffer` 不足以保存完整路徑。 在此情況下， `pcchPathBuffer` 包含所需的 `WCHAR` 計數，包括結束的 null 字元且 `GetMetaData` 被稱為第二次的要求緩衝區大小。|  
  
## <a name="remarks"></a>備註  
 如果 `wszImagePath` 包含來自傾印的模組完整路徑，它會指定從收集傾印所在之電腦的路徑。 檔案可能不存在這個位置，或具有相同名稱的不正確檔案可能儲存在路徑上。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugThread4 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)

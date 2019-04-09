---
title: ICorDebugProcess6::GetExportStepInfo 方法
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 44a891e6d65d159875f5607ac33b0668414cb380
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137211"
---
# <a name="icordebugprocess6getexportstepinfo-method"></a>ICorDebugProcess6::GetExportStepInfo 方法
提供執行階段匯出函式的相關資訊，以協助逐步執行 Managed 程式碼。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,   
    [out] CorDebugCodeInvokeKind* pInvokeKind,   
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
## <a name="parameters"></a>參數  
 pszExportName  
 [in] 執行階段匯出函式寫入 PE 匯出資料表時所使用的名稱。  
  
 invokeKind  
 [out]成員指標[CorDebugCodeInvokeKind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md)列舉，描述如何匯出的函式會叫用 managed 程式碼。  
  
 invokePurpose  
 [out]成員指標[CorDebugCodeInvokePurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md)描述匯出函式呼叫 managed 程式碼的原因的列舉型別。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下表所列的值。  
  
|傳回值|描述|  
|------------------|-----------------|  
|`S_OK`|方法呼叫成功。|  
|`E_POINTER`|`pInvokeKind` 或是`pInvokePurpose`已**null**。|  
|其他失敗的 `HRESULT` 值。|視需要。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  這個方法僅適用於 .NET Native。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugProcess6 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

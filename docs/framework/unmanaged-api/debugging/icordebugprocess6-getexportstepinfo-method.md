---
title: ICorDebugProcess6::GetExportStepInfo 方法
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
ms.openlocfilehash: d92b05e3d84a230e87901378f34ed27ac38286b2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123452"
---
# <a name="icordebugprocess6getexportstepinfo-method"></a>ICorDebugProcess6::GetExportStepInfo 方法
提供執行階段匯出函式的相關資訊，以協助逐步執行 Managed 程式碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,   
    [out] CorDebugCodeInvokeKind* pInvokeKind,   
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
## <a name="parameters"></a>參數  
 pszExportName  
 [in] 執行階段匯出函式寫入 PE 匯出資料表時所使用的名稱。  
  
 invokeKind  
 脫銷描述匯出函式如何叫用 managed 程式碼之[CorDebugCodeInvokeKind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md)列舉的成員指標。  
  
 invokePurpose  
 脫銷[CorDebugCodeInvokePurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md)列舉的成員指標，描述匯出的函式將呼叫 managed 程式碼的原因。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下表所列的值。  
  
|傳回值|描述|  
|------------------|-----------------|  
|`S_OK`|方法呼叫成功。|  
|`E_POINTER`|`pInvokeKind` 或 `pInvokePurpose` 是**null**。|  
|其他失敗的 `HRESULT` 值。|視需要。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個方法僅適用於 .NET Native。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugProcess6 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

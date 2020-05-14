---
title: ICorDebugVirtualUnwinder::GetContext 方法
ms.date: 03/30/2017
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
ms.openlocfilehash: e203db78b40bf4305316046cfcd679f3d10d1876
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396440"
---
# <a name="icordebugvirtualunwindergetcontext-method"></a>ICorDebugVirtualUnwinder::GetContext 方法
取得此回溯器的目前內容。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetContext(  
   [in] ULONG32 contextFlags,  
   [in] ULONG32 cbContextBuf,  
   [out] ULONG32* contextSize,  
   [out, size_is(cbContextBuf)] BYTE contextBuf[]  
);  
```  
  
## <a name="parameters"></a>參數  
 `contextFlags`  
 [in] 指定要傳回哪些內容的旗標 (在 WinNT.h 中定義)。  
  
 `cbContextBuf`  
 [in] `contextBuf` 中的位元組數。  
  
 `contextSize`  
 [out] 實際寫入至 `contextBuf` 的位元組數目指標。  
  
 `contextBuf`  
 [out] 包含此回溯器目前內容的位元組陣列。  
  
## <a name="return-value"></a>傳回值  
 mscordbi 所接收之任何失敗 HRESULT 值會視為嚴重錯誤且會導致 ICorDebug 應用程式開發介面傳回 `CORDBG_E_DATA_TARGET_ERROR`。  
  
## <a name="remarks"></a>備註  
 您可以藉 `contextBuf` 由呼叫[ICorDebugStackWalk：： GetCoNtext](icordebugstackwalk-getcontext-method.md)方法，將引數的初始值設定為傳回的內容緩衝區。  
  
> [!NOTE]
> 這個方法僅適用於 .NET Native。  
  
 由於回溯可能只還原暫存器的子集 (例如只還原非暫時性暫存器)，所以在實際方法呼叫時內容可能不完全與暫存器狀態相同。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugMemoryBuffer 介面](icordebugmemorybuffer-interface.md)
- [偵錯介面](debugging-interfaces.md)

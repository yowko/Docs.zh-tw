---
title: ICorDebugDataTarget2::EnumerateThreadIDs 方法
ms.date: 03/30/2017
ms.assetid: af02460f-2a45-496e-bc4e-a1ac4f80fe11
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d915c7d5521e630602f4dac6c905920fd2fab9d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411443"
---
# <a name="icordebugdatatarget2enumeratethreadids-method"></a>ICorDebugDataTarget2::EnumerateThreadIDs 方法
傳回使用中執行緒 ID 的清單。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT EnumerateThreadIDs(  
    [in] ULONG32 cThreadIds,   
    [out] ULONG32 *pcThreadIds,   
    [out, size_is(cThreadIds), length_is(*pcThreadIds)] ULONG32 pThreadIds[]  
);  
```  
  
#### <a name="parameters"></a>參數  
 cThreadIDs  
 [in] 可傳回其 ID 的執行緒最大數目。  
  
 pcThreadIds  
 [out] 表示寫入 `ULONG32` 陣列的實際執行緒 ID 數目之 `pThreadIds` 的指標。  
  
 pThreadIDs  
 執行緒識別項的陣列。  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  本方法只適用於 .NET 原生。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。**標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorDebugDataTarget2 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

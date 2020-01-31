---
title: ICorDebugRegisterSet2::GetRegistersAvailable 方法
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.GetRegistersAvailable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::GetRegistersAvailable
helpviewer_keywords:
- GetRegistersAvailable method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegistersAvailable method [.NET Framework debugging]
ms.assetid: f3ed344b-0d3a-44e8-8000-2a97e0805a2c
topic_type:
- apiref
ms.openlocfilehash: 00c9939b25f395010f6ea5832b405c3e9928a223
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792018"
---
# <a name="icordebugregisterset2getregistersavailable-method"></a>ICorDebugRegisterSet2::GetRegistersAvailable 方法
取得提供可用暫存器之點陣圖的位元組陣列。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
## <a name="parameters"></a>參數  
 `numChunks`  
 [in] `availableRegChunks` 陣列的大小。  
  
 `availableRegChunks`  
 脫銷位元組陣列，其中每個位對應至暫存器。 如果有可用的註冊，則會設定暫存器的對應位。  
  
## <a name="remarks"></a>備註  
 CorDebugRegister 列舉的值會指定不同微處理器的暫存器。 每個值的前五個位是 `availableRegChunks` 位元組陣列中的索引。 每個值的較低三個位識別索引位元組內的位位置。 假設有一個指定特定暫存器的 `CorDebugRegister` 值，則會以下列方式決定登錄在遮罩中的位置：  
  
1. 解壓縮存取 `availableRegChunks` 陣列中正確位元組所需的索引：  
  
     `CorDebugRegister` 值 > > 3  
  
2. 將索引位元組中的位位置解壓縮，其中 bit 零是最不重要的位：  
  
     `CorDebugRegister` 值 & 7  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugRegisterSet2 介面](icordebugregisterset2-interface.md)
- [ICorDebugRegisterSet 介面](icordebugregisterset-interface.md)

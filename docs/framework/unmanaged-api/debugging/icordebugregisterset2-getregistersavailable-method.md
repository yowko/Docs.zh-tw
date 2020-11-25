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
ms.openlocfilehash: cb56ea817d4045c19793a6290d68ae8b6236f14a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712310"
---
# <a name="icordebugregisterset2getregistersavailable-method"></a>ICorDebugRegisterSet2::GetRegistersAvailable 方法

取得位元組陣列，以提供可用暫存器的點陣圖。  
  
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
 擴展位元組陣列，每個位都對應到一個暫存器。 如果有可用的暫存器，則會設定註冊程式的對應位。  
  
## <a name="remarks"></a>備註  

 CorDebugRegister 列舉的值會指定不同微處理器的暫存器。 每個值的前五個位是位元組陣列中的索引 `availableRegChunks` 。 每個值的下半部會識別索引位元組內的位位置。 指定特定暫存器的 `CorDebugRegister` 值時，在遮罩中的暫存器位置會依照下列方式決定：  
  
1. 解壓縮存取陣列中正確位元組所需的索引 `availableRegChunks` ：  
  
     `CorDebugRegister` 值 >> 3  
  
2. 將索引位元組內的位位置解壓縮，其中 bit 零是最不重要的位：  
  
     `CorDebugRegister` 值 & 7  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugRegisterSet2 介面](icordebugregisterset2-interface.md)
- [ICorDebugRegisterSet 介面](icordebugregisterset-interface.md)

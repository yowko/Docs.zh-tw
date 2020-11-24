---
title: ICorDebugProcess2::SetUnmanagedBreakpoint 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.SetUnmanagedBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint
helpviewer_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint method [.NET Framework debugging]
- SetUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 93829d15-d942-4e2d-b7a4-dfc9d7fb96be
topic_type:
- apiref
ms.openlocfilehash: 1a883878107569145b97d5793f0628efefb13545
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675239"
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a>ICorDebugProcess2::SetUnmanagedBreakpoint 方法

在指定的原生映射位移上設定未受管理的中斷點。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetUnmanagedBreakpoint (  
    [in]  CORDB_ADDRESS    address,  
    [in]  ULONG32          bufsize,  
    [out, size_is(bufsize), length_is(*bufLen)]
        BYTE               buffer[],  
    [out] ULONG32          *bufLen  
);  
```  
  
## <a name="parameters"></a>參數  

 `address`  
 在 `CORDB_ADDRESS` 指定原生影像位移的物件。  
  
 `bufsize`  
 在陣列的大小（以位元組為單位） `buffer` 。  
  
 `buffer`  
 擴展陣列，其中包含由中斷點所取代的 opcode。  
  
 `bufLen`  
 擴展陣列中傳回的位元組數目的指標 `buffer` 。  
  
## <a name="remarks"></a>備註  

 如果原生映射位移是在 common language runtime (CLR) 內，則會忽略中斷點。 當偵錯工具設定中斷點時，這可讓 CLR 避免分派頻外中斷點。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

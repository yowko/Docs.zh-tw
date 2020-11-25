---
title: ICorDebugCode::CreateBreakpoint 方法
ms.date: 03/30/2017
api_name:
- ICorDebugCode.CreateBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::CreateBreakpoint
helpviewer_keywords:
- ICorDebugCode::CreateBreakpoint method [.NET Framework debugging]
- CreateBreakpoint method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 46842618-0fe4-480b-871c-82fba82d23d9
topic_type:
- apiref
ms.openlocfilehash: ade428ce001a6b40e2fed67f4f23b12cef5ea30f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717639"
---
# <a name="icordebugcodecreatebreakpoint-method"></a>ICorDebugCode::CreateBreakpoint 方法

在此程式碼片段中，于指定的位移建立中斷點。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateBreakpoint (  
    [in] ULONG32     offset,  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
## <a name="parameters"></a>參數  

 `offset`  
 在要在其中建立中斷點的位移。  
  
 `ppBreakpoint`  
 擴展代表中斷點的 "ICorDebugFunctionBreakpoint" 物件位址的指標。  
  
## <a name="remarks"></a>備註  

 在中斷點開始使用之前，必須先將它新增至處理常式物件。  
  
 如果這段程式碼是 Microsoft 中繼語言 (MSIL) 程式碼，而且有即時 (JIT) 編譯的機器碼機器碼，則中斷點也會套用在 JIT 編譯的程式碼中。 如果稍後以 JIT 編譯程式碼， (相同的情況。 )   
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

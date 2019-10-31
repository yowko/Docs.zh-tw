---
title: ICorDebugILFrame::CanSetIP 方法
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::CanSetIP
helpviewer_keywords:
- CanSetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::CanSetIP method [.NET Framework debugging]
ms.assetid: 16caf02f-c71e-486c-90b0-f0e54357d8f0
topic_type:
- apiref
ms.openlocfilehash: 57d83d1f301cbfd43f8f553d9aef4beb3baf95f8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131076"
---
# <a name="icordebugilframecansetip-method"></a>ICorDebugILFrame::CanSetIP 方法
取得 HRESULT，指出是否可以安全地在 Microsoft 中繼語言（MSIL）程式碼中，將指令指標設定為指定的位移位置。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
## <a name="parameters"></a>參數  
 `nOffset`  
 在指令指標所需的設定。  
  
## <a name="remarks"></a>備註  
 呼叫[ICorDebugILFrame：： SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)方法之前，請先使用 `CanSetIP` 方法。 如果 `CanSetIP` 傳回 S_OK 以外的任何 HRESULT，您仍然可以叫用 `ICorDebugILFrame::SetIP`，但不保證偵錯工具將會繼續執行所要調試之程式碼的安全和正確執行。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cordebug.h .idl、Cordebug.h、h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

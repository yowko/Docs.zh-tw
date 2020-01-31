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
ms.openlocfilehash: c6a02b080739d00667893008be4a19b4fa9a6ef2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788597"
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
 呼叫[ICorDebugILFrame：： SetIP](icordebugilframe-setip-method.md)方法之前，請先使用 `CanSetIP` 方法。 如果 `CanSetIP` 會傳回 S_OK 以外的任何 HRESULT，您仍然可以叫用 `ICorDebugILFrame::SetIP`，但不保證偵錯工具會繼續安全且正確地執行正在進行調試的程式碼。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cordebug.h .idl、Cordebug.h、h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

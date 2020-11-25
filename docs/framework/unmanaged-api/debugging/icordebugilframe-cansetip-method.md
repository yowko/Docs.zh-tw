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
ms.openlocfilehash: 99c80fba594e9eaf69a3cc9a025509aa4c3c26a4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703300"
---
# <a name="icordebugilframecansetip-method"></a>ICorDebugILFrame::CanSetIP 方法

取得 HRESULT，指出是否可以安全地將指令指標設定為 Microsoft 中繼語言 (MSIL) 程式碼中指定的位移位置。  
  
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

 在 `CanSetIP` 呼叫 [ICorDebugILFrame：： SetIP](icordebugilframe-setip-method.md) 方法之前，請先使用方法。 如果傳回 `CanSetIP` S_OK 以外的任何 HRESULT，您仍然可以叫用 `ICorDebugILFrame::SetIP` ，但不保證偵錯工具會繼續執行正在進行程式碼的安全且正確的執行。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cordebug.h .idl、Cordebug.h、h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

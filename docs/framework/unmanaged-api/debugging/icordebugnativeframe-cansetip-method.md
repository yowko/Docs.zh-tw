---
title: ICorDebugNativeFrame::CanSetIP 方法
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::CanSetIP
helpviewer_keywords:
- ICorDebugNativeFrame::CanSetIP method [.NET Framework debugging]
- CanSetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 13258ac6-f4e4-4f66-8fc3-f1244417a3c3
topic_type:
- apiref
ms.openlocfilehash: 21890f8130ec677cb88f2f5d7ef648aa19e67e71
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213058"
---
# <a name="icordebugnativeframecansetip-method"></a>ICorDebugNativeFrame::CanSetIP 方法
取得 HRESULT，指出是否可以安全地將指令指標（IP）設定為機器碼中的指定位移位置。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32            nOffset  
);  
```  
  
## <a name="parameters"></a>參數  
 `nOffset`  
 在指令指標所需的設定。  
  
## <a name="remarks"></a>備註  
 `CanSetIP`呼叫[ICorDebugNativeFrame：： SetIP](icordebugnativeframe-setip-method.md)方法之前，請先使用方法。 如果傳回 `CanSetIP` 除了 S_OK 以外的任何 HRESULT，您仍然可以叫用 `ICorDebugNativeFrame::SetIP` ，但不保證偵錯工具會繼續執行所要調試之程式碼的安全和正確執行。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

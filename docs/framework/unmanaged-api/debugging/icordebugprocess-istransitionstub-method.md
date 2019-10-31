---
title: ICorDebugProcess::IsTransitionStub 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.IsTransitionStub
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsTransitionStub
helpviewer_keywords:
- ICorDebugProcess::IsTransitionStub method [.NET Framework debugging]
- IsTransitionStub method [.NET Framework debugging]
ms.assetid: f7653317-7e48-4163-be03-f50f1a4b0f70
topic_type:
- apiref
ms.openlocfilehash: 852c77be0dc8ef91933bacbbd3d6b3f5a69ae8c8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139383"
---
# <a name="icordebugprocessistransitionstub-method"></a>ICorDebugProcess::IsTransitionStub 方法
取得值，指出位址是否在將導致轉換成 managed 程式碼的存根內部。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
## <a name="parameters"></a>參數  
 `address`  
 在指定有問題之位址的 `CORDB_ADDRESS` 值。  
  
 `pbTransitionStub`  
 脫銷布林值的指標，如果指定的位址位於會導致轉換成 managed 程式碼的存根內部，則為 `true`：否則，會 `false``pbTransitionStub`。  
  
## <a name="remarks"></a>備註  
 未受管理的逐步執行程式碼可以使用 `IsTransitionStub` 方法，決定何時要將逐步執行控制傳回給 managed 分檔器。  
  
 您也可以查看可移植執行檔（PE）檔案中的資訊，以識別轉換存根。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

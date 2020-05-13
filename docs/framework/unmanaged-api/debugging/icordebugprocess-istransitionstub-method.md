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
ms.openlocfilehash: ab2121605f974fdf3f9053214a4d29d8b0dd72db
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210696"
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
 在`CORDB_ADDRESS`值，指定有問題的位址。  
  
 `pbTransitionStub`  
 脫銷布林值的指標， `true` 如果指定的位址位於會導致轉換成 managed 程式碼的存根內部，則為，否則為 * `pbTransitionStub` `false` 。  
  
## <a name="remarks"></a>備註  
 未受管理的 `IsTransitionStub` 逐步執行程式碼可以使用方法，決定何時要將逐步執行控制傳回給 managed 分檔器。  
  
 您也可以查看可移植執行檔（PE）檔案中的資訊，以識別轉換存根。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

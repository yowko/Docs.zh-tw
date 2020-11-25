---
title: ICorDebugThread::GetHandle 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetHandle method [.NET Framework debugging]
ms.assetid: 172ef8c4-2ead-4cfc-bd2e-dee4fb7191cd
topic_type:
- apiref
ms.openlocfilehash: 5debd09f3ca0b4562f62913f9530cc4fa6f9110b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728026"
---
# <a name="icordebugthreadgethandle-method"></a>ICorDebugThread::GetHandle 方法

取得此 ICorDebugThread 之使用中部分的目前控制碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetHandle (  
    [out] HTHREAD *phThreadHandle  
);  
```  
  
## <a name="parameters"></a>參數  

 `phThreadHandle`  
 擴展HTHREAD 的指標，該指標是此執行緒之使用中部分的控制碼。  
  
## <a name="remarks"></a>備註  

 當程式執行時，控制碼可能會變更，而執行緒的不同部分可能會有不同的控制碼。  
  
 這個控制碼是由偵錯工具 API 所擁有。 偵錯工具應該在使用之前複製它。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

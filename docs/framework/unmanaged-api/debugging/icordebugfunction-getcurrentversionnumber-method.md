---
title: ICorDebugFunction::GetCurrentVersionNumber 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetCurrentVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetCurrentVersionNumber
helpviewer_keywords:
- GetCurrentVersionNumber method [.NET Framework debugging]
- ICorDebugFunction::GetCurrentVersionNumber method [.NET Framework debugging]
ms.assetid: c3af1575-cbe6-457a-bc08-c53460edcbc8
topic_type:
- apiref
ms.openlocfilehash: 14579d4c84be9bb225e618715b3a7d45ccaac0a9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728143"
---
# <a name="icordebugfunctiongetcurrentversionnumber-method"></a>ICorDebugFunction::GetCurrentVersionNumber 方法

取得這個 ICorDebugFunction 物件所代表之函式的最新編輯版本號碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetCurrentVersionNumber (  
    [out] ULONG32 *pnCurrentVersion  
);  
```  
  
## <a name="parameters"></a>參數  

 `pnCurrentVersion`  
 擴展整數值的指標，此為對此函數所做之最新編輯的版本號碼。  
  
## <a name="remarks"></a>備註  

 對此函式所做的最新編輯版本號碼，可能會大於函數本身的版本號碼。 您可以使用 [ICorDebugFunction2：： GetVersionNumber](icordebugfunction2-getversionnumber-method.md) 方法或 [ICorDebugCode：： GetVersionNumber](icordebugcode-getversionnumber-method.md) 方法來取出函數的版本號碼。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

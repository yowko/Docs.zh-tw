---
title: CreateCordbObject 函式
ms.date: 03/30/2017
api_name:
- CreateCoredbObject
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCordbObject
helpviewer_keywords:
- remote debugging API [Silverlight]
- CreateCordbObject function
- Silverlight, remote debugging
ms.assetid: b259821d-4fa7-464d-85cf-304dfffc8089
topic_type:
- apiref
ms.openlocfilehash: 2716adcc8c79c8003202561ea2011c2469a6bc5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179224"
---
# <a name="createcordbobject-function"></a>CreateCordbObject 函式
創建調試器介面 （[ICorDebug](icordebug-interface.md)）， 提供在遠端進程上具現化託管調試會話的功能。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,
       [out] IUnknown**  ppCordb  
);  
```  
  
## <a name="parameters"></a>參數  
 `iDebuggerVersion`  
 [in] 目標處理序的偵錯工具版本。 這個參數必須是 CorDebugVersion_2_0，才能進行遠端偵錯。  
  
 `ppCordb`  
 [出]指向將強制轉換為[ICorDebug](icordebug-interface.md)介面並返回的物件的指標。  
  
## <a name="return-value"></a>傳回值  
 S_OK  
 已成功確定處理序中的 CLR 數目，並且已正確填入對應的控制代碼和路徑陣列。  
  
 E_INVALIDARG  
 `ppCordb` 為 null，或 `iDebuggerVersion` 不是 CorDebugVersion_2_0。  
  
 E_OUTOFMEMORY  
 無法為 `ppCordb` 配置足夠的記憶體。  
  
 E_FAIL (或其他 E_ 傳回碼)  
 其他失敗。  
  
## <a name="remarks"></a>備註  
 返回的`ppCordb` [ICorDebug](icordebug-interface.md)介面是所有託管調試服務的頂級調試介面。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 核心Clr遠端偵錯介面.h  
  
 **資料庫：** mscordbi_macx86.dll  
  
 **.NET 框架版本：** 3.5 SP1

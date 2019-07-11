---
title: ICorDebugILFrame::EnumerateArguments 方法
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.EnumerateArguments
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::EnumerateArguments
helpviewer_keywords:
- ICorDebugILFrame::EnumerateArguments method [.NET Framework debugging]
- EnumerateArguments method [.NET Framework debugging]
ms.assetid: 00ac81e2-a774-422a-bd88-54a4b3c99f73
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 499f58cc0a3f2d1b3c159435ed7d9b523f25e29e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757899"
---
# <a name="icordebugilframeenumeratearguments-method"></a>ICorDebugILFrame::EnumerateArguments 方法
取得列舉值的引數，這個框架中。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumerateArguments (  
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppValueEnum`  
 [out]ICorDebugValueEnum 物件，在此框架的引數的列舉值的位址指標。  
  
## <a name="remarks"></a>備註  
 `EnumerateArguments` 取得可以列出此 ICorDebugILFrame 物件所代表的呼叫框架中可用的引數的列舉值。 此清單將包含所引數[vararg](/cpp/windows/vararg) （也就是可變數目的引數） 以及非引數`vararg`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

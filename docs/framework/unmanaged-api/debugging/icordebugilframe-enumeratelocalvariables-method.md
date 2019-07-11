---
title: ICorDebugILFrame::EnumerateLocalVariables 方法
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.EnumerateLocalVariables
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::EnumerateLocalVariables
helpviewer_keywords:
- EnumerateLocalVariables method [.NET Framework debugging]
- ICorDebugILFrame::EnumerateLocalVariables method [.NET Framework debugging]
ms.assetid: 1a67fa1b-2419-4cd0-aad4-6f46a0719b4b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c18f2fce23e979f27d9116e74b6c6b007cd33bf0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752895"
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a>ICorDebugILFrame::EnumerateLocalVariables 方法
取得這個框架中區域變數的列舉值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumerateLocalVariables(   
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppValueEnum`  
 [out]ICorDebugValueEnum 物件，這個框架中區域變數的列舉值的位址指標。  
  
## <a name="remarks"></a>備註  
 `EnumerateLocalVariables` 取得可以列出可用此 ICorDebugILFrame 物件所代表的呼叫框架中區域變數的列舉值。 清單可能不包含所有的本機變數中執行的函式，因為其中部分可能不是作用中。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

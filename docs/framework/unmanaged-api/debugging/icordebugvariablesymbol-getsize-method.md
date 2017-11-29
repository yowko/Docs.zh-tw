---
title: ICorDebugVariableSymbol::GetSize Method
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: add0cd9d-9a29-49b1-ae07-d9d3786b4ccd
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0ea4a77b08b12c3f067d51f9dfe2c961192c3354
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablesymbolgetsize-method"></a>ICorDebugVariableSymbol::GetSize Method
取得變數的大小，以位元組為單位。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pcbValue`  
 32 位元不帶正負號的整數指標，這個整數包含變數的大小。  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  這個方法僅適用於 .NET 原生。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorDebugVariableSymbol 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

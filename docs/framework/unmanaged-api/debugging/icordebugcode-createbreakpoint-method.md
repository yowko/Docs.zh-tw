---
title: "ICorDebugCode::CreateBreakpoint 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode.CreateBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode::CreateBreakpoint
helpviewer_keywords:
- ICorDebugCode::CreateBreakpoint method [.NET Framework debugging]
- CreateBreakpoint method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 46842618-0fe4-480b-871c-82fba82d23d9
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 211435025fe06eff180244430138be9d42c5eb86
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcodecreatebreakpoint-method"></a>ICorDebugCode::CreateBreakpoint 方法
指定的位移此程式碼區段中建立的中斷點。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CreateBreakpoint (  
    [in] ULONG32     offset,  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
#### <a name="parameters"></a>參數  
 `offset`  
 [in]要建立的中斷點處的位移。  
  
 `ppBreakpoint`  
 [out]表示中斷點"ICorDebugFunctionBreakpoint 」 物件的位址指標。  
  
## <a name="remarks"></a>備註  
 中斷點為作用中，它必須先新增至處理程序物件。  
  
 如果此程式碼是 Microsoft intermediate language (MSIL) 程式碼，而且沒有在 just-in-time (JIT)-JIT 編譯程式碼中也會套用原生編譯版本的程式碼中斷點。 （也是如此如果程式碼為 JIT 編譯更新版本。）  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 

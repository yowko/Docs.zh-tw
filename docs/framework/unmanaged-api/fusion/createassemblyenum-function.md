---
title: "CreateAssemblyEnum 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateAssemblyEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type: DLLExport
f1_keywords: CreateAssemblyEnum
helpviewer_keywords: CreateAssemblyEnum function [.NET Framework fusion]
ms.assetid: 3506df38-6cea-42f6-946e-4287863bcfb3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3719da442b2c2c589772a0bc19cec3efb4e6dace
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="createassemblyenum-function"></a>CreateAssemblyEnum 函式
取得指標[IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)可以列舉具有指定組件中的物件的執行個體[IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
#### <a name="parameters"></a>參數  
 `pEnum`  
 [out]包含所要求的記憶體位置的指標`IAssemblyEnum`指標。  
  
 `pUnkReserved`  
 [in]保留供未來擴充。 `pUnkReserved`必須是 null 參考。  
  
 `pName`  
 [in]`IAssemblyName`要求的組件。 這個名稱用來篩選列舉型別。 它可以是 null 來列舉在全域組件快取中的所有組件。  
  
 `dwFlags`  
 [in]修改列舉值的行為的旗標。 這個參數會包含從剛好包含一個位元[ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md)列舉型別。  
  
 `pvReserved`  
 [in]保留供未來擴充。 `pvReserved`必須是 null 參考。  
  
## <a name="remarks"></a>備註  
 `dwFlags`參數包含剛好一個位元從`ASM_CACHE_FLAGS`列舉型別。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Fusion.h  
  
 **程式庫：**包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [IAssemblyEnum 介面](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)  
 [IAssemblyName 介面](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [融合全域靜態函式](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)

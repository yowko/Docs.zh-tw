---
title: ICorDebugILFrame2 Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2
helpviewer_keywords:
- ICorDebugILFrame2 interface [.NET Framework debugging]
ms.assetid: f94b9d53-d8f8-4424-a95e-53a1bfd26e4a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ccb39609b37aff09ac7890df562d6c08e3c3c159
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugilframe2-interface1"></a>ICorDebugILFrame2 Interface1
ICorDebugILFrame 介面邏輯擴充。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[EnumerateTypeParameters 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md)|取得包含 ICorDebugTypeEnum 物件<xref:System.Type>這個框架中的參數。|  
|[RemapFunction 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md)|重新對應已編輯函式，藉由指定新的 MSIL 位移。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

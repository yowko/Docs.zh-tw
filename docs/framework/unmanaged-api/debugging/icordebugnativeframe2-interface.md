---
title: ICorDebugNativeFrame2 介面
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2
helpviewer_keywords:
- ICorDebugNativeFrame2 interface [.NET Framework debugging]
ms.assetid: 52a80838-af36-4399-bc97-d8a4c6d76df2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dd8f1adee6bbcb3b57b87a2d6c85c01c624da9ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugnativeframe2-interface"></a>ICorDebugNativeFrame2 介面
提供測試父子框架關聯的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[IsChild 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ischild-method.md)|判斷目前的框架是子框架。|  
|[IsMatchingParentFrame 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md)|判斷指定的範圍是否為目前的畫面格的父代。|  
|[GetStackParameterSize 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-getstackparametersize-method.md)|在 x86 作業系統上的堆疊上傳回參數的累計大小。|  
  
## <a name="remarks"></a>備註  
 這個介面會以邏輯方式擴充 「 ICorDebugNativeFrame"介面。  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
    
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)

---
title: ICorDebugILCode2 介面
ms.date: 03/30/2017
api_name:
- ICorDebugILCode2
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: f9dc2afd-df8a-464d-bdbf-5af0a1d4bf85
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1982226e90792d4bbda1cb023d80dec96fcb2060
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugilcode2-interface"></a>ICorDebugILCode2 介面
[在 .NET Framework 4.5.2 及更新版本中支援]  
  
 以邏輯方式擴充[ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)介面，提供方法，傳回的語彙基元函式的區域變數簽章，而且，它將對應剖析工具檢測中繼語言 (IL) 位移至原始方法 IL位移。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetInstrumentedILMap 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)|將分析工具中的已檢測 IL 位移對應傳回至此執行個體的原始方法 IL 位移。|  
|[GetLocalVarSigToken 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getlocalvarsigtoken-method.md)|針對此執行個體表示的函式，取得區域變數簽章的中繼資料語彙基元。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorDebugILCode 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)

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
ms.openlocfilehash: 30008d6cc98f7d0d0501d67e18703ed5a344d43a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794369"
---
# <a name="icordebugilcode2-interface"></a>ICorDebugILCode2 介面
[.NET Framework 4.5.2 與更新版本提供支援]  
  
 以邏輯方式擴充[ICorDebugILCode](icordebugilcode-interface.md)介面，以提供方法來傳回函式的區域變數簽章的 token，並將分析工具的檢測中繼語言（IL）位移對應至原始方法 IL 位移。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetInstrumentedILMap 方法](icordebugilcode2-getinstrumentedilmap-method.md)|將分析工具中的已檢測 IL 位移對應傳回至此執行個體的原始方法 IL 位移。|  
|[GetLocalVarSigToken 方法](icordebugilcode2-getlocalvarsigtoken-method.md)|針對此執行個體表示的函式，取得區域變數簽章的中繼資料語彙基元。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugILCode 介面](icordebugilcode-interface.md)
- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)

---
title: ICorProfilerInfo8 介面
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 210029ed1b1c7d780f3895f975f7a72227bbea80
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973818"
---
# <a name="icorprofilerinfo8-interface"></a>ICorProfilerInfo8 介面

[ICorProfilerInfo7](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)的子類別, 提供方法來查詢動態方法的相關資訊。

## <a name="methods"></a>方法  

| 方法|說明|  
| ------------|-----------------|  
|[IsFunctionDynamic 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-isfunctiondynamic-method.md)| 判斷函數是否沒有相關聯的中繼資料。|
|[GetFunctionFromIP3 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-getfunctionfromip3-method.md)| 將 managed 程式碼指令指標對應至 FunctionID。 這個方法適用于動態和非動態方法。 |
|[GetDynamicFunctionInfo 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-getdynamicfunctioninfo-method.md)| 抓取動態方法的相關資訊。 |

## <a name="requirements"></a>需求  
**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
**標頭：** Corprof.idl .idl, Corprof.idl。h  
**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
## <a name="see-also"></a>另請參閱
- [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)

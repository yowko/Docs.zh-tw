---
title: ICorProfilerInfo8 介面
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 476bcbd91188e3ff9eb63f50cfa2118a440b1a69
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868313"
---
# <a name="icorprofilerinfo8-interface"></a>ICorProfilerInfo8 介面

[ICorProfilerInfo7](icorprofilerinfo7-interface.md)的子類別，提供方法來查詢動態方法的相關資訊。

## <a name="methods"></a>方法  

| 方法|描述|  
| ------------|-----------------|  
|[IsFunctionDynamic 方法](icorprofilerinfo8-isfunctiondynamic-method.md)| 判斷函數是否沒有相關聯的中繼資料。|
|[GetFunctionFromIP3 方法](icorprofilerinfo8-getfunctionfromip3-method.md)| 將 managed 程式碼指令指標對應至 FunctionID。 這個方法適用于動態和非動態方法。 |
|[GetDynamicFunctionInfo 方法](icorprofilerinfo8-getdynamicfunctioninfo-method.md)| 抓取動態方法的相關資訊。 |

## <a name="requirements"></a>需求  
**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
**標頭：** CorProf.idl、CorProf.h  
**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  

## <a name="see-also"></a>請參閱

- [分析介面](profiling-interfaces.md)

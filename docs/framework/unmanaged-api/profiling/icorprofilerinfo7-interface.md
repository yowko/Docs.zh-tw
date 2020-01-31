---
title: ICorProfilerInfo7 介面
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
ms.openlocfilehash: f80f310c10bae33583cb7cd2048ede4f5efbe14c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861745"
---
# <a name="icorprofilerinfo7-interface"></a>ICorProfilerInfo7 介面
[在 .NET Framework 4.6.1 及更新版本中支援]  
  
 [ICorProfilerInfo6](icorprofilerinfo6-interface.md)的子類別，提供方法來將新定義的中繼資料套用至模組，並提供記憶體內部符號資料流程的存取權。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[ApplyMetaData 方法](icorprofilerinfo7-applymetadata-method.md)|將 `IMetadataEmit::Define*` 方法新定義的中繼資料套用至指定的模組。|  
|[GetInMemorySymbolsLength 方法](icorprofilerinfo7-getinmemorysymbolslength-method.md)|傳回記憶體中符號資料流程的長度。|  
|[ReadInMemorySymbols](icorprofilerinfo7-readinmemorysymbols.md)|從記憶體中的符號資料流程讀取位元組。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [分析介面](profiling-interfaces.md)

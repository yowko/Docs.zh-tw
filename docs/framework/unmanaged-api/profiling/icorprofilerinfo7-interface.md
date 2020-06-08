---
title: ICorProfilerInfo7 介面
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
ms.openlocfilehash: 0e9f76717aeff27e863245faac241927e7495076
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495485"
---
# <a name="icorprofilerinfo7-interface"></a>ICorProfilerInfo7 介面
[在 .NET Framework 4.6.1 及更新版本中支援]  
  
 [ICorProfilerInfo6](icorprofilerinfo6-interface.md)的子類別，提供方法來將新定義的中繼資料套用至模組，並提供記憶體內部符號資料流程的存取權。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[ApplyMetaData 方法](icorprofilerinfo7-applymetadata-method.md)|將方法新定義的中繼資料套用 `IMetadataEmit::Define*` 至指定的模組。|  
|[GetInMemorySymbolsLength 方法](icorprofilerinfo7-getinmemorysymbolslength-method.md)|傳回記憶體中符號資料流程的長度。|  
|[ReadInMemorySymbols](icorprofilerinfo7-readinmemorysymbols.md)|從記憶體中的符號資料流程讀取位元組。|  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [分析介面](profiling-interfaces.md)

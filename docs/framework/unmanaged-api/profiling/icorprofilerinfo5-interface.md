---
title: ICorProfilerInfo5 介面
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo5
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 7bd48c34-37ed-4230-9eec-39a17280f05d
topic_type:
- apiref
ms.openlocfilehash: 82f6262c2c576b49be4e7fcaa14043950df4c67a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495623"
---
# <a name="icorprofilerinfo5-interface"></a>ICorProfilerInfo5 介面
[.NET Framework 4.5.2 與更新版本提供支援]  
  
 [ICorProfilerInfo4](icorprofilerinfo4-interface.md)的子類別，提供程式碼分析工具用來與 common language RUNTIME （CLR）通訊以控制事件監視的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetEventMask2 方法](icorprofilerinfo5-geteventmask2-method.md)|取得分析工具想要從 CLR 接收的目前事件分類通知。|  
|[SetEventMask2 方法](icorprofilerinfo5-seteventmask2-method.md)|設定一個值，以指定分析工具想要從 CLR 接收事件通知的事件類型。|  
  
## <a name="remarks"></a>備註  
 此介面上可用的方法是用來取代[ICorProfilerInfo：： GetEventMask](icorprofilerinfo-geteventmask-method.md)和[ICorProfilerInfo：： SetEventMask](icorprofilerinfo-seteventmask-method.md)方法。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [分析介面](profiling-interfaces.md)

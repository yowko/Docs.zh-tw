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
ms.openlocfilehash: 655cdd5db0894a4e44d43b071caf1ee0829ffe50
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861719"
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
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [分析介面](profiling-interfaces.md)

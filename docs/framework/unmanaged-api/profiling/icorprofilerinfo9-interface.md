---
title: ICorProfilerInfo9 介面
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 0ba4f2b4a515143d50bc812f04ea75d821b69471
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973798"
---
# <a name="icorprofilerinfo9-interface"></a>ICorProfilerInfo9 介面

[ICorProfilerInfo8](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md)的子類別, 提供方法來查詢具有多個機器碼版本之函數的相關資訊。  

## <a name="methods"></a>方法  

| 方法|描述|  
| ------------|-----------------|  
|[GetNativeCodeStartAddresses 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getnativecodestartaddresses-method.md)| 假設有 functionId 和 rejitId, 會列舉此程式碼中所有目前存在之已編譯版本的原生程式碼起始位址。 |
|[GetILToNativeMapping3 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getiltonativemapping3-method.md)| 假設機器碼的起始位址, 會傳回這個程式碼編譯版本的原生到 IL 對應資訊。 |
|[GetCodeInfo4 方法](icorprofilerinfo9-getcodeinfo4-method.md)| 假設機器碼的起始位址, 會傳回儲存此程式碼的虛擬記憶體區塊。 |

## <a name="requirements"></a>需求  
**平台：** 請參閱[.Net Core 支援的作業系統](../../../core/windows-prerequisites.md#net-core-supported-operating-systems)。  
**標頭：** Corprof.idl .idl, Corprof.idl。h  
**.Net 版本:** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]  
## <a name="see-also"></a>另請參閱
- [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)

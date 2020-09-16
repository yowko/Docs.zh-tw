---
title: ICorProfilerInfo9 介面
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: f38195b1a7983e23c7f5c20055ea8c2a8bfcb7d8
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556846"
---
# <a name="icorprofilerinfo9-interface"></a>ICorProfilerInfo9 介面

[ICorProfilerInfo8](icorprofilerinfo8-interface.md)的子類別，可提供方法來查詢具有多個機器碼版本的函式相關資訊。  

## <a name="methods"></a>方法  

| 方法|描述|  
| ------------|-----------------|  
|[GetNativeCodeStartAddresses 方法](icorprofilerinfo9-getnativecodestartaddresses-method.md)| 在指定 functionId 和 rejitId 的情況下，列舉此程式碼目前存在的所有可編譯版本的機器碼開始位址。 |
|[GetILToNativeMapping3 方法](icorprofilerinfo9-getiltonativemapping3-method.md)| 在指定機器碼起始位址的情況下，傳回此程式碼的程式碼的原生對應資訊。 |
|[GetCodeInfo4 方法](icorprofilerinfo9-getcodeinfo4-method.md)| 在指定機器碼起始位址的情況下，傳回儲存此程式碼的虛擬記憶體區塊。 |

## <a name="requirements"></a>需求  
**平臺：** 請參閱 [.Net Core 支援的作業系統](../../../core/install/windows.md?pivots=os-windows)。  
**標頭：** CorProf.idl、CorProf.h  
**.Net 版本：**[!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]  

## <a name="see-also"></a>另請參閱

- [分析介面](profiling-interfaces.md)

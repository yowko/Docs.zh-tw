---
title: "COR_PRF_FUNCTION_ARGUMENT_INFO 結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_FUNCTION_ARGUMENT_INFO
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_FUNCTION_ARGUMENT_INFO
helpviewer_keywords: COR_PRF_FUNCTION_ARGUMENT_INFO structure [.NET Framework profiling]
ms.assetid: 07cf3bab-e193-4991-8205-3f41cf2d67b3
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e26377fe3c5cfbae68f90087e3fb624ae4db0dc8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="corprffunctionargumentinfo-structure"></a>COR_PRF_FUNCTION_ARGUMENT_INFO 結構
代表函式的引數，順序由左至右。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_INFO {  
    ULONG numRanges;  
    ULONG totalArgumentSize;  
    COR_PRF_FUNCTION_ARGUMENT_RANGE ranges[1];  
} COR_PRF_FUNCTION_ARGUMENT_INFO;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`numRanges`|引數的區塊數目。 也就是說，這個值是數目[COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md)中結構`ranges`陣列。|  
|`totalArgumentSize`|所有引數的大小總計。 換句話說，這個值會是引數長度的總和。|  
|`ranges`|陣列`COR_PRF_FUNCTION_ARGUMENT_RANGE`結構，其中每一個都代表一個區塊函式引數。|  
  
## <a name="remarks"></a>備註  
 函式可能會有多個引數。 這些引數可能會不會由左至右連續儲存在記憶體中。 您可能必須區塊的兩個引數中的其他位置，以及最後一個區塊中的不同位置有一個引數的一個位置中的三個引數區塊。 這些引數都相同的函式。它們只儲存在不同的地方。  
  
 `COR_PRF_FUNCTION_ARGUMENT_INFO`結構表示的單一函式的所有引數。 它會使用陣列參考的函式引數的所有區塊。 因此，在單一函式，您有單一`COR_PRF_FUNCTION_ARGUMENT_INFO`結構，它會參考多個`COR_PRF_FUNCTION_ARGUMENT_RANGE`結構，其中每個指向一個或多個函式引數。  
  
 儲存在暫存器中的引數會溢出到記憶體，建立結構。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [分析結構](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)

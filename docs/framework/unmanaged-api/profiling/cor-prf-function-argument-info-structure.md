---
title: COR_PRF_FUNCTION_ARGUMENT_INFO 結構
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION_ARGUMENT_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION_ARGUMENT_INFO
helpviewer_keywords:
- COR_PRF_FUNCTION_ARGUMENT_INFO structure [.NET Framework profiling]
ms.assetid: 07cf3bab-e193-4991-8205-3f41cf2d67b3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 293ad30ebf47ca8684d158b1ae1772ab245d7981
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775085"
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
|`numRanges`|引數的區塊數目。 也就是說，這個值是數目[COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md)結構中`ranges`陣列。|  
|`totalArgumentSize`|所有引數的大小總計。 換句話說，這個值會是引數長度的總和。|  
|`ranges`|陣列`COR_PRF_FUNCTION_ARGUMENT_RANGE`結構，每一個都代表一個區塊的函式引數。|  
  
## <a name="remarks"></a>備註  
 函式可能會有多個引數。 這些引數不可能在記憶體中儲存連續。 您可能必須在不同的位置有一個引數的最後一個區塊、 區塊的兩個引數，在另一個位置，以及在一處的三個引數的區塊。 這些引數都相同的函式;它們只儲存在不同的位置。  
  
 `COR_PRF_FUNCTION_ARGUMENT_INFO`結構代表單一函式的所有引數。 它會使用陣列參考的函式引數的所有區塊。 因此，在單一的函式，您擁有單一`COR_PRF_FUNCTION_ARGUMENT_INFO`結構，參考多個`COR_PRF_FUNCTION_ARGUMENT_RANGE`結構，其中每一個指向一或多個函式引數。  
  
 會儲存在暫存器中的引數會溢出到記憶體中建立的結構。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [分析結構](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)

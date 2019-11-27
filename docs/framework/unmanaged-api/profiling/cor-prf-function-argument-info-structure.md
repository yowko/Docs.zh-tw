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
ms.openlocfilehash: 2b01acbd617b13a64ef3dca6c8661f1e6bb067ac
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447378"
---
# <a name="cor_prf_function_argument_info-structure"></a>COR_PRF_FUNCTION_ARGUMENT_INFO 結構
代表函式的引數，順序由左至右。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_INFO {  
    ULONG numRanges;  
    ULONG totalArgumentSize;  
    COR_PRF_FUNCTION_ARGUMENT_RANGE ranges[1];  
} COR_PRF_FUNCTION_ARGUMENT_INFO;  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`numRanges`|引數的區塊數目。 也就是說，此值是 `ranges` 陣列中[COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md)結構的數目。|  
|`totalArgumentSize`|所有引數的總大小。 換句話說，此值是引數長度的總和。|  
|`ranges`|`COR_PRF_FUNCTION_ARGUMENT_RANGE` 結構的陣列，其中每一個都代表一個函式引數的區塊。|  
  
## <a name="remarks"></a>備註  
 函數可能有許多引數。 這些引數可能不會連續儲存于記憶體中。 在一個位置中，您可能會有三個引數的區塊、另一個位置的兩個引數區塊，以及在不同位置的一個引數的最後一個區塊。 這些引數全都適用于相同的函式;它們只會儲存在不同的位置。  
  
 `COR_PRF_FUNCTION_ARGUMENT_INFO` 結構代表單一函式的所有引數。 它會使用陣列來參考函數引數的所有區塊。 因此，在單一函式中，您會有一個參考多個 `COR_PRF_FUNCTION_ARGUMENT_RANGE` 結構的單一 `COR_PRF_FUNCTION_ARGUMENT_INFO` 結構，每一個都指向一個或多個函式引數。  
  
 儲存在暫存器中的引數會溢出到記憶體中，以建立結構。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Corprof.idl .idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [分析結構](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)

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
ms.openlocfilehash: 9fca75ae59b95a226b51768b3e1bfb220d9926f1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500958"
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
  
## <a name="members"></a>成員  
  
|成員|說明|  
|------------|-----------------|  
|`numRanges`|引數的區塊數目。 也就是說，此值是陣列中[COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md)結構的數目 `ranges` 。|  
|`totalArgumentSize`|所有引數的總大小。 換句話說，此值是引數長度的總和。|  
|`ranges`|結構的陣列 `COR_PRF_FUNCTION_ARGUMENT_RANGE` ，其中每一個都代表函式引數的一個區塊。|  
  
## <a name="remarks"></a>備註  
 函數可能有許多引數。 這些引數可能不會連續儲存于記憶體中。 在一個位置中，您可能會有三個引數的區塊、另一個位置的兩個引數區塊，以及在不同位置的一個引數的最後一個區塊。 這些引數全都適用于相同的函式;它們只會儲存在不同的位置。  
  
 `COR_PRF_FUNCTION_ARGUMENT_INFO`結構代表單一函式的所有引數。 它會使用陣列來參考函數引數的所有區塊。 因此，在單一函式中，您有一個 `COR_PRF_FUNCTION_ARGUMENT_INFO` 參考多個結構的單一結構， `COR_PRF_FUNCTION_ARGUMENT_RANGE` 每個結構都指向一個或多個函式引數。  
  
 儲存在暫存器中的引數會溢出到記憶體中，以建立結構。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Corprof.idl .idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [分析結構](profiling-structures.md)

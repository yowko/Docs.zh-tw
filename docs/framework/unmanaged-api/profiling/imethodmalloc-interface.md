---
title: IMethodMalloc 介面
ms.date: 03/30/2017
api_name:
- IMethodMalloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc
helpviewer_keywords:
- IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8c8ab5dc-557c-473a-82f2-6e403eca7dac
topic_type:
- apiref
ms.openlocfilehash: 12b97b28383eb7c39f20ee0e88f55d48e60ad956
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494095"
---
# <a name="imethodmalloc-interface"></a>IMethodMalloc 介面
提供方法來為新的 Microsoft 中繼語言（MSIL）函數主體配置記憶體。  
  
> [!NOTE]
> `IMethodMalloc`介面是簡單的記憶體配置器。 它可讓您配置記憶體，但不能釋放它。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Alloc 方法](imethodmalloc-alloc-method.md)|嘗試為新的 MSIL 函數主體配置指定的記憶體數量。|  
  
## <a name="remarks"></a>備註  
 每個配置器都是模組特有的，並可確保函式主體會位於模組基底的正位移。 高於模組基底的記憶體可能非常寶貴，因此應該使用配置器只為函式主體配置記憶體。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [分析介面](profiling-interfaces.md)

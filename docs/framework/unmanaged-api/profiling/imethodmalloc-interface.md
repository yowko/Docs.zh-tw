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
ms.openlocfilehash: 8eccdba75b59df505ae72d74cfcd2bc83de2b45a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688168"
---
# <a name="imethodmalloc-interface"></a>IMethodMalloc 介面

提供方法，為新的 Microsoft 中繼語言 (MSIL) 函式主體中配置記憶體。  
  
> [!NOTE]
> `IMethodMalloc`介面是簡單的記憶體配置器。 它可讓您配置記憶體，但無法釋放記憶體。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Alloc 方法](imethodmalloc-alloc-method.md)|嘗試為新的 MSIL 函數主體配置指定的記憶體數量。|  
  
## <a name="remarks"></a>備註  

 每個配置器都是模組專屬的，可確保函式主體會與模組基底的正位移。 在模組基底之上的記憶體可能很寶貴，因此配置器只能用來配置函數主體的記憶體。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [分析介面](profiling-interfaces.md)

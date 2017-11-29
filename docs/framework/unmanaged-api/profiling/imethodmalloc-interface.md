---
title: "IMethodMalloc 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMethodMalloc
api_location: mscorwks.dll
api_type: COM
f1_keywords: IMethodMalloc
helpviewer_keywords: IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8c8ab5dc-557c-473a-82f2-6e403eca7dac
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d246f329f80a76d2c93190fd663c7362418385f7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="imethodmalloc-interface"></a>IMethodMalloc 介面
提供方法來為新的 Microsoft intermediate language (MSIL) 函式主體配置記憶體。  
  
> [!NOTE]
>  `IMethodMalloc`介面是簡單的記憶體配置器。 它可讓您配置記憶體，但不是將它釋放。  
  
## <a name="methods"></a>方法  
  
|方法|說明|  
|------------|-----------------|  
|[Alloc 方法](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|嘗試為新的 MSIL 函式主體配置指定的記憶體數量。|  
  
## <a name="remarks"></a>備註  
 每個配置器為特定模組，並確保函式主體會在正的模組基底位移。 以上的模組基底的記憶體可以珍貴，因此配置器應該用來只針對函式主體配置記憶體。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)

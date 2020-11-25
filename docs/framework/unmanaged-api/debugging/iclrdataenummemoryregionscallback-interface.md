---
title: ICLRDataEnumMemoryRegionsCallback 介面
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegionsCallback
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegionsCallback
helpviewer_keywords:
- ICLRDataEnumMemoryRegionsCallback interface [.NET Framework debugging]
ms.assetid: 3f1af8b0-8478-48e0-a7ec-3e90e0b97649
topic_type:
- apiref
ms.openlocfilehash: f080d852b190346740a3629f3b5d46a9f3808293
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703625"
---
# <a name="iclrdataenummemoryregionscallback-interface"></a>ICLRDataEnumMemoryRegionsCallback 介面

提供 [ICLRDataEnumMemoryRegions：： EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) 的回呼方法，以向偵錯工具報告嘗試列舉指定之記憶體區域的結果。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[EnumMemoryRegion 方法](iclrdataenummemoryregionscallback-enummemoryregion-method.md)|呼叫 `ICLRDataEnumMemoryRegions::EnumMemoryRegions` 以向偵錯工具報告嘗試列舉指定記憶體區域的結果。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** ClrData .idl、ClrData。h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)

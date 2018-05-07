---
title: ICLRDataTarget2 介面
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2
helpviewer_keywords:
- ICLRDataTarget2 interface [.NET Framework debugging]
ms.assetid: 94249397-861b-4294-a538-cf01466a66d3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6fc26694bded2c7df1a53a96e8743f3be73c93eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="iclrdatatarget2-interface"></a>ICLRDataTarget2 介面
子類別[ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)資料存取服務層用來管理目標處理序中的虛擬記憶體區域。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[AllocVirtual 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)|配置記憶體中目標處理序的位址空間。|  
|[FreeVirtual 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)|釋放先前在目標處理序的位址空間配置的記憶體。|  
  
## <a name="remarks"></a>備註  
 API 用戶端 (也就是偵錯工具) 必須針對適合的特定目標處理序實作這個介面。 例如，即時處理序的實作與記憶體傾印的實作不同。 目標可能不支援修改其記憶體區域。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** ClrData.idl、 ClrData.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICLRDataTarget 介面](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

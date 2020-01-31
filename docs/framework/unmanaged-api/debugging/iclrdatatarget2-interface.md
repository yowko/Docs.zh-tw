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
ms.openlocfilehash: bdc8378a129dd5bb1d9fdcb080c7b5cd53d34091
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789067"
---
# <a name="iclrdatatarget2-interface"></a>ICLRDataTarget2 介面
資料存取服務層用來操作目標進程中虛擬記憶體區域的[ICLRDataTarget](iclrdatatarget-interface.md)子類別。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[AllocVirtual 方法](iclrdatatarget2-allocvirtual-method.md)|在目標進程的位址空間中配置記憶體。|  
|[FreeVirtual 方法](iclrdatatarget2-freevirtual-method.md)|釋放先前在目標進程的位址空間中配置的記憶體。|  
  
## <a name="remarks"></a>備註  
 API 用戶端 (也就是偵錯工具) 必須針對適合的特定目標處理序實作這個介面。 例如，即時處理序的實作與記憶體傾印的實作不同。 目標可能不支援修改其記憶體區域。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** ClrData .idl，ClrData。h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICLRDataTarget 介面](iclrdatatarget-interface.md)
- [偵錯介面](debugging-interfaces.md)

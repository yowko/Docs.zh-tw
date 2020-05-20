---
title: ICLRGCManager2 介面
ms.date: 03/30/2017
api_name:
- ICLRGCManager2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager2
helpviewer_keywords:
- ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 4b5ffd7b-9ad7-41cd-9bba-34030ae3da7e
topic_type:
- apiref
ms.openlocfilehash: 0f3ecc0d497eaee937647df47ba0956335a2fe41
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703953"
---
# <a name="iclrgcmanager2-interface"></a>ICLRGCManager2 介面
提供可讓主機與 common language runtime 的垃圾收集系統互動的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[SetGCStartupLimitsEx 方法](iclrgcmanager2-setgcstartuplimitsex-method.md)|設定垃圾收集區段的大小，以及垃圾收集系統層代0的大小上限。 啟用層代0和區段大小大於 `DWORD` 。|  
  
## <a name="remarks"></a>備註  
 此介面繼承自[ICLRGCManager 介面](iclrgcmanager-interface.md)。  
  
 Common language runtime （CLR）會使用 managed 類型來執行其垃圾收集機制 <xref:System.GC> 。 如需垃圾收集系統的詳細資訊，請參閱[垃圾收集](../../../standard/garbage-collection/index.md)。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [自動記憶體管理](../../../standard/automatic-memory-management.md)
- [COR_GC_STATS 結構](cor-gc-stats-structure.md)
- [ICLRControl 介面](iclrcontrol-interface.md)
- [.NET Framework 4 和 4.5 中新增的 CLR 裝載介面](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [裝載介面](hosting-interfaces.md)
- [裝載](index.md)

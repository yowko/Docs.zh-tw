---
title: ICLRGCManager 介面
ms.date: 03/30/2017
api_name:
- ICLRGCManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager
helpviewer_keywords:
- ICLRGCManager interface [.NET Framework hosting]
ms.assetid: fb511c9b-3fe4-41b0-822a-6ba4a079d1f5
topic_type:
- apiref
ms.openlocfilehash: f878e2f1f86bc42c0ff5abada8d7df4feb9ed228
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504182"
---
# <a name="iclrgcmanager-interface"></a>ICLRGCManager 介面
提供可讓主機與 common language runtime 的垃圾收集系統互動的方法。  
  
> [!NOTE]
> 從 .NET Framework 4.5 開始，您可以使用[ICLRGCManager2：： SetGCStartupLimitsEx](iclrgcmanager2-setgcstartuplimitsex-method.md)方法，將垃圾收集區段的大小，以及垃圾收集系統層代0的大小上限設定為大於 `DWORD` [SetGCStartupLimits](iclrgcmanager-setgcstartuplimits-method.md)方法所加諸限制的值。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Collect 方法](iclrgcmanager-collect-method.md)|強制執行指定之層代的垃圾收集。|  
|[GetStats 方法](iclrgcmanager-getstats-method.md)|取得有關垃圾收集系統的一組目前統計資料。|  
|[SetGCStartupLimits 方法](iclrgcmanager-setgcstartuplimits-method.md)|設定垃圾收集區段的大小，以及垃圾收集系統層代0的大小上限。|  
  
## <a name="remarks"></a>備註  
 Common language runtime （CLR）會使用 managed 類型來執行其垃圾收集機制 <xref:System.GC> 。 如需垃圾收集系統的詳細資訊，請參閱[垃圾收集](../../../standard/garbage-collection/index.md)。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [自動記憶體管理](../../../standard/automatic-memory-management.md)
- [COR_GC_STATS 結構](cor-gc-stats-structure.md)
- [ICLRControl 介面](iclrcontrol-interface.md)
- [CLR 裝載介面](clr-hosting-interfaces.md)
- [裝載介面](hosting-interfaces.md)
- [Hosting](index.md)

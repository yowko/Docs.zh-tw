---
title: IGCHost2 介面
ms.date: 03/30/2017
api_name:
- IGCHost2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost2
helpviewer_keywords:
- IGCHost2 interface [.NET Framework hosting]
ms.assetid: e5323fa4-18ac-424d-859d-a65a550d08d9
topic_type:
- apiref
ms.openlocfilehash: 7529ecd215d74eb0eedbec8b90eba367ed20d56f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687739"
---
# <a name="igchost2-interface"></a>IGCHost2 介面

提供方法來取得垃圾收集系統的相關資訊，以及控制垃圾收集的某些層面。  
  
> [!NOTE]
> 針對新的開發，我們建議您改用 [ICLRGCManager2](iclrgcmanager2-interface.md) 介面。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[SetGCStartupLimitsEx 方法](igchost2-setgcstartuplimitsex-method.md)|設定層代0的區段大小和大小上限。 啟用超出的層代0和區段大小 `DWORD` 。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** GCHost .idl、GCHost。h  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載介面](hosting-interfaces.md)
- [CLR 裝載介面](clr-hosting-interfaces.md)
- [CorRuntimeHost Coclass](corruntimehost-coclass.md)

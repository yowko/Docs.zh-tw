---
title: IGCHost::Collect 方法
ms.date: 03/30/2017
api_name:
- IGCHost.Collect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Collect
helpviewer_keywords:
- Collect method, IGCHost interface [.NET Framework hosting]
- IGCHost::Collect method [.NET Framework hosting]
ms.assetid: fc7d9448-3186-494d-9f0d-ea39717e9a82
topic_type:
- apiref
ms.openlocfilehash: e20ea6addc1ae3f99b4b3d65f532e0128ac160b3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134964"
---
# <a name="igchostcollect-method"></a>IGCHost::Collect 方法
無論目前垃圾收集的狀態為何，都會強制針對給定的層代進行集合。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a>參數  
 `Generation`  
 在要在其上執行垃圾收集的產生。 -1 值表示所有層代都會進行垃圾收集。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** GCHost .idl，GCHost。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [IGCHost 介面](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)

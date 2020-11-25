---
title: ICLRRuntimeInfo::IsLoadable 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoadable
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoadable
helpviewer_keywords:
- IsLoadable method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoadable method [.NET Framework hosting]
ms.assetid: 205ca53b-e78e-49b2-9a46-2a7823e96b8c
topic_type:
- apiref
ms.openlocfilehash: 2236e815211168d8e7105375b75f30128f7f209a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714962"
---
# <a name="iclrruntimeinfoisloadable-method"></a>ICLRRuntimeInfo::IsLoadable 方法

指出與這個介面相關聯的執行時間是否可以載入至目前的進程，並將可能已載入至進程的其他執行時間納入考慮。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT IsLoadable(  
        [out, retval] BOOL *pbLoadable);  
```  
  
## <a name="parameters"></a>參數  

 `pbLoadable`  
 [out] `true` 如果此執行時間可以載入至目前的進程，則為。否則為 `false` 。  
  
## <a name="return-value"></a>傳回值  

 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功完成命令。|  
|E_POINTER|`pbLoadable` 為 null。|  
  
## <a name="remarks"></a>備註  

 如果另一個執行時間已載入至進程，而且可以載入與此介面相關聯的執行時間，以進行同進程並存執行，則會 `pbLoadable` 傳回 `true` 。 如果這兩個執行時間無法並存在進程中執行，則會 `pbLoadable` 傳回 `false` 。 例如，common language runtime (CLR) 第4版可在與 CLR 2.0 版或 CLR 1.1 版相同的進程中並存執行。 不過，CLR 1.1 版和 CLR 2.0 版無法並存執行同進程。  
  
 如果沒有任何執行時間載入至進程，這個方法一律會傳回 `true` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRRuntimeInfo 介面](iclrruntimeinfo-interface.md)
- [裝載介面](hosting-interfaces.md)
- [裝載](index.md)

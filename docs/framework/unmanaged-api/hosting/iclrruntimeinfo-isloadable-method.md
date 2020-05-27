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
ms.openlocfilehash: a1cd169fc4be5b1dd3ab1a83f4ad143ba2e2442b
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007360"
---
# <a name="iclrruntimeinfoisloadable-method"></a>ICLRRuntimeInfo::IsLoadable 方法
指出與這個介面相關聯的執行時間是否可以載入目前的進程中，並考慮可能已經載入進程的其他執行時間。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT IsLoadable(  
        [out, retval] BOOL *pbLoadable);  
```  
  
## <a name="parameters"></a>參數  
 `pbLoadable`  
 [out] `true`如果此執行時間可以載入至目前的進程，則為，否則為 `false` 。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功完成命令。|  
|E_POINTER|`pbLoadable` 為 null。|  
  
## <a name="remarks"></a>備註  
 如果另一個執行時間已載入進程中，而且可以載入與此介面相關聯的執行時間，以進行同進程並存執行，會傳回 `pbLoadable` `true` 。 如果這兩個執行時間無法並行在進程中執行，則會 `pbLoadable` 傳回 `false` 。 例如，common language runtime （CLR）第4版可以在 CLR 版本2.0 或 CLR 1.1 版的相同進程中並存執行。 不過，CLR 版本1.1 和 CLR 版本2.0 無法並存執行同進程。  
  
 如果未將執行時間載入進程中，這個方法一律會傳回 `true` 。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRRuntimeInfo 介面](iclrruntimeinfo-interface.md)
- [裝載介面](hosting-interfaces.md)
- [裝載](index.md)

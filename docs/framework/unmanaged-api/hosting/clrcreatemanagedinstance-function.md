---
title: ClrCreateManagedInstance 函式
ms.date: 03/30/2017
api_name:
- ClrCreateManagedInstance
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- ClrCreateManagedInstance
helpviewer_keywords:
- ClrCreateManagedInstance function [.NET Framework hosting]
ms.assetid: 58ba42c0-4857-43bf-a039-73a4dc6544c2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1c576bd4a7bc29be2647a858a680b91e602d2c4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57488873"
---
# <a name="clrcreatemanagedinstance-function"></a>ClrCreateManagedInstance 函式
建立指定之 managed 型別的執行個體。  
  
 此函式中的過時[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。 若要建立的 managed 類型中，執行個體中使用 COM 啟動，或使用裝載 (請參閱[CLR 裝載介面中加入.NET Framework 4 和 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md))。  
  
## <a name="syntax"></a>語法  
  
```  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,   
    [in]  REFIID   riid,   
    [out] void     **ppObject  
);  
```  
  
## <a name="parameters"></a>參數  
 `pTypeName`  
 [in]所要求的執行個體類型的名稱指標。  
  
 `riid`  
 [in]`IID`所要求的執行個體類型。  
  
 `ppObject`  
 [out]指標的指標，呼叫端所要求之 managed 型別的執行個體。  
  
## <a name="remarks"></a>備註  
 Common language runtime 已應載入的程序。 例如，藉由呼叫載入[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)函式之前`ClrCreateManagedInstance`呼叫函式。 如果未載入執行階段，`ClrCreateManagedInstance`第一次嘗試載入 v1.0.3705 的執行階段。 如果失敗，它會嘗試載入的執行階段的最新版本。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：** MSCorEE.dll  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [裝載](../../../../docs/framework/unmanaged-api/hosting/index.md)

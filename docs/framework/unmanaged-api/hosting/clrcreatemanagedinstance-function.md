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
ms.openlocfilehash: ecd618ecf08836ea5e38ce738f97fc91ee6426f4
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616807"
---
# <a name="clrcreatemanagedinstance-function"></a>ClrCreateManagedInstance 函式
建立指定之 managed 類型的實例。  
  
 此函式在 .NET Framework 4 中已被取代。 使用 COM 啟動來建立 managed 類型的實例，或使用裝載（請參閱[在 .NET Framework 4 和4.5 中新增的 CLR 裝載介面](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)）。  
  
## <a name="syntax"></a>語法  
  
```cpp  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,
    [in]  REFIID   riid,
    [out] void     **ppObject  
);  
```  
  
## <a name="parameters"></a>參數  
 `pTypeName`  
 在所要求之實例類型名稱的指標。  
  
 `riid`  
 在所 `IID` 要求之實例類型的。  
  
 `ppObject`  
 脫銷呼叫端所要求之 managed 型別的實例指標。  
  
## <a name="remarks"></a>備註  
 通用語言執行平臺應該已經載入進程中。 例如，您可以在呼叫函式之前，使用[CorBindToRuntimeEx](corbindtoruntimeex-function.md)函式的呼叫來載入它 `ClrCreateManagedInstance` 。 如果未載入執行時間，會 `ClrCreateManagedInstance` 先嘗試載入執行時間的 v v1.0.3705。 如果失敗，則會嘗試載入最新版本的執行時間。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** Mscoree.dll .dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [已被取代的 CLR 裝載函式](deprecated-clr-hosting-functions.md)
- [裝載](index.md)

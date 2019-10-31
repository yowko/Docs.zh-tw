---
title: IsFrameworkAssembly 函式
ms.date: 03/30/2017
api_name:
- IsFrameworkAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IsFrameworkAssembly
helpviewer_keywords:
- IsFrameworkAssembly function [.NET Framework fusion]
ms.assetid: b0c6f19b-d4fd-4971-88f0-12ffb5793da3
topic_type:
- apiref
ms.openlocfilehash: e30b6f2d2254d2d107c4c82a2c5664850ce6ec23
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123074"
---
# <a name="isframeworkassembly-function"></a>IsFrameworkAssembly 函式
取得值，指出指定的元件是否為 managed。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
## <a name="parameters"></a>參數  
 `pwzAssemblyReference`  
 在要檢查之元件的名稱。  
  
 `pbIsFrameworkAssembly`  
 脫銷布林值，指出元件是否受管理。  
  
 `pwzFrameworkAssemblyIdentity`  
 在Uncanonicalized 字串，其中包含元件的唯一識別。  
  
 `pccSize`  
 [in] `pwzFrameworkAssemblyIdentity` 的大小。  
  
## <a name="remarks"></a>備註  
 `pwzAssemblyReference` 參數是字元字串的指標，其中包含元件的名稱。  
  
 如果這個元件是 .NET Framework 的一部分，`pbIsFrameworkAssembly` 參數將會包含 `true`的布林值。  
  
 如果命名元件不是 .NET Framework 的一部分，或如果 `pwzAssemblyReference` 參數未命名元件，`pbIsFrameworkAssembly` 會包含 `false`的布林值。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
## <a name="see-also"></a>請參閱

- [融合全域靜態函式](fusion-global-static-functions.md)

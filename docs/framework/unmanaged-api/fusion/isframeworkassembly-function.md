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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 269e3702c21532f377735ba6087abb1603dde4f7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796325"
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
 `pwzAssemblyReference`參數是字元字串的指標，其中包含元件的名稱。  
  
 如果這個元件是 .NET Framework 的一部分，則`pbIsFrameworkAssembly`參數會包含的布林`true`值。  
  
 如果命名元件不是 .NET Framework 的一部分，或如果`pwzAssemblyReference`參數不是元件的名稱， `pbIsFrameworkAssembly`則會`false`包含的布林值。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
## <a name="see-also"></a>另請參閱

- [融合全域靜態函式](fusion-global-static-functions.md)

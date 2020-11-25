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
ms.openlocfilehash: 828c7660d6c006e700302d119ce4caf7d76e5d84
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728559"
---
# <a name="isframeworkassembly-function"></a>IsFrameworkAssembly 函式

取得值，這個值會指出指定的元件是否為 managed。  
  
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
 在要檢查的元件名稱。  
  
 `pbIsFrameworkAssembly`  
 擴展指出元件是否受管理的布林值。  
  
 `pwzFrameworkAssemblyIdentity`  
 在Uncanonicalized 字串，其中包含元件的唯一識別。  
  
 `pccSize`  
 [in] `pwzFrameworkAssemblyIdentity` 的大小。  
  
## <a name="remarks"></a>備註  

 `pwzAssemblyReference`參數是包含元件名稱的字元字串指標。  
  
 如果這個元件是 .NET Framework 的一部分， `pbIsFrameworkAssembly` 參數將包含的布林值 `true` 。  
  
 如果命名的元件不是 .NET Framework 的一部分，或如果參數未 `pwzAssemblyReference` 命名元件， `pbIsFrameworkAssembly` 將會包含的布林值 `false` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
## <a name="see-also"></a>另請參閱

- [融合全域靜態函式](fusion-global-static-functions.md)

---
title: StrongNameCompareAssemblies 函式
ms.date: 03/30/2017
api_name:
- StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameCompareAssemblies
helpviewer_keywords:
- StrongNameCompareAssemblies function [.NET Framework strong naming]
ms.assetid: 763f2375-efc6-4219-8806-a3b0567ef72b
topic_type:
- apiref
ms.openlocfilehash: e7292635ea0344f1c77c8d44908a9a811e464ff9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732303"
---
# <a name="strongnamecompareassemblies-function"></a>StrongNameCompareAssemblies 函式

判斷兩個組件是否只有強制名稱簽章不同。  
  
 此函數已被取代。 請改用 [ICLRStrongName：： StrongNameCompareAssemblies](../hosting/iclrstrongname-strongnamecompareassemblies-method.md) 方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
BOOLEAN StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a>參數  

 `wszAssembly1`  
 在第一個元件的路徑。  
  
 `wszAssembly2`  
 在第二個元件的路徑。  
  
 `pdwResult`  
 擴展下列其中一個值：  
  
- `SN_CMP_DIFFERENT` (0) -指定元件包含不同的資料。  
  
- `SN_CMP_IDENTICAL` (1) -指定元件完全相同，包括其簽章和總和檢查碼。  
  
- `SN_CMP_SIGONLY` (2) -指定元件只有簽章和總和檢查碼不同。  
  
## <a name="return-value"></a>傳回值  

 `true` 成功完成時;否則為 `false` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Stackexchange.redis.strongname。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="remarks"></a>備註  

 元件的強式名稱簽章是由元件的文字名稱、版本、文化特性和公開金鑰 token 所組成。  
  
 如果函式 `StrongNameCompareAssemblies` 未順利完成，請呼叫 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 函式來取出最後產生的錯誤。  
  
## <a name="see-also"></a>另請參閱

- [StrongNameCompareAssemblies 方法](../hosting/iclrstrongname-strongnamecompareassemblies-method.md)
- [ICLRStrongName 介面](../hosting/iclrstrongname-interface.md)

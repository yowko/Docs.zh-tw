---
title: GetHashFromAssemblyFile 函式
ms.date: 03/30/2017
api_name:
- GetHashFromAssemblyFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromAssemblyFile
helpviewer_keywords:
- GetHashFromAssemblyFile function [.NET Framework strong naming]
ms.assetid: 751ed69f-b7ab-4e07-80de-e17ca9319b0c
topic_type:
- apiref
ms.openlocfilehash: caefc9773b0d208f8b20847b664f7bc017d2c076
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730990"
---
# <a name="gethashfromassemblyfile-function"></a>GetHashFromAssemblyFile 函式

使用指定的雜湊演算法取得所指定組件檔案的雜湊。  
  
 此函數已被取代。 請改用 [ICLRStrongName：： GetHashFromAssemblyFile](../hosting/iclrstrongname-gethashfromassemblyfile-method.md) 方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a>參數  

 `szFilePath`  
 在要雜湊處理之檔案的路徑。  
  
 `piHashAlg`  
 [in，out]指定雜湊演算法的常數。 使用零作為預設雜湊演算法。  
  
 `pbHash`  
 擴展傳回的雜湊緩衝區。  
  
 `cchHash`  
 在要求的大小上限 `pbHash` 。  
  
 `pchHash`  
 擴展傳回的大小（以位元組為單位） `pbHash` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Stackexchange.redis.strongname。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [GetHashFromAssemblyFile 方法](../hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [GetHashFromAssemblyFileW 方法](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [ICLRStrongName 介面](../hosting/iclrstrongname-interface.md)

---
title: ISymUnmanagedSymbolSearchInfo::GetSearchPath 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo.GetSearchPath
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo::GetSearchPath
helpviewer_keywords:
- GetSearchPath method [.NET Framework debugging]
- ISymUnmanagedSymbolSearchInfo::GetSearchPath method [.NET Framework debugging]
ms.assetid: b588d470-53c2-4492-be8c-957323eaca0b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 62eb5782071b42df1a035a4553b6cf9da53e24ac
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778092"
---
# <a name="isymunmanagedsymbolsearchinfogetsearchpath-method"></a>ISymUnmanagedSymbolSearchInfo::GetSearchPath 方法
取得搜尋路徑。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetSearchPathLength(  
    [out] ULONG32 *pcchPath);  
```  
  
## <a name="parameters"></a>參數  
 `pcchPath`  
 [out]指標`ULONG32`接收大小，以字元為單位，以包含搜尋路徑所需的緩衝區。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。  
  
## <a name="requirements"></a>需求  
 **標頭：** 於 CorSym.idl CorSym.h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedSymbolSearchInfo 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)

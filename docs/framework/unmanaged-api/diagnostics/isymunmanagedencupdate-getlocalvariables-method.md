---
title: ISymUnmanagedENCUpdate::GetLocalVariables 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.GetLocalVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables method [.NET Framework debugging]
- GetLocalVariables method [.NET Framework debugging]
ms.assetid: 5c8840be-ffea-447f-9c8d-178f1eaf8d06
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 82e657e91e586d7fe409646ea4fb8946c026e84c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedencupdategetlocalvariables-method"></a>ISymUnmanagedENCUpdate::GetLocalVariables 方法
取得區域變數。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetLocalVariables(  
    [in]  mdMethodDef  mdMethodToken,  
    [in]  ULONG        cLocals,  
    [out, size_is(cLocals), length_is(*pceltFetched)]  
        ISymUnmanagedVariable *rgLocals[],  
    [out] ULONG        *pceltFetched);  
```  
  
#### <a name="parameters"></a>參數  
 `mdMethodToken`  
 [in]方法的中繼資料語彙基元。  
  
 `cLocals`  
 [in]A`ULONG`指出的大小`rgLocals`參數。  
  
 `rgLocals`  
 [out]傳回的陣列的<!--zz<xref:ISymUnmanagedVariable>-->`ISymUnmanagedVariable`執行個體。  
  
 `pceltFetched`  
 [out]指標`ULONG`大小`rgLocals`包含區域變數所需要的緩衝區。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。  
  
## <a name="requirements"></a>需求  
 **標頭：**於 CorSym.idl、 CorSym.h  
  
## <a name="see-also"></a>另請參閱  
 [ISymUnmanagedENCUpdate 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)

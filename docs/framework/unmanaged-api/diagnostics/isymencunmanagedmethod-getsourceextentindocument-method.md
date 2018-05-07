---
title: ISymENCUnmanagedMethod::GetSourceExtentInDocument 方法
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetSourceExtentInDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetSourceExtentInDocument
helpviewer_keywords:
- GetSourceExtentInDocument method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetSourceExtentInDocument method [.NET Framework debugging]
ms.assetid: 9c5566ab-4ec7-4b61-9753-839bb90ae78c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dc3a986326f9b47194558ca86bcbeabb61dbaeb3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="isymencunmanagedmethodgetsourceextentindocument-method"></a>ISymENCUnmanagedMethod::GetSourceExtentInDocument 方法
取得最小起始行和最大的結尾行方法特定的文件中。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetSourceExtentInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [out] ULONG32* pstartLine,  
    [out] ULONG32* pendLine);  
```  
  
#### <a name="parameters"></a>參數  
 `document`  
 [in]文件指標。  
  
 `pstartLine`  
 [out]指標`ULONG32`接收之起始行。  
  
 `pendLine`  
 [out]指標`ULONG32`接收之結尾行。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。  
  
## <a name="requirements"></a>需求  
 **標頭：**於 CorSym.idl、 CorSym.h  
  
## <a name="see-also"></a>另請參閱  
 [ISymENCUnmanagedMethod 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)

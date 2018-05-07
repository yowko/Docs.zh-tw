---
title: ISymENCUnmanagedMethod::GetLineFromOffset 方法
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetLineFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetLineFromOffset
helpviewer_keywords:
- GetLineFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetLineFromOffset method [.NET Framework debugging]
ms.assetid: cc09bad2-fb34-4d13-a521-6ec7b1a1d915
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 29990ad6a94f063577236bdbc84d02d4d2b4b2f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a>ISymENCUnmanagedMethod::GetLineFromOffset 方法
取得相關聯的位移的行資訊。 如果位移的參數 (`dwOffset`) 不是序列點，這個方法會取得相關聯的上一個位移的行資訊。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetLineFromOffset(  
     [in]  ULONG32   dwOffset,  
     [out] ULONG32*  pline,  
     [out] ULONG32*  pcolumn,  
     [out] ULONG32*  pendLine,  
     [out] ULONG32*  pendColumn,  
     [out] ULONG32*  pdwStartOffset);  
```  
  
#### <a name="parameters"></a>參數  
 `dwOffset`  
 [in]A`ULONG32`包含位移。  
  
 `pline`  
 [out]指標`ULONG32`接收之列。  
  
 `pcolumn`  
 [out]指標`ULONG32`接收的資料行。  
  
 `pendLine`  
 [out]指標`ULONG32`接收之結尾行。  
  
 `pendColumn`  
 [out]指標`ULONG32`接收結束資料行。  
  
 `pdwStartOffset`  
 [out]指標`ULONG32`接收相關聯的序列點。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。  
  
## <a name="requirements"></a>需求  
 **標頭：**於 CorSym.idl、 CorSym.h  
  
## <a name="see-also"></a>另請參閱  
 [ISymENCUnmanagedMethod 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)

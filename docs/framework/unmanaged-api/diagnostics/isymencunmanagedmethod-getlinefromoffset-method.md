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
ms.openlocfilehash: 98015af4a79a9fca4945708e6d0baeb61e46876f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54531222"
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a>ISymENCUnmanagedMethod::GetLineFromOffset 方法
取得位移與相關聯的行資訊。 如果位移的參數 (`dwOffset`) 不是序列點，這個方法會取得先前的位移與相關聯的行資訊。  
  
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
 [out]指標`ULONG32`接收端資料行。  
  
 `pdwStartOffset`  
 [out]指標`ULONG32`接收相關聯的序列點。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。  
  
## <a name="requirements"></a>需求  
 **標頭：** 於 CorSym.idl CorSym.h  
  
## <a name="see-also"></a>另請參閱
- [ISymENCUnmanagedMethod 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)

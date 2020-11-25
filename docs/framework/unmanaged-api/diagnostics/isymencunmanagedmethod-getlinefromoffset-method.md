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
ms.openlocfilehash: 196993df9058d3eb8167e0144255c5fe366c54f8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707356"
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a>ISymENCUnmanagedMethod::GetLineFromOffset 方法

取得與位移相關聯的行資訊。 如果 (`dwOffset`) 不是序列點的 offset 參數，這個方法會取得與先前位移相關聯的行資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetLineFromOffset(  
     [in]  ULONG32   dwOffset,  
     [out] ULONG32*  pline,  
     [out] ULONG32*  pcolumn,  
     [out] ULONG32*  pendLine,  
     [out] ULONG32*  pendColumn,  
     [out] ULONG32*  pdwStartOffset);  
```  
  
## <a name="parameters"></a>參數  

 `dwOffset`  
 在 `ULONG32` 包含位移的。  
  
 `pline`  
 擴展接收該行之的指標 `ULONG32` 。  
  
 `pcolumn`  
 擴展接收資料行之的指標 `ULONG32` 。  
  
 `pendLine`  
 擴展 `ULONG32` 接收結束行之的指標。  
  
 `pendColumn`  
 擴展的指標 `ULONG32` ，會接收 end 資料行。  
  
 `pdwStartOffset`  
 擴展的指標 `ULONG32` ，會接收相關聯的序列點。  
  
## <a name="return-value"></a>傳回值  

 如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。  
  
## <a name="requirements"></a>需求  

 **標頭：** CorSym .idl、CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymENCUnmanagedMethod 介面](isymencunmanagedmethod-interface.md)

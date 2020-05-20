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
ms.openlocfilehash: d9a7b18e90a3038c1ffb634ccc7315143875c809
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441912"
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a>ISymENCUnmanagedMethod::GetLineFromOffset 方法
取得與位移相關聯的線條資訊。 如果 offset 參數（ `dwOffset` ）不是序列點，這個方法會取得與上一個位移相關聯的行資訊。  
  
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
 在`ULONG32`包含位移的。  
  
 `pline`  
 脫銷接收行之的指標 `ULONG32` 。  
  
 `pcolumn`  
 脫銷接收資料行之的指標 `ULONG32` 。  
  
 `pendLine`  
 脫銷`ULONG32`接收結束行之的指標。  
  
 `pendColumn`  
 脫銷接收結束資料行之的指標 `ULONG32` 。  
  
 `pdwStartOffset`  
 脫銷`ULONG32`接收相關聯序列點之的指標。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymENCUnmanagedMethod 介面](isymencunmanagedmethod-interface.md)

---
title: ISymUnmanagedENCUpdate::GetLocalVariableCount 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.GetLocalVariableCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount method [.NET Framework debugging]
- GetLocalVariableCount method [.NET Framework debugging]
ms.assetid: 9777d8bb-4abc-4be8-aa7c-34f853eceb9c
topic_type:
- apiref
ms.openlocfilehash: d04c9865d8272bf8d04080f6049ddfb1d4c643bb
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614574"
---
# <a name="isymunmanagedencupdategetlocalvariablecount-method"></a>ISymUnmanagedENCUpdate::GetLocalVariableCount 方法
取得本機變數的數目。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetLocalVariableCount(  
    [in]  mdMethodDef  mdMethodToken,  
    [out] ULONG        *pcLocals);  
```  
  
## <a name="parameters"></a>參數  
 `mdMethodToken`  
 在方法的元資料標記。  
  
 `pcLocals`  
 脫銷的指標， `ULONG32` 接收包含區域變數數目所需的緩衝區大小（以字元為單位）。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedENCUpdate 介面](isymunmanagedencupdate-interface.md)

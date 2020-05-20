---
title: ISymUnmanagedENCUpdate::UpdateMethodLines 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.UpdateMethodLines
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::UpdateMethodLines
helpviewer_keywords:
- UpdateMethodLines method [.NET Framework debugging]
- ISymUnmanagedENCUpdate::UpdateMethodLines method [.NET Framework debugging]
ms.assetid: 275ef87b-0b53-49f9-af6b-58506335dc06
topic_type:
- apiref
ms.openlocfilehash: 9a490299c24f44b59da682f714f4b696fde3cba5
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614509"
---
# <a name="isymunmanagedencupdateupdatemethodlines-method"></a>ISymUnmanagedENCUpdate::UpdateMethodLines 方法
允許更新尚未重新編譯之方法的行資訊，但其行已獨立移動。 允許每個語句的差異。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT UpdateMethodLines(  
    [in]  mdMethodDef  mdMethodToken,  
    [in, size_is(cDeltas)] INT32*  pDeltas,  
    [in]  ULONG        cDeltas);  
```  
  
## <a name="parameters"></a>參數  
 `mdMethodToken`  
 在方法 token 的中繼資料。  
  
 `pDeltas`  
 在`INT32`值的陣列，表示方法中每個序列點的差異。  
  
 `cDeltas`  
 在`ULONG`包含參數大小的 `pDeltas` 。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedENCUpdate 介面](isymunmanagedencupdate-interface.md)

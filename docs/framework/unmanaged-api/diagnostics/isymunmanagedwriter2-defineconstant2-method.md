---
title: ISymUnmanagedWriter2::DefineConstant2 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineConstant2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineConstant2
helpviewer_keywords:
- DefineConstant2 method [.NET Framework debugging]
- ISymUnmanagedWriter2::DefineConstant2 method [.NET Framework debugging]
ms.assetid: dd2bc956-7dbe-49fc-a646-daa0d267f2df
topic_type:
- apiref
ms.openlocfilehash: 70ee853ff657a75dcc4df1454c4354f9d3f8202f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614717"
---
# <a name="isymunmanagedwriter2defineconstant2-method"></a>ISymUnmanagedWriter2::DefineConstant2 方法
定義常數值的名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DefineConstant2(  
    [in] const WCHAR  *name,  
    [in] VARIANT      value,  
    [in] mdSignature  sigToken);  
```  
  
## <a name="parameters"></a>參數  
 `name`  
 在常數名稱。  
  
 `value`  
 在常數的值。  
  
 `sigToken`  
 在常數的元資料標記。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedWriter2 介面](isymunmanagedwriter2-interface.md)
- [DefineConstant 方法](isymunmanagedwriter-defineconstant-method.md)

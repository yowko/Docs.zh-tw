---
title: ISymUnmanagedWriter3::OpenMethod2 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3.OpenMethod2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3::OpenMethod2
helpviewer_keywords:
- ISymUnmanagedWriter3::OpenMethod2 method [.NET Framework debugging]
- OpenMethod2 method [.NET Framework debugging]
ms.assetid: 025e358c-448f-4423-a2f2-57acf437c8a5
topic_type:
- apiref
ms.openlocfilehash: 0c112819ef3bc4f9a7146ee80f55202ff89d689a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178322"
---
# <a name="isymunmanagedwriter3openmethod2-method"></a>ISymUnmanagedWriter3::OpenMethod2 方法
打開方法並在圖像中提供其實際截面偏移。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT OpenMethod2(
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
## <a name="parameters"></a>參數  
 `method`  
 [在]要打開的方法的中繼資料權杖。  
  
 `isect`  
 [在]圖像中的截面偏移。  
  
 `offset`  
 [在]圖像中的偏移量。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，S_OK;否則，E_FAIL或其他錯誤代碼。  
  
## <a name="requirements"></a>需求  
 **標題：** 科西姆.伊德爾，科西姆.h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedWriter3 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
- [OpenMethod 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)

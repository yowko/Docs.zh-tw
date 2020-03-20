---
title: ISymUnmanagedScope2::GetConstants 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2.GetConstants
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2::GetConstants
helpviewer_keywords:
- ISymUnmanagedScope2::GetConstants method [.NET Framework debugging]
- GetConstants method [.NET Framework debugging]
ms.assetid: f241b620-9ec5-42fd-92ef-3b22329db72a
topic_type:
- apiref
ms.openlocfilehash: 45268929b6e9ad6ac6423aa0fa2b7b5022bc9179
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176613"
---
# <a name="isymunmanagedscope2getconstants-method"></a>ISymUnmanagedScope2::GetConstants 方法
獲取在此作用域中定義的本地常量。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetConstants(  
     [in]  ULONG32  cConstants,  
     [out] ULONG32  *pcConstants,  
     [out, size_is(cConstants),  
         length_is(*pcConstants)] ISymUnmanagedConstant*
             constants[]);  
```  
  
## <a name="parameters"></a>參數  
 `cConstants`  
 [在]`pcConstants`參數指向的緩衝區的長度。  
  
 `pcConstants`  
 [出]指向 的指標`ULONG32`，該指標以字元形式接收包含常量所需的緩衝區的大小。  
  
 `constants`  
 [出]存儲常量的緩衝區。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，S_OK;否則，E_FAIL或其他錯誤代碼。  
  
## <a name="requirements"></a>需求  
 **標題：** 科西姆.伊德爾，科西姆.h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedScope2 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)

---
title: ISymUnmanagedWriter::OpenMethod 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenMethod
helpviewer_keywords:
- ISymUnmanagedWriter::OpenMethod method [.NET Framework debugging]
- OpenMethod method [.NET Framework debugging]
ms.assetid: fb90cb7f-af88-45e8-a99f-80a0bbddb08b
topic_type:
- apiref
ms.openlocfilehash: d2d16ab0a29fadd3a64d906a64fc46c422e01c45
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610037"
---
# <a name="isymunmanagedwriteropenmethod-method"></a>ISymUnmanagedWriter::OpenMethod 方法
開啟用來發出符號資訊的方法。 給定的方法會成為呼叫的目前方法，以定義序列點、參數和詞彙範圍。 整個方法周圍有隱含的詞法範圍。 重新開啟先前已關閉的方法，會清除該方法先前定義的任何符號。 一次只能有一個開啟的方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT OpenMethod(  
    [in] mdMethodDef method);  
```  
  
## <a name="parameters"></a>參數  
 `method`  
 在要開啟之方法的元資料標記。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedWriter 介面](isymunmanagedwriter-interface.md)
- [CloseMethod 方法](isymunmanagedwriter-closemethod-method.md)
- [OpenMethod2 方法](isymunmanagedwriter3-openmethod2-method.md)

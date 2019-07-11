---
title: ISymUnmanagedDocument::GetSourceRange 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetSourceRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetSourceRange
helpviewer_keywords:
- ISymUnmanagedDocument::GetSourceRange method [.NET Framework debugging]
- GetSourceRange method [.NET Framework debugging]
ms.assetid: 20fefee7-1040-41ba-93dc-bd42f68b90c2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 981048c10be27900f011afeab55d1c5eb523f734
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776676"
---
# <a name="isymunmanageddocumentgetsourcerange-method"></a>ISymUnmanagedDocument::GetSourceRange 方法
傳回指定的範圍的內嵌來源到指定的緩衝區。 緩衝區必須夠大，無法容納來源。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetSourceRange(  
    [in]  ULONG32  startLine,  
    [in]  ULONG32  startColumn,  
    [in]  ULONG32  endLine,  
    [in]  ULONG32  endColumn,  
    [in]  ULONG32  cSourceBytes,  
    [out] ULONG32  *pcSourceBytes,  
    [out, size_is(cSourceBytes),  
        length_is(*pcSourceBytes)] BYTE source[]);  
```  
  
## <a name="parameters"></a>參數  
 `startLine`  
 [in]目前文件起始行。  
  
 `startColumn`  
 [in]目前的文件中的起始欄。  
  
 `endLine`  
 [in]目前的文件中的最後一行。  
  
 `endColumn`  
 [in]目前的文件中的最後一個資料行。  
  
 `cSourceBytes`  
 [in]來源，以位元組為單位的大小。  
  
 `pcSourceBytes`  
 [out]此變數會接收來源的大小指標。  
  
 `source`  
 [out]大小和來源文件，以位元組為單位的指定範圍的長度。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功為 S_OK。  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedDocument 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)

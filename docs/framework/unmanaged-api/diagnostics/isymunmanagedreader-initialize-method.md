---
title: "ISymUnmanagedReader::Initialize 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.Initialize
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::Initialize
helpviewer_keywords:
- ISymUnmanagedReader::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 8f0dd2fe-7df7-464e-91f4-5518c586bb5f
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 433cd62f7801d386f3b34b7fc8e95bd1d0c5f765
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreaderinitialize-method"></a>ISymUnmanagedReader::Initialize 方法
初始化這個讀取器會與，以及檔案名稱的模組相關聯的中繼資料匯入工具介面的符號讀取器。  
  
> [!NOTE]
>  這個方法可以只一次，而且必須在任何其他的讀取器方法之前呼叫。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
#### <a name="parameters"></a>參數  
 `importer`  
 [in]與這個讀取器將相關聯的中繼資料匯入工具介面。  
  
 `filename`  
 [in]模組檔案名稱。 您可以使用`pIStream`參數改為。  
  
 `searchPath`  
 [in]要搜尋的路徑。 這是選擇性參數。  
  
 `pIStream`  
 [in]檔案資料流，做為檔案名稱參數的替代方案。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。  
  
## <a name="remarks"></a>備註  
 您必須指定的其中之一`filename`或`pIStream`參數不可同時為兩者。 `searchPath` 是選擇性參數。  
  
## <a name="requirements"></a>需求  
 **標頭：**於 CorSym.idl、 CorSym.h  
  
## <a name="see-also"></a>請參閱  
 [ISymUnmanagedReader 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

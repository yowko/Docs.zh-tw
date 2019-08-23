---
title: ISymUnmanagedReader::Initialize 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.Initialize
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::Initialize
helpviewer_keywords:
- ISymUnmanagedReader::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 8f0dd2fe-7df7-464e-91f4-5518c586bb5f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f2dceeb2f0b3aa9f3147157e77087dffbf2d5f85
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939018"
---
# <a name="isymunmanagedreaderinitialize-method"></a>ISymUnmanagedReader::Initialize 方法
使用與此讀取器相關聯的中繼資料匯入介面, 以及模組的檔案名, 初始化符號讀取器。  
  
> [!NOTE]
> 這個方法只能呼叫一次, 而且必須在任何其他讀取器方法之前呼叫。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
## <a name="parameters"></a>參數  
 `importer`  
 在與這個讀取器相關聯的中繼資料匯入工具介面。  
  
 `filename`  
 在模組的檔案名。 您可以`pIStream`改用參數。  
  
 `searchPath`  
 在要搜尋的路徑。 這個參數是選擇性的。  
  
 `pIStream`  
 在檔案資料流程, 用來做為 filename 參數的替代項。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功, 則為 S_OK;否則, E_FAIL 或其他錯誤碼。  
  
## <a name="remarks"></a>備註  
 您只需要指定其中一個`filename` `pIStream`或參數, 而不是兩者。 `searchPath` 是選擇性參數。  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl, CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedReader 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

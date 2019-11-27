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
ms.openlocfilehash: ca34d1d84d6f9960d021c35566f8412df321464d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429745"
---
# <a name="isymunmanagedreaderinitialize-method"></a>ISymUnmanagedReader::Initialize 方法
使用與此讀取器相關聯的中繼資料匯入介面，以及模組的檔案名，初始化符號讀取器。  
  
> [!NOTE]
> 這個方法只能呼叫一次，而且必須在任何其他讀取器方法之前呼叫。  
  
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
 在模組的檔案名。 您可以改用 `pIStream` 參數。  
  
 `searchPath`  
 在要搜尋的路徑。 這個參數是選擇性的。  
  
 `pIStream`  
 在檔案資料流程，用來做為 filename 參數的替代項。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。  
  
## <a name="remarks"></a>備註  
 您只需要指定其中一個 `filename` 或 `pIStream` 參數，而不是兩者。 `searchPath` 是選擇性參數。  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedReader 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

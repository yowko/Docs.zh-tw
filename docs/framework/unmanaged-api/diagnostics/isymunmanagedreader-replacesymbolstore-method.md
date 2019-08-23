---
title: ISymUnmanagedReader::ReplaceSymbolStore 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.ReplaceSymbolStore
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::ReplaceSymbolStore
helpviewer_keywords:
- ReplaceSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::ReplaceSymbolStore method [.NET Framework debugging]
ms.assetid: 43257761-8cb1-4eaf-8fb5-1f3980cb66cd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8721f7c30061fbfd4a761bed090b761762c3c13c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939031"
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a>ISymUnmanagedReader::ReplaceSymbolStore 方法
以差異符號存放區來取代現有的符號存放區。 這個方法類似于[UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)方法, 不同之處在于指定的差異會作為完整取代, 而不是更新。  
  
> [!NOTE]
> 您只需要指定其中一個`filename`或`pIStream`參數, 而不是兩者。 如果`filename`指定了, 符號存放區將會以該檔案中的符號進行更新。 如果`pIStream`指定了, 則會使用<xref:System.Runtime.InteropServices.ComTypes.IStream>中的資料來更新存放區。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ReplaceSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a>參數  
 `filename`  
 在包含符號存放區的檔案名。  
  
 `pIStream`  
 在檔案資料流程, 用來`filename`做為參數的替代方法。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功, 則為 S_OK;否則, E_FAIL 或其他錯誤碼。  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl, CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedReader 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

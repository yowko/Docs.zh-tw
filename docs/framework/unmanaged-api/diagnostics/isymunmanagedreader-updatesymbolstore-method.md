---
title: ISymUnmanagedReader::UpdateSymbolStore 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.UpdateSymbolStore
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::UpdateSymbolStore
helpviewer_keywords:
- UpdateSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::UpdateSymbolStore method [.NET Framework debugging]
ms.assetid: 4a17d723-86b9-4f27-bd0d-b70c3259011c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d84d4fccb2cb4e500f07f6bfbfb93b8c7b81f5d6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938998"
---
# <a name="isymunmanagedreaderupdatesymbolstore-method"></a>ISymUnmanagedReader::UpdateSymbolStore 方法
以差異符號存放區來更新現有的符號存放區。 這個方法是在編輯後繼續案例中使用, 以更新符號存放區, 以符合原始可移植執行檔 (PE) 檔案的差異。  
  
> [!NOTE]
> 您只需要指定其中一個`filename`或`pIStream`參數, 而不是兩者。 如果`filename`指定了, 符號存放區將會以該檔案中的符號進行更新。 如果`pIStream`指定了, 則會使用<xref:System.Runtime.InteropServices.ComTypes.IStream>中的資料來更新存放區。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT UpdateSymbolStore (  
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

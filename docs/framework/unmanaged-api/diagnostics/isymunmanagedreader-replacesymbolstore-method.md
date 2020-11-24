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
ms.openlocfilehash: 3fa94094ad066496cc8a1fc4dd2ccb0ee16b5aac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675837"
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a>ISymUnmanagedReader::ReplaceSymbolStore 方法

以差異符號存放區來取代現有的符號存放區。 這個方法類似于 [UpdateSymbolStore](isymunmanagedreader-updatesymbolstore-method.md) 方法，不同之處在于指定的差異可作為完整的取代，而不是更新。  
  
> [!NOTE]
> 您只需指定其中一個 `filename` 或 `pIStream` 參數，不能同時指定兩者。 如果 `filename` 指定了，則會使用該檔案中的符號來更新符號存放區。 如果 `pIStream` 指定了，則會使用中的資料來更新存放區 <xref:System.Runtime.InteropServices.ComTypes.IStream> 。  
  
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
 在檔案資料流程，用來做為參數的替代項 `filename` 。  
  
## <a name="return-value"></a>傳回值  

 如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。  
  
## <a name="requirements"></a>需求  

 **標頭：** CorSym .idl、CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedReader 介面](isymunmanagedreader-interface.md)

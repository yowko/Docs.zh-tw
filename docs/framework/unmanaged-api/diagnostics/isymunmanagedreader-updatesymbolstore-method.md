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
ms.openlocfilehash: 6670d985eed4c55550b23d3f4110ee20f3b75661
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675824"
---
# <a name="isymunmanagedreaderupdatesymbolstore-method"></a>ISymUnmanagedReader::UpdateSymbolStore 方法

以差異符號存放區來更新現有的符號存放區。 在編輯後繼續案例中，會使用這個方法來更新符號存放區，使其符合原始可攜式可執行檔 (PE) 檔的差異。  
  
> [!NOTE]
> 您只需指定其中一個 `filename` 或 `pIStream` 參數，不能同時指定兩者。 如果 `filename` 指定了，則會使用該檔案中的符號來更新符號存放區。 如果 `pIStream` 指定了，則會使用中的資料來更新存放區 <xref:System.Runtime.InteropServices.ComTypes.IStream> 。  
  
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
 在檔案資料流程，用來做為參數的替代項 `filename` 。  
  
## <a name="return-value"></a>傳回值  

 如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。  
  
## <a name="requirements"></a>需求  

 **標頭：** CorSym .idl、CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedReader 介面](isymunmanagedreader-interface.md)

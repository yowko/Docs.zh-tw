---
title: ImportTypes 方法
ms.date: 03/30/2017
api_name:
- IALink.ImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes
helpviewer_keywords:
- ImportTypes method
ms.assetid: 351d4b4c-c939-486d-9471-51914a55f471
topic_type:
- apiref
ms.openlocfilehash: 762f78900add70238971978ceecda089d0c725ce
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705107"
---
# <a name="importtypes-method"></a>ImportTypes 方法

從透過 [ImportFile 方法](importfile-method.md)匯入的每個範圍起始匯入類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ImportTypes(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
## <a name="parameters"></a>參數  

 `AssemblyID`  
 要匯入之元件的識別碼。  
  
 `FileToken`  
 要匯入之檔案的識別碼。  
  
 `dwScope`  
 要匯入之以零為基底的範圍。  
  
 `phEnum`  
 接收此範圍中類型的枚舉器控制碼。  
  
 `ppImportScope`  
 選擇性地接收 [IMetaDataImport 介面](../metadata/imetadataimport-interface.md) 介面。  
  
 `pdwCountOfTypes`  
 （選擇性）在指定範圍內接收類型的計數。  
  
## <a name="return-value"></a>傳回值  

 如果方法成功，則傳回 S_OK。  
  
## <a name="requirements"></a>需求  

 需要 alink。h  
  
## <a name="see-also"></a>另請參閱

- [IALink 介面](ialink-interface.md)
- [IALink2 介面](ialink2-interface.md)
- [ALink API](index.md)

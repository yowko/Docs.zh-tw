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
ms.openlocfilehash: 76d2b163f959111923bffb1348890f6fbb29828e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445686"
---
# <a name="importtypes-method"></a>ImportTypes 方法
從透過[ImportFile 方法](importfile-method.md)匯入的每個範圍，起始匯入類型。  
  
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
 接收此範圍內之類型的列舉值控制碼。  
  
 `ppImportScope`  
 選擇性地接收[IMetaDataImport 介面](../metadata/imetadataimport-interface.md)介面。  
  
 `pdwCountOfTypes`  
 選擇性地接收指定範圍內的類型計數。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則傳回 S_OK。  
  
## <a name="requirements"></a>需求  
 需要 alink. h  
  
## <a name="see-also"></a>另請參閱

- [IALink 介面](ialink-interface.md)
- [IALink2 介面](ialink2-interface.md)
- [ALink API](index.md)

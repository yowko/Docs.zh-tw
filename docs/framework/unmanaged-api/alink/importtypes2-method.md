---
title: ImportTypes2 方法
ms.date: 03/30/2017
api_name:
- IALink2.ImportTypes2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes2
helpviewer_keywords:
- ImportTypes2 method
ms.assetid: 32f3ba58-9695-41e9-ba58-fd19e45ed396
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ce09eca30e1edb9e1afc02216a07955a5fed4fd2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787263"
---
# <a name="importtypes2-method"></a>ImportTypes2 方法
起始類型的匯入。 呼叫這個方法，以開始從每個透過[ImportFile 方法](importfile-method.md)匯入的範圍匯入類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ImportTypes2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport2** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
## <a name="parameters"></a>參數  
 `AssemblyID`  
 要匯入之元件的識別碼。  
  
 `FileToken`  
 要從中匯入之檔案的識別碼。  
  
 `dwScope`  
 要匯入之以零為基底的範圍。  
  
 `phEnum`  
 接收指定範圍內之類型的列舉值控制碼。  
  
 `ppImportScope`  
 選擇性地接收[IMetaDataImport2 介面](../metadata/imetadataimport2-interface.md)介面。  
  
 `pdwCountOfTypes`  
 選擇性地接收指定範圍內的類型計數。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則傳回 S_OK。  
  
## <a name="requirements"></a>需求  
 需要 alink. h  
  
## <a name="see-also"></a>另請參閱

- [IALink2 介面](ialink2-interface.md)
- [IALink 介面](ialink-interface.md)
- [ALink API](index.md)

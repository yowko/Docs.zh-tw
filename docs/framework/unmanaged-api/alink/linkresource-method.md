---
title: LinkResource 方法
ms.date: 03/30/2017
api_name:
- IALink.LinkResource
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- LinkResource
helpviewer_keywords:
- LinkResource method
ms.assetid: c404acb3-4c59-4100-9a4c-483cbdb1d736
topic_type:
- apiref
ms.openlocfilehash: 9e91d990a8f23335248043c59eb210e8c4155e3a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445626"
---
# <a name="linkresource-method"></a>LinkResource 方法
Links in a resource.  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT LinkResource(  
    mdAssembly  AssemblyID,  
    LPCWSTR     pszFileName,  
    LPCWSTR     pszNewLocation,  
    LPCWSTR     pszResourceName,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a>參數  
 `AssemblyID`  
 ID of the assembly.  
  
 `pszFileName`  
 檔案的名稱。  
  
 `pszNewLocation`  
 Optional new file name. If non-NULL, `pszFileName` will be copied to pszNewLocation.  
  
 `pszResourceName`  
 資源的名稱。  
  
 `dwFlags`  
 Accessibility flags such as `mrPublic` and `mrPrivate`. This parameter may be passed to [DefineManifestResource Method](../metadata/imetadataassemblyemit-definemanifestresource-method.md).  
  
## <a name="return-value"></a>傳回值  
 Returns S_OK if the method succeeds.  
  
## <a name="requirements"></a>需求  
 Requires alink.h.  
  
## <a name="see-also"></a>請參閱

- [IALink 介面](ialink-interface.md)
- [IALink2 介面](ialink2-interface.md)
- [ALink API](index.md)

---
title: EmbedResource 方法
ms.date: 03/30/2017
api_name:
- IALink.EmbedResource
- EmbedResource
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmbedResource
helpviewer_keywords:
- EmbedResource method
ms.assetid: 667bd954-6dc6-4020-a3cb-0e8224179993
topic_type:
- apiref
ms.openlocfilehash: 34439b7c01dee7d7789d989b58e8944c6282b71b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676383"
---
# <a name="embedresource-method"></a>EmbedResource 方法

宣告內嵌資源。 這個方法不會實際內嵌資源。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a>參數  

 `AssemblyID`  
 元件的識別碼。  
  
 `FileToken`  
 包含資源之檔案的檔案 token 或元件識別碼。  
  
 `pszResourceName`  
 資源名稱。  
  
 `dwOffset`  
 從 RVA 開始的資源位移。  
  
 `dwFlags`  
 協助工具旗標 `mrPublic` ，例如和 `mrPrivate` 。 這些旗標可傳遞至 [DefineExportedType 方法](../metadata/imetadataassemblyemit-defineexportedtype-method.md)。  
  
## <a name="return-value"></a>傳回值  

 如果方法成功，則傳回 S_OK。  
  
## <a name="requirements"></a>需求  

 需要 alink. h。  
  
## <a name="see-also"></a>另請參閱

- [IALink 介面](ialink-interface.md)
- [IALink2 介面](ialink2-interface.md)
- [ALink API](index.md)

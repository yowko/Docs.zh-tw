---
title: GetResolutionScope 方法
ms.date: 03/30/2017
api_name:
- IALink.GetResolutionScope
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetResolutionScope
helpviewer_keywords:
- GetResolutionScope method
ms.assetid: 5b48ca60-dacd-44b2-9979-4a5122f00812
topic_type:
- apiref
ms.openlocfilehash: 6318890dd6f0259d8d6a7675380684a129c14c8b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684667"
---
# <a name="getresolutionscope-method"></a>GetResolutionScope 方法

抓取給定型別的範圍。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetResolutionScope(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    mdToken     TargetFile,  
    mdToken*    pScope  
) PURE;  
```  
  
## <a name="parameters"></a>參數  

 `AssemblyID`  
 元件的識別碼。  
  
 `FileToken`  
 需要參考的檔案。  
  
 `TargetFile`  
 在中定義類型之檔案的標記，通常是使用 [ImportFile 方法](importfile-method.md)來取出。  
  
 `pScope`  
 接收元件或模組參考。  
  
## <a name="return-value"></a>傳回值  

 如果方法成功，則傳回 S_OK。  
  
## <a name="requirements"></a>需求  

 需要 alink. h。  
  
## <a name="see-also"></a>另請參閱

- [IALink 介面](ialink-interface.md)
- [IALink2 介面](ialink2-interface.md)
- [ALink API](index.md)

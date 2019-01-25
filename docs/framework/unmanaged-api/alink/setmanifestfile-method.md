---
title: SetManifestFile 方法
ms.date: 03/30/2017
api_name:
- IALink3.SetManifestFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetManifestFile
helpviewer_keywords:
- SetManifestFile method
ms.assetid: 1b33de4c-19cb-4a36-a93f-8675b2a36d58
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a253503f3046c004cc7109a31b5aa8fd8e8dc195
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54618047"
---
# <a name="setmanifestfile-method"></a>SetManifestFile 方法
可讓您指定或重設時它會建立組件連結器所使用之資訊清單檔案。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
#### <a name="parameters"></a>參數  
 `pszFile`  
  
 Win32 資源的 blob 內容會放入資訊清單檔案的名稱。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則會傳回 S_OK。  
  
## <a name="remarks"></a>備註  
 呼叫這個方法之前先詢問 Win32ResBlob。 值`pszFile`參數是其內容會讀取並放入識別碼的 RT_MANIFEST 的 Win32 資源資訊清單檔案的名稱。 當呼叫時使用的參數是 NULL，則會清除任何先前讀取的資訊清單。 這可讓一個連結器的狀態重設為初始設定時。  
  
## <a name="requirements"></a>需求  
 需要 aLink.h  
  
## <a name="see-also"></a>另請參閱
- [IALink3 介面](../../../../docs/framework/unmanaged-api/alink/ialink3-interface.md)
- [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
- [IALink 介面](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [Al.exe (組件連結器)](../../../../docs/framework/tools/al-exe-assembly-linker.md)

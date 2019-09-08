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
ms.openlocfilehash: b293c30060107d18c6b609efc82c4128a73cc1c7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787203"
---
# <a name="setmanifestfile-method"></a>SetManifestFile 方法
可讓您指定或重設連結器在建立元件時所使用的資訊清單檔。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
## <a name="parameters"></a>參數  
 `pszFile`  
  
 資訊清單檔案的名稱，其內容會放入 Win32 資源 blob 中。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則傳回 S_OK。  
  
## <a name="remarks"></a>備註  
 在要求 Win32ResBlob 之前，請先呼叫此程式。 `pszFile`參數的值是資訊清單檔案的名稱，其內容會讀取並放在識別碼為 RT_MANIFEST 的 Win32 資源中。 使用 Null 的參數呼叫時，會清除任何先前讀取的資訊清單。 如此一來，就可以將連結器的狀態重設為初始化時間的狀態。  
  
## <a name="requirements"></a>需求  
 需要 aLink. h  
  
## <a name="see-also"></a>另請參閱

- [IALink3 介面](ialink3-interface.md)
- [ALink API](index.md)
- [IALink 介面](ialink-interface.md)
- [Al.exe (組件連結器)](../../tools/al-exe-assembly-linker.md)

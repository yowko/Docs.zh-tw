---
title: GetWin32ResBlob 方法
ms.date: 03/30/2017
api_name:
- IALink.GetWin32ResBlob
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetWin32ResBlob
helpviewer_keywords:
- GetWin32ResBlob method
ms.assetid: 36997e04-f9f6-4254-a041-6767ac6c51d9
topic_type:
- apiref
ms.openlocfilehash: 03f6c97b4a5bbbdc0aeaf7b3f07277e66d7d0e9a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684508"
---
# <a name="getwin32resblob-method"></a>GetWin32ResBlob 方法

抓取 Win32 資源 blob。 在設定元件選項之後，請呼叫這個方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetWin32ResBlob(  
    mdAssembly    AssemblyID,  
    mdToken       FileToken,  
    BOOL          fDll,  
    LPCWSTR       pszIconFile,  
    const void**  ppResBlob,  
    DWORD*        pcbResBlob  
) PURE;  
```  
  
## <a name="parameters"></a>參數  

 `AssemblyID`  
 元件的識別碼。  
  
 `FileToken`  
 用來抓取在建立 Win32 版本資源時所使用之檔案名的檔案 token  
  
 `fDll`  
 如果 file 是 DLL，則為 TRUE，EXE 則為 false。  
  
 `pszIconFile`  
 要插入至資源 blob 的選擇性圖示。  
  
 `ppResBlob`  
 接收資源 blob。  
  
 `pcbResBlob`  
 接收 blob 的大小。  
  
## <a name="return-value"></a>傳回值  

 如果方法成功，則傳回 S_OK。  
  
## <a name="requirements"></a>需求  

 需要 alink。h  
  
## <a name="see-also"></a>另請參閱

- [IALink 介面](ialink-interface.md)
- [IALink2 介面](ialink2-interface.md)
- [ALink API](index.md)

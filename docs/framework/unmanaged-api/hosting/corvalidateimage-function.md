---
title: _CorValidateImage 函式
ms.date: 03/30/2017
api_name:
- _CorValidateImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorValidateImage
helpviewer_keywords:
- _CorValidateImage function [.NET Framework hosting]
ms.assetid: 0117e080-05f9-4772-885d-e1847230947c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6f1d76ef5cf36bcbab29a33647520663f822798
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770033"
---
# <a name="corvalidateimage-function"></a>_CorValidateImage 函式
驗證 managed 的模組映像，並載入後通知作業系統載入器。  
  
## <a name="syntax"></a>語法  
  
```cpp  
STDAPI _CorValidateImage (   
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
## <a name="parameters"></a>參數  
 `ImageBase`  
 [in]指向要驗證的映像的起始位置的 managed 程式碼。 映像必須已被載入到記憶體中。  
  
 `FileName`  
 [in]映像的檔案名稱。  
  
## <a name="return-value"></a>傳回值  
 此函數會傳回標準值`E_INVALIDARG`， `E_OUTOFMEMORY`， `E_UNEXPECTED`，和`E_FAIL`，以及下列的值。  
  
|傳回值|說明|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|映像無效。 此值沒有 HRESULT 0xC000007BL。|  
|`STATUS_SUCCESS`|影像是有效的。 此值沒有 HRESULT 0x00000000L。|  
  
## <a name="remarks"></a>備註  
 在 Windows XP 和更新版本中，作業系統載入器會檢查 managed 模組藉由檢查 COM 描述元的目錄中的位元的通用物件檔案格式 (COFF) 標頭。 設定位元表示受管理的模組。 如果載入器偵測到受管理的模組，它會載入 MsCorEE.dll，並呼叫`_CorValidateImage`，會執行下列動作：  
  
- 確認映像都是有效的受管理的模組。  
  
- Common language runtime (CLR) 中的進入點變更映像中的進入點。  
  
- 如需 64 位元版本的 Windows，修改的映像從 PE32 格式轉換成 PE32 + 格式是在記憶體中。  
  
- 載入器在載入 managed 的模組映像時傳回。  
  
 針對可執行檔映像，作業系統載入器接著會呼叫[_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)函式，不論在可執行檔中指定的進入點。 DLL 組件映像，則載入器會呼叫[_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)函式。  
  
 `_CorExeMain` 或`_CorDllMain`執行下列動作：  
  
- 初始化 CLR。  
  
- 找出組件的 CLR 標頭的 managed 的進入點。  
  
- 開始執行。  
  
 載入器呼叫[_CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md)函式時受管理模組映像，就會卸載。 不過，此函式不會執行任何動作;它只會傳回。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料全域靜態函式](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)

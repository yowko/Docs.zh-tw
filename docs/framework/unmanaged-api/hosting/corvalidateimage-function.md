---
title: "_CorValidateImage 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _CorValidateImage
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: _CorValidateImage
helpviewer_keywords: _CorValidateImage function [.NET Framework hosting]
ms.assetid: 0117e080-05f9-4772-885d-e1847230947c
topic_type: apiref
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 03deb62a84a1e9c6cee898fe0023c34b8c538ece
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="corvalidateimage-function"></a>_CorValidateImage 函式
驗證 managed 的模組映像，並已經載入後，通知作業系統載入器。  
  
## <a name="syntax"></a>語法  
  
```  
STDAPI _CorValidateImage (   
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ImageBase`  
 [in]要驗證之影像的起始位置的指標 managed 程式碼。 映像已經必須載入記憶體。  
  
 `FileName`  
 [in]影像的檔案名稱。  
  
## <a name="return-value"></a>傳回值  
 此函式傳回的標準值`E_INVALIDARG`， `E_OUTOFMEMORY`， `E_UNEXPECTED`，和`E_FAIL`，以及下列值。  
  
|傳回值|描述|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|映像無效。 此值沒有 HRESULT 0xC000007BL。|  
|`STATUS_SUCCESS`|影像是有效的。 此值沒有 HRESULT 0x00000000L。|  
  
## <a name="remarks"></a>備註  
 在 Windows XP 和更新版本中，作業系統載入器會檢查 managed 模組藉由檢查 COM 描述元的目錄中的位元的通用物件檔案格式 (COFF) 標頭。 設定位元表示受管理的模組。 如果載入器偵測到受管理的模組，它會載入 MsCorEE.dll 呼叫`_CorValidateImage`，它會執行下列動作：  
  
-   確認影像為有效的受管理的模組。  
  
-   Common language runtime (CLR) 中的進入點變更映像中的進入點。  
  
-   對於 64 位元版本的 Windows，修改的映像從 PE32 將其轉換為 PE32 + 格式是在記憶體中。  
  
-   載入器載入 managed 的模組映像時傳回。  
  
 針對可執行檔映像，作業系統載入器接著呼叫[_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)函式，不論在可執行檔中指定的進入點。 載入器會呼叫 DLL 的組件映像， [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)函式。  
  
 `_CorExeMain`或`_CorDllMain`執行下列動作：  
  
-   初始化 CLR。  
  
-   找出組件的 CLR 標頭的 managed 的進入點。  
  
-   開始執行。  
  
 載入器呼叫[_CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md)函式時 managed 模組映像會卸載。 不過，此函式不會執行任何動作;它只會傳回。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [中繼資料全域靜態函式](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)

---
title: _CorDllMain 函式
ms.date: 03/30/2017
api_name:
- _CorDllMain
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorDllMain
helpviewer_keywords:
- _CorDllMain function [.NET Framework hosting]
ms.assetid: bc7b51cf-39d3-48ec-a5cb-2f179fbefff8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5d541f834e829305fa2b091c45d0dc8f387bb55
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431665"
---
# <a name="cordllmain-function"></a>_CorDllMain 函式
初始化 common language runtime (CLR)、 找出 managed 的進入點 DLL 組件的 CLR 標頭，並開始執行。  
  
## <a name="syntax"></a>語法  
  
```  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
#### <a name="parameters"></a>參數  
 `hInst`  
 [in]載入模組的執行個體控制代碼。  
  
 `dwReason`  
 [in]指出為什麼稱為 DLL 進入點函式。 這個參數可以是下列值之一： DLL_PROCESS_ATTACH、 DLL_THREAD_ATTACH、 DLL_THREAD_ATTACH 或 DLL_PROCESS_DETACH。 如需這些值的描述，請參閱`DllMain`Platform SDK 中的文件。  
  
 `lpReserved`  
 [in]未使用。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回`true`成功和`false`如果發生錯誤。  
  
## <a name="remarks"></a>備註  
 作業系統載入器會呼叫此函數的 DLL 的組件。 可執行的組件，載入器會呼叫[_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)函式。  
  
 作業系統載入器會呼叫這個方法，不論 DLL 檔案中指定的進入點。  
  
 在 Windows 98、 Windows ME、 Windows NT 和 Windows 2000`_CorDllMain`函式間接透過呼叫 fixupin 作業系統載入器。 在所有其他 Windows 版本，它會呼叫直接由作業系統載入器。  
  
 如需詳細資訊，請參閱中的 < 備註 > 一節[_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md)主題。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：** 包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [中繼資料全域靜態函式](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)

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
ms.openlocfilehash: 3b2322f708afed08172f87e843c225aa9c60d9d3
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616602"
---
# <a name="_cordllmain-function"></a>\_CorDllMain 函式

初始化 common language runtime （CLR），尋找 DLL 元件的 CLR 標頭中的 managed 進入點，然後開始執行。  
  
## <a name="syntax"></a>語法  
  
```cpp  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
## <a name="parameters"></a>參數  
 `hInst`  
 在已載入模組的實例控制碼。  
  
 `dwReason`  
 在指出呼叫 DLL 進入點函式的原因。 這個參數可以是下列其中一個值： DLL \_ PROCESS_ATTACH、dll \_ 執行緒 \_ 附加、dll \_ 執行緒 \_ 附加或 dll 進程卸 \_ \_ 離。 如需這些值的說明，請參閱 `DllMain` PLATFORM SDK 中的檔。  
  
 `lpReserved`  
 在未使用.  
  
## <a name="return-value"></a>傳回值  
 這個方法 `true` 會針對成功傳回，而且 `false` 如果發生錯誤，則會傳回。  
  
## <a name="remarks"></a>備註  
 DLL 元件的作業系統載入器會呼叫這個函式。 對於可執行檔元件，載入器會改為呼叫[ \_ CorExeMain](corexemain-function.md)函式。  
  
 無論 DLL 檔案中指定的進入點為何，作業系統載入器都會呼叫這個方法。  
  
函式 `_CorDllMain` 是由作業系統載入器直接呼叫。
  
 如需詳細資訊，請參閱[ \_ CorValidateImage](corvalidateimage-function.md)主題中的「備註」一節。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料全域靜態函式](../metadata/metadata-global-static-functions.md)

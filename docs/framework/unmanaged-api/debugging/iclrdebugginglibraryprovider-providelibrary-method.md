---
title: ICLRDebuggingLibraryProvider::ProvideLibrary 方法
ms.date: 03/30/2017
api_name:
- ICLRDebuggingLibraryProvider.ProvideLibrary Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebuggingLibraryProvider::ProvideLibrary
helpviewer_keywords:
- ProvideLibrary method [.NET Framework debugging]
- ICLRDebuggingLibraryProvider::ProvideLibrary method [.NET Framework debugging]
ms.assetid: 86f06245-9517-49be-8d8c-ca5deaf34c02
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a1b02bb74a61e64a3ed9875fcf88e018de9f6317
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041434"
---
# <a name="iclrdebugginglibraryproviderprovidelibrary-method"></a>ICLRDebuggingLibraryProvider::ProvideLibrary 方法

取得程式庫提供者回呼介面, 允許視需要尋找並載入 common language runtime (CLR) 版本特定的偵錯工具程式庫。

## <a name="syntax"></a>語法

```cpp
HRESULT ProvideLibrary(
     [in] const WCHAR* pwszFileName,
     [in] DWORD dwTimestamp,
     [in] DWORD dwSizeOfImage,
     [out] HMODULE* hModule);
```

## <a name="parameters"></a>參數

`pwszFilename` \
在所要求的模組名稱。

`dwTimestamp` \
在儲存在 PE 檔案之 COFF 檔案標頭中的日期時間戳記。

`pLibraryProvider` \
在儲存在 PE 檔案之 COFF 選擇性檔案標頭中的欄位。`SizeOfImage`

`hModule` \
脫銷要求之模組的控制碼。

## <a name="return-value"></a>傳回值

這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。

|HRESULT|描述|
|-------------|-----------------|
|S_OK|已成功完成命令。|

## <a name="exceptions"></a>例外狀況

## <a name="remarks"></a>備註

`ProvideLibrary`可讓偵錯工具提供用來偵測特定 CLR 檔案 (例如 mscordbi.dll 和 mscordacwks) 所需的模組。 模組控制碼必須保持有效, 直到呼叫[ICLRDebugging:: CanUnloadNow](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md)方法指出它們可能被釋放為止, 此時呼叫端會負責釋放控制碼。

偵錯工具可能會使用任何可用的方法來尋找或購買偵錯工具模組。

> [!IMPORTANT]
> 這項功能可讓 API 呼叫端提供包含可執行檔的模組, 以及可能的惡意程式碼。 做為安全性預防措施, 呼叫端不應該`ProvideLibrary`使用來散發不願意自行執行的任何程式碼。
>
> 如果在已發行的程式庫 (例如 mscordbi.dll 或 mscordacwks) 中發現嚴重的安全性問題, 則可以修補填充碼來辨識檔案的錯誤版本。 填充碼接著可以發出已修補之檔案版本的要求, 並在回應任何要求時, 拒絕不正確的版本。 只有在使用者已修補新版本的填充碼時, 才會發生這種情況。 未修補的版本將會保持易受攻擊。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。

**標頭：** CorDebug.idl、CorDebug.h

**LIBRARY:** CorGuids.lib

**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]

## <a name="see-also"></a>另請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)

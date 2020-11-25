---
title: ICLRMetaHost 介面
ms.date: 03/30/2017
api_name:
- ICLRMetaHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost
helpviewer_keywords:
- ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: c627fcdd-fc4f-4b1c-8e91-df8536f627d8
topic_type:
- apiref
ms.openlocfilehash: 75c8d550e572795a291f4639f9f28bd5214ff188
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714012"
---
# <a name="iclrmetahost-interface"></a>ICLRMetaHost 介面

提供方法，這些方法會根據其版本號碼傳回特定版本的 common language runtime (CLR) 、列出所有已安裝的 Clr、列出在指定進程中載入的所有執行時間、探索用來編譯元件的 CLR 版本、找出用來編譯元件的 CLR 版本、結束具有正常執行時間關機的進程，以及查詢舊版 API 系結。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[EnumerateInstalledRuntimes 方法](iclrmetahost-enumerateinstalledruntimes-method.md)|傳回列舉，其中包含電腦上所安裝之每個 CLR 版本的有效 [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 介面指標。|  
|[EnumerateLoadedRuntimes 方法](iclrmetahost-enumerateloadedruntimes-method.md)|傳回列舉，其中包含在給定進程中載入的每個 CLR 的有效 [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 介面指標。 這個方法會取代 [GetVersionFromProcess](getversionfromprocess-function.md)。|  
|[ExitProcess 方法](iclrmetahost-exitprocess-method.md)|嘗試正常關閉所有載入的執行時間，然後終止進程。 取代 [CorExitProcess](corexitprocess-function.md) 函數。|  
|[GetRuntime 方法](iclrmetahost-getruntime-method.md)|取得對應至特定 CLR 版本的 [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 介面。 這個方法會取代搭配[STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md)旗標使用的[CorBindToRuntimeEx](corbindtoruntimeex-function.md)函數。|  
|[GetVersionFromFile 方法](iclrmetahost-getversionfromfile-method.md)|取得元件的原始 .NET Framework 編譯版本 (儲存在中繼資料) 中（指定其檔案路徑）。 這個方法會取代 [GetFileVersion](getfileversion-function.md)。|  
|[QueryLegacyV2RuntimeBinding 方法](iclrmetahost-querylegacyv2runtimebinding-method.md)|傳回介面，這個介面表示舊版啟用原則已系結的執行時間，例如，藉由使用 `useLegacyV2RuntimeActivationPolicy` 專案設定檔[ \<startup> ](../../configure-apps/file-schema/startup/startup-element.md)案專案上的屬性、直接使用舊版啟用 api，或藉由呼叫[ICLRRuntimeInfo：： BindAsLegacyV2Runtime](iclrruntimeinfo-bindaslegacyv2runtime-method.md)方法。|  
|[RequestRuntimeLoadedNotification 方法](iclrmetahost-requestruntimeloadednotification-method.md)|當 CLR 版本第一次載入但尚未啟動時，保證指定函式指標的回呼。 這個方法會取代 [LockClrVersion](lockclrversion-function.md)|  
  
## <a name="remarks"></a>備註  

 取得這個介面實例的唯一方法，就是呼叫 [CLRCreateInstance](clrcreateinstance-function.md) 函式，如下所示：  
  
```cpp  
ICLRMetaHost *pMetaHost = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHost,  
                   IID_ICLRMetaHost, (LPVOID*)&pMetaHost);  
```  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載介面](hosting-interfaces.md)
- [裝載](index.md)

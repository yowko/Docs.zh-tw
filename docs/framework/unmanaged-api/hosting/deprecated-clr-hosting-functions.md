---
title: 已被取代的 CLR 裝載函式
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 1.1, hosting global static functions
- global static functions [.NET Framework hosting], version 2.0
- .NET Framework 2.0, hosting global static functions
- hosting global static functions [.NET Framework], version 2.0
ms.assetid: 91fbbb35-e543-4814-b806-371cebae8c5a
ms.openlocfilehash: 62773ce526b1f21c57ab85a106708589fcf92f6f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138264"
---
# <a name="deprecated-clr-hosting-functions"></a>已被取代的 CLR 裝載函式
本節說明舊版裝載 API 所使用的非受控全域靜態函式。  
  
 除了僅供 .NET Framework 使用的基礎結構函數（`_Cor*` 函式）之外，這些函式在 .NET Framework 4 中已被取代。  
  
## <a name="activation-functions"></a>啟用函式  
 [ClrCreateManagedInstance 函式](../../../../docs/framework/unmanaged-api/hosting/clrcreatemanagedinstance-function.md)  
 已取代。 建立指定之 managed 類型的實例。  
  
 [CoInitializeCor 函式](../../../../docs/framework/unmanaged-api/hosting/coinitializecor-function.md)  
 已過時。 若要初始化 common language runtime （CLR），請使用[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)或[CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)。  
  
 [CoInitializeEE 函式](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)  
 已取代。 確保 CLR 執行引擎已載入進程中。 請改用[ICLRRuntimeHost：： Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)方法。  
  
 [CorBindToCurrentRuntime 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 已取代。 使用儲存在 XML 檔案中的版本資訊，將 common language runtime （CLR）載入進程中。  
  
 [CorBindToRuntime 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 已取代。 可讓非受控主機將 CLR 載入進程中。  
  
 [CorBindToRuntimeByCfg 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 已取代。 使用從 XML 檔案讀取的版本資訊，將 CLR 載入進程中。  
  
 [CorBindToRuntimeEx 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 已取代。 可讓非受控主機將 CLR 載入進程，並可讓您設定旗標來指定 CLR 的行為。  
  
 [CorBindToRuntimeHost 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 已取代。 讓主機能夠將指定的 CLR 版本載入進程中。  
  
 [GetCORRequiredVersion 函式](../../../../docs/framework/unmanaged-api/hosting/getcorrequiredversion-function.md)  
 已取代。 取得所需的 CLR 版本號碼。  
  
 [GetCORSystemDirectory 函式](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md)  
 已取代。 傳回載入進程之 CLR 的安裝目錄。  
  
 [GetRealProcAddress 函式](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md)  
 已取代。 取得從 CLR 的最新已安裝版本匯出之指定函式的位址。  
  
 [GetRequestedRuntimeInfo 函式](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 已取代。 取得應用程式所要求之 CLR 的版本和目錄資訊。  
  
## <a name="clr-version-functions"></a>CLR 版本函數  
 本節中的函式會傳回 CLR 版本;它們不會啟動 CLR。  
  
 [GetCORVersion 函式](../../../../docs/framework/unmanaged-api/hosting/getcorversion-function.md)  
 已取代。 傳回目前進程中正在執行之 CLR 的版本號碼。  
  
 [GetFileVersion 函式](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md)  
 已取代。 使用指定的緩衝區，取得指定檔案的 CLR 版本資訊。  
  
 [GetRequestedRuntimeVersion 函式](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 已取代。 取得指定的應用程式所要求之 CLR 的版本號碼。 如果未安裝該版本，會取得所要求版本之前所安裝的最新版本。  
  
 [GetRequestedRuntimeVersionForCLSID 函式](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversionforclsid-function.md)  
 已取代。 使用指定的 CLSID，取得類別的適當 CLR 版本資訊。  
  
 [GetVersionFromProcess 函式](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 已取代。 取得與指定的進程控制碼相關聯之 CLR 的版本號碼。  
  
 [LockClrVersion 函式](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)  
 已取代。 允許主機判斷在明確初始化 CLR 之前，將在進程中使用的 CLR 版本。  
  
## <a name="hosting-functions"></a>裝載函數  
 [CallFunctionShim 函式](../../../../docs/framework/unmanaged-api/hosting/callfunctionshim-function.md)  
 已取代。 呼叫在指定的程式庫中具有指定名稱和參數的函式。  
  
 [CoEEShutDownCOM 函式](../../../../docs/framework/unmanaged-api/hosting/coeeshutdowncom-function.md)  
 已取代。 從進程中卸載 COM 元件。  
  
 [CorExitProcess 函式](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md)  
 已取代。 關閉目前的非受控進程。  
  
 [CorLaunchApplication 函式](../../../../docs/framework/unmanaged-api/hosting/corlaunchapplication-function.md)  
 已取代。 使用指定的資訊清單和其他應用程式資料，在指定的網路路徑啟動應用程式。  
  
 [CorMarkThreadInThreadPool 函式](../../../../docs/framework/unmanaged-api/hosting/cormarkthreadinthreadpool-function.md)  
 已取代。 標示目前執行中的執行緒集區執行緒，以執行 managed 程式碼。 從 .NET Framework 版本2.0 開始，此函式不會有任何作用。 這不是必要的，而且可以從程式碼中移除。  
  
 [CoUninitializeCor 函式](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md)  
 已過時。 CLR 無法從進程中卸載。  
  
 [CoUninitializeEE 函式](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md)  
 已過時。  
  
 [CreateDebuggingInterfaceFromVersion 函式](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md)  
 已取代。 根據指定的版本資訊建立[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)物件。  
  
 [CreateICeeFileGen 函式](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md)  
 已取代。 建立[ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md)物件。  
  
 [DestroyICeeFileGen 函式](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md)  
 已取代。 終結[ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md)物件。  
  
 [FExecuteInAppDomainCallback 函式指標](../../../../docs/framework/unmanaged-api/hosting/fexecuteinappdomaincallback-function-pointer.md)  
 已取代。 指向 CLR 所呼叫的函式，以執行 managed 程式碼。  
  
 [FLockClrVersionCallback 函式指標](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md)  
 已取代。 指向 CLR 呼叫的函式，以通知主機初始化已啟動或已完成。  
  
 [GetCLRIdentityManager 函式](../../../../docs/framework/unmanaged-api/hosting/getclridentitymanager-function.md)  
 已取代。 取得介面的指標，允許 CLR 管理身分識別。  
  
 [LoadLibraryShim 函式](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md)  
 已取代。 載入指定的 .NET Framework DLL 版本。  
  
 [LoadStringRC 函式](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
 已取代。 使用目前線程的預設文化特性，將 HRESULT 值轉譯為錯誤訊息。  
  
 [LoadStringRCEx 函式](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
 已取代。 針對指定的文化特性，將 HRESULT 值轉譯為適當的錯誤訊息。  
  
 [LPOVERLAPPED_COMPLETION_ROUTINE 函式指標](../../../../docs/framework/unmanaged-api/hosting/lpoverlapped-completion-routine-function-pointer.md)  
 已取代。 指向函式，當裝置的重迭（也就是非同步） i/o 完成時，會通知主機。  
  
 [LPTHREAD_START_ROUTINE 函式指標](../../../../docs/framework/unmanaged-api/hosting/lpthread-start-routine-function-pointer.md)  
 已取代。 指向函式，該函式會通知主機執行緒已開始執行。  
  
 [RunDll32ShimW 函式](../../../../docs/framework/unmanaged-api/hosting/rundll32shimw-function.md)  
 已取代。 執行指定命令。  
  
 [WAITORTIMERCALLBACK 函式指標](../../../../docs/framework/unmanaged-api/hosting/waitortimercallback-function-pointer.md)  
 已取代。 指向函式，該函式會通知主機等候控制碼已發出信號或已超時。  
  
## <a name="infrastructure-functions"></a>基礎結構函式  
 本節中的函數僅供 .NET Framework 使用。  
  
 [_CorDllMain 函式](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)  
 初始化 CLR，尋找 DLL 元件的 CLR 標頭中的 managed 進入點，並開始執行。  
  
 [_CorExeMain 函式](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)  
 初始化 CLR，尋找可執行元件的 CLR 標頭中的 managed 進入點，並開始執行。  
  
 [_CorExeMain2 函式](../../../../docs/framework/unmanaged-api/hosting/corexemain2-function.md)  
 執行指定的記憶體對應程式碼中的進入點。 此函式是由作業系統載入器所呼叫。  
  
 [_CorImageUnloading 函式](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md)  
 卸載受管理的模組映射時，通知載入器。  
  
 [_CorValidateImage 函式](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md)  
 驗證受管理的模組映射，並在載入作業系統載入器之後通知它。  
  
## <a name="see-also"></a>請參閱

- [.NET Framework 4 裝載全域靜態函式](../../../../docs/framework/unmanaged-api/hosting/net-framework-4-hosting-global-static-functions.md)

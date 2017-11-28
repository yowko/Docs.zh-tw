---
title: "已被取代的 CLR 裝載函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- .NET Framework 1.1, hosting global static functions
- global static functions [.NET Framework hosting], version 2.0
- .NET Framework 2.0, hosting global static functions
- hosting global static functions [.NET Framework], version 2.0
ms.assetid: 91fbbb35-e543-4814-b806-371cebae8c5a
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9530fecb4f2ca6f59d165e49c282320966fd2fa8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="deprecated-clr-hosting-functions"></a>已被取代的 CLR 裝載函式
本章節描述的 unmanaged 全域靜態函式使用舊版的裝載 API。  
  
 基礎結構功能除外 (`_Cor*`函式)，這僅供.NET Framework 中，這些函式已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。  
  
## <a name="activation-functions"></a>啟用函式  
 [ClrCreateManagedInstance 函式](../../../../docs/framework/unmanaged-api/hosting/clrcreatemanagedinstance-function.md)  
 已取代。 建立指定的 managed 型別的執行個體。  
  
 [CoInitializeCor 函式](../../../../docs/framework/unmanaged-api/hosting/coinitializecor-function.md)  
 已過時。 若要初始化 common language runtime (CLR)，請使用[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)或[CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)。  
  
 [CoInitializeEE 函式](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)  
 已取代。 確保 CLR 執行引擎載入處理序。 使用[iclrruntimehost:: Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)方法改為。  
  
 [CorBindToCurrentRuntime 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 已取代。 載入處理序的 common language runtime (CLR) 使用 XML 檔案中儲存的版本資訊。  
  
 [CorBindToRuntime 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 已取代。 可讓 unmanaged 的主機將 CLR 載入處理序。  
  
 [CorBindToRuntimeByCfg 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 已取代。 載入處理序的 CLR 使用會從 XML 檔案讀取的版本資訊。  
  
 [CorBindToRuntimeEx 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 已取代。 可讓 unmanaged 的主機將 CLR 載入處理序，並可讓您設定旗標來指定 CLR 的行為。  
  
 [CorBindToRuntimeHost 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 已取代。 可讓主機處理程序中載入指定的 clr 版本。  
  
 [GetCORRequiredVersion 函式](../../../../docs/framework/unmanaged-api/hosting/getcorrequiredversion-function.md)  
 已取代。 取得必要的 CLR 版本號碼。  
  
 [GetCORSystemDirectory 函式](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md)  
 已取代。 傳回 CLR 載入到處理程序的安裝目錄。  
  
 [GetRealProcAddress 函式](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md)  
 已取代。 取得最新安裝的 CLR 版本從匯出的指定函式的位址。  
  
 [GetRequestedRuntimeInfo 函式](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 已取代。 取得有關應用程式所要求的 CLR 版本和目錄資訊。  
  
## <a name="clr-version-functions"></a>CLR 版本函式  
 本節中的函式傳回 CLR 版本;它們沒有啟動 CLR。  
  
 [GetCORVersion 函式](../../../../docs/framework/unmanaged-api/hosting/getcorversion-function.md)  
 已取代。 傳回目前的處理序中執行的 clr 版本編號。  
  
 [GetFileVersion 函式](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md)  
 已取代。 取得指定的檔案，使用指定的緩衝區的 CLR 版本資訊。  
  
 [GetRequestedRuntimeVersion 函式](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 已取代。 取得所指定的應用程式要求的 CLR 的版本號碼。 如果未安裝該版本，取得要求的版本之前安裝的最新版本。  
  
 [GetRequestedRuntimeVersionForCLSID 函式](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversionforclsid-function.md)  
 已取代。 取得具有指定的 CLSID 之類別的適當 CLR 版本資訊。  
  
 [GetVersionFromProcess 函式](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 已取代。 取得與指定的處理序控制代碼相關聯之 CLR 的版本號碼。  
  
 [LockClrVersion 函式](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)  
 已取代。 可讓主機判斷處理序中先明確初始化 CLR 使用的 clr 版本。  
  
## <a name="hosting-functions"></a>裝載函式  
 [CallFunctionShim 函式](../../../../docs/framework/unmanaged-api/hosting/callfunctionshim-function.md)  
 已取代。 會指定程式庫中有指定的名稱和參數的函式呼叫。  
  
 [CoEEShutDownCOM 函式](../../../../docs/framework/unmanaged-api/hosting/coeeshutdowncom-function.md)  
 已取代。 卸載從處理序的 COM 組件。  
  
 [CorExitProcess 函式](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md)  
 已取代。 關閉目前未受管理的程序。  
  
 [CorLaunchApplication 函式](../../../../docs/framework/unmanaged-api/hosting/corlaunchapplication-function.md)  
 已取代。 啟動指定的網路路徑，使用指定的資訊清單和其他應用程式資料在應用程式。  
  
 [CorMarkThreadInThreadPool 函式](../../../../docs/framework/unmanaged-api/hosting/cormarkthreadinthreadpool-function.md)  
 已取代。 標記目前正在執行的執行緒集區執行緒，以便執行 managed 程式碼。 從.NET Framework 2.0 版開始，此函式沒有任何作用。 它不是必要項目，並可以從您的程式碼中移除。  
  
 [CoUninitializeCor 函式](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md)  
 已過時。 CLR 無法從處理序卸載。  
  
 [CoUninitializeEE 函式](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md)  
 已過時。  
  
 [CreateDebuggingInterfaceFromVersion 函式](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md)  
 已取代。 建立[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)物件會根據指定的版本資訊。  
  
 [CreateICeeFileGen 函式](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md)  
 已取代。 建立[ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md)物件。  
  
 [DestroyICeeFileGen 函式](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md)  
 已取代。 終結[ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md)物件。  
  
 [FExecuteInAppDomainCallback 函式指標](../../../../docs/framework/unmanaged-api/hosting/fexecuteinappdomaincallback-function-pointer.md)  
 已取代。 指向以 CLR 執行 managed 程式碼呼叫的函式。  
  
 [FLockClrVersionCallback 函式指標](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md)  
 已取代。 指向 CLR 會呼叫以通知主機的函式初始設定已啟動，或是已完成。  
  
 [GetCLRIdentityManager 函式](../../../../docs/framework/unmanaged-api/hosting/getclridentitymanager-function.md)  
 已取代。 取得可讓管理身分識別 CLR 的介面指標。  
  
 [LoadLibraryShim 函式](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md)  
 已取代。 載入指定的版本的.NET Framework DLL。  
  
 [LoadStringRC 函式](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
 已取代。 使用目前執行緒的預設文化特性，將 HRESULT 值轉譯成錯誤訊息。  
  
 [LoadStringRCEx 函式](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
 已取代。 HRESULT 值轉譯成適當的錯誤訊息指定的文化特性。  
  
 [LPOVERLAPPED_COMPLETION_ROUTINE 函式指標](../../../../docs/framework/unmanaged-api/hosting/lpoverlapped-completion-routine-function-pointer.md)  
 已取代。 指向某個函式以通知主機重疊時 (也就是非同步) 至裝置的 I/O 已完成。  
  
 [LPTHREAD_START_ROUTINE 函式指標](../../../../docs/framework/unmanaged-api/hosting/lpthread-start-routine-function-pointer.md)  
 已取代。 指向以通知主機在執行緒已開始執行的函式。  
  
 [RunDll32ShimW 函式](../../../../docs/framework/unmanaged-api/hosting/rundll32shimw-function.md)  
 已取代。 執行指定命令。  
  
 [WAITORTIMERCALLBACK 函式指標](../../../../docs/framework/unmanaged-api/hosting/waitortimercallback-function-pointer.md)  
 已取代。 指向以通知主機，等候控制代碼已收到信號或逾時的函式。  
  
## <a name="infrastructure-functions"></a>基礎結構函式  
 本節中的函式是.NET Framework 所使用。  
  
 [_CorDllMain 函式](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)  
 初始化 CLR 中，找出 managed 的進入點 DLL 組件的 CLR 標頭，並開始執行。  
  
 [_CorExeMain 函式](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)  
 初始化 CLR 中，找出 managed 的進入點中可執行組件的 CLR 標頭，並開始執行。  
  
 [_CorExeMain2 函式](../../../../docs/framework/unmanaged-api/hosting/corexemain2-function.md)  
 指定記憶體對應程式碼中執行的進入點。 作業系統載入器會呼叫此函式。  
  
 [_CorImageUnloading 函式](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md)  
 卸載 managed 的模組映像時，請通知載入器。  
  
 [_CorValidateImage 函式](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md)  
 驗證 managed 的模組映像，並已經載入後，通知作業系統載入器。  
  
## <a name="see-also"></a>另請參閱  
 [.NET framework 4 裝載全域靜態函式](../../../../docs/framework/unmanaged-api/hosting/net-framework-4-hosting-global-static-functions.md) 

---
title: 已被取代的 CLR 裝載函式
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 1.1, hosting global static functions
- global static functions [.NET Framework hosting], version 2.0
- .NET Framework 2.0, hosting global static functions
- hosting global static functions [.NET Framework], version 2.0
ms.assetid: 91fbbb35-e543-4814-b806-371cebae8c5a
ms.openlocfilehash: 9e19502672973f292991b72c7ea9b4fdc17f5707
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673120"
---
# <a name="deprecated-clr-hosting-functions"></a>已被取代的 CLR 裝載函式

本節說明舊版裝載 API 所使用的非受控全域靜態函式。  
  
 除了基礎結構函式以外 (函式 `_Cor*`) （僅供 .NET Framework 使用），這些函式在 .NET Framework 4 中已經被取代。  
  
## <a name="activation-functions"></a>啟用函式  

 [ClrCreateManagedInstance 函式](clrcreatemanagedinstance-function.md)  
 已取代。 建立指定之 managed 類型的實例。  
  
 [CoInitializeCor 函式](coinitializecor-function.md)  
 已過時。 若要初始化 common language runtime (CLR) ，請使用 [CorBindToRuntimeEx](corbindtoruntimeex-function.md) 或 [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md)。  
  
 [CoInitializeEE 函式](coinitializeee-function.md)  
 已取代。 確保 CLR 執行引擎已載入至進程。 請改用 [ICLRRuntimeHost：： Start](iclrruntimehost-start-method.md) 方法。  
  
 [CorBindToCurrentRuntime 函式](corbindtocurrentruntime-function.md)  
 已取代。 使用儲存在 XML 檔案中的版本資訊，將 common language runtime (CLR) 載入至進程。  
  
 [CorBindToRuntime 函式](corbindtoruntime-function.md)  
 已取代。 讓非受控主機將 CLR 載入至進程。  
  
 [CorBindToRuntimeByCfg 函式](corbindtoruntimebycfg-function.md)  
 已取代。 使用從 XML 檔案讀取的版本資訊，將 CLR 載入處理常式。  
  
 [CorBindToRuntimeEx 函式](corbindtoruntimeex-function.md)  
 已取代。 可讓非受控主機將 CLR 載入至進程，並可讓您設定旗標來指定 CLR 的行為。  
  
 [CorBindToRuntimeHost 函式](corbindtoruntimehost-function.md)  
 已取代。 讓主機將指定的 CLR 版本載入至進程。  
  
 [GetCORRequiredVersion 函式](getcorrequiredversion-function.md)  
 已取代。 取得所需的 CLR 版本號碼。  
  
 [GetCORSystemDirectory 函式](getcorsystemdirectory-function.md)  
 已取代。 傳回載入至進程的 CLR 安裝目錄。  
  
 [GetRealProcAddress 函式](getrealprocaddress-function.md)  
 已取代。 取得從最新安裝的 CLR 版本匯出的指定函式位址。  
  
 [GetRequestedRuntimeInfo 函式](getrequestedruntimeinfo-function.md)  
 已取代。 取得應用程式所要求之 CLR 的版本和目錄資訊。  
  
## <a name="clr-version-functions"></a>CLR 版本函數  

 本節中的函式會傳回 CLR 版本;它們不會啟用 CLR。  
  
 [GetCORVersion 函式](getcorversion-function.md)  
 已取代。 傳回目前進程中正在執行之 CLR 的版本號碼。  
  
 [GetFileVersion 函式](getfileversion-function.md)  
 已取代。 使用指定的緩衝區，取得指定之檔案的 CLR 版本資訊。  
  
 [GetRequestedRuntimeVersion 函式](getrequestedruntimeversion-function.md)  
 已取代。 取得指定之應用程式所要求之 CLR 的版本號碼。 如果未安裝該版本，則會取得在要求的版本之前安裝的最新版本。  
  
 [GetRequestedRuntimeVersionForCLSID 函式](getrequestedruntimeversionforclsid-function.md)  
 已取代。 取得具有指定 CLSID 之類別的適當 CLR 版本資訊。  
  
 [GetVersionFromProcess 函式](getversionfromprocess-function.md)  
 已取代。 取得與指定之進程控制碼相關聯之 CLR 的版本號碼。  
  
 [LockClrVersion 函式](lockclrversion-function.md)  
 已取代。 允許主機在明確初始化 CLR 之前，判斷要在進程中使用的 CLR 版本。  
  
## <a name="hosting-functions"></a>裝載函數  

 [CallFunctionShim 函式](callfunctionshim-function.md)  
 已取代。 呼叫函式，該函式在指定的程式庫中具有指定的名稱和參數。  
  
 [CoEEShutDownCOM 函式](coeeshutdowncom-function.md)  
 已取代。 卸載進程中的 COM 元件。  
  
 [CorExitProcess 函式](corexitprocess-function.md)  
 已取代。 關閉目前未受管理的進程。  
  
 [CorLaunchApplication 函式](corlaunchapplication-function.md)  
 已取代。 使用指定的資訊清單和其他應用程式資料，在指定的網路路徑上啟動應用程式。  
  
 [CorMarkThreadInThreadPool 函式](cormarkthreadinthreadpool-function.md)  
 已取代。 標示目前執行中的執行緒集區執行緒，以執行 managed 程式碼。 從 .NET Framework 版本2.0 開始，此函數沒有任何作用。 這並不是必要的，而且可以從程式碼中移除。  
  
 [CoUninitializeCor 函式](couninitializecor-function.md)  
 已過時。 CLR 無法從進程中卸載。  
  
 [CoUninitializeEE 函式](couninitializeee-function.md)  
 已過時。  
  
 [CreateDebuggingInterfaceFromVersion 函式](createdebugginginterfacefromversion-function.md)  
 已取代。 根據指定的版本資訊建立 [ICorDebug](../debugging/icordebug-interface.md) 物件。  
  
 [CreateICeeFileGen 函式](createiceefilegen-function.md)  
 已取代。 建立 [ICeeFileGen](iceefilegen-class.md) 物件。  
  
 [DestroyICeeFileGen 函式](destroyiceefilegen-function.md)  
 已取代。 終結 [ICeeFileGen](iceefilegen-class.md) 物件。  
  
 [FExecuteInAppDomainCallback 函式指標](fexecuteinappdomaincallback-function-pointer.md)  
 已取代。 指向 CLR 呼叫以執行 managed 程式碼的函式。  
  
 [FLockClrVersionCallback 函式指標](flockclrversioncallback-function-pointer.md)  
 已取代。 指向 CLR 呼叫的函式，以通知主機初始化已啟動或已完成。  
  
 [GetCLRIdentityManager 函式](getclridentitymanager-function.md)  
 已取代。 取得介面的指標，該介面可讓 CLR 管理身分識別。  
  
 [LoadLibraryShim 函式](loadlibraryshim-function.md)  
 已取代。 載入指定的 .NET Framework DLL 版本。  
  
 [LoadStringRC 函式](loadstringrc-function.md)  
 已取代。 使用目前線程的預設文化特性，將 HRESULT 值轉譯為錯誤訊息。  
  
 [LoadStringRCEx 函式](loadstringrcex-function.md)  
 已取代。 針對指定的文化特性，將 HRESULT 值轉譯為適當的錯誤訊息。  
  
 [LPOVERLAPPED_COMPLETION_ROUTINE 函式指標](lpoverlapped-completion-routine-function-pointer.md)  
 已取代。 指向函式，此函式會在重迭 (（也就是對裝置的非同步) i/o 完成）時通知主機。  
  
 [LPTHREAD_START_ROUTINE 函式指標](lpthread-start-routine-function-pointer.md)  
 已取代。 指向函式，該函式會通知主機執行緒已開始執行。  
  
 [RunDll32ShimW 函式](rundll32shimw-function.md)  
 已取代。 執行指定命令。  
  
 [WAITORTIMERCALLBACK 函式指標](waitortimercallback-function-pointer.md)  
 已取代。 指向函式，該函式會通知主機等候控制碼已發出信號或已超時。  
  
## <a name="infrastructure-functions"></a>基礎結構函式  

 本節中的函數僅供 .NET Framework 使用。  
  
 [_CorDllMain 函式](cordllmain-function.md)  
 初始化 CLR、找出 DLL 元件的 CLR 標頭中的 managed 進入點，然後開始執行。  
  
 [_CorExeMain 函式](corexemain-function.md)  
 初始化 CLR、找出可執行元件的 CLR 標頭中的 managed 進入點，然後開始執行。  
  
 [_CorExeMain2 函式](corexemain2-function.md)  
 執行指定之記憶體對應程式碼中的進入點。 作業系統載入器會呼叫這個函式。  
  
 [_CorImageUnloading 函式](corimageunloading-function.md)  
 卸載受控模組映射時，通知載入器。  
  
 [_CorValidateImage 函式](corvalidateimage-function.md)  
 驗證受管理的模組映射，並在載入作業系統載入器之後通知作業系統載入器。  
  
## <a name="see-also"></a>另請參閱

- [裝載全域靜態函式的 .NET Framework 4](net-framework-4-hosting-global-static-functions.md)

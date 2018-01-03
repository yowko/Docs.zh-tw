---
title: "診斷 Managed 偵錯助理的錯誤"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: EHMDA
helpviewer_keywords:
- run-time error debugging
- managed code, run-time debugging
- resource debugging
- registry, MDAs
- common language runtime, debugging
- MDAs (managed debugging assistants)
- configuration files [.NET Framework], debugging runtime events
- messages, managed debugging assistants
- application configuration files, managed debugging assistants
- debugging [.NET Framework], managed debugging assistants
- environment variables, MDAs
- access violation debugging [.NET Framework]
- diagnostics, managed debugging assistants
- unmanaged code, run-time debugging
- default debug output stream
- memory, debugging
- app.config files, managed debugging assistants
- managed debugging assistants (MDAs)
- debugging [.NET Framework], run-time errors
- trapping events
- runtime, error debugging
- disabling MDAs
- output, managed debugging assistants
- errors [.NET Framework], managed debugging assistants
ms.assetid: 76994ee6-9fa9-4059-b813-26578d24427c
caps.latest.revision: "63"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 12a96068412f05d48b8b006385c66f3efbbf9870
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="diagnosing-errors-with-managed-debugging-assistants"></a>診斷 Managed 偵錯助理的錯誤
Managed 偵錯助理 (MDA) 是偵錯輔助程式，可與通用語言執行平台 (CLR) 合作提供執行階段狀態的相關資訊。 這些助理會產生有關您無法設陷之執行階段事件的告知性訊息。 您可以使用 MDA 來隔離在 Managed 與 Unmanaged 程式碼之間轉換時，所發生之不易發現的應用程式 Bug。 若要啟用或停用所有 MDA，您可以加入機碼至 Windows 登錄，或是設定環境變數。 若要啟用特定 MDA，您可以使用應用程式組態設定。 您可以針對應用程式組態檔中某些個別的 MDA，設定額外的組態設定。 因為在載入執行階段時，會剖析這些組態檔，所以您必須在 Managed 應用程式啟動之前，先啟用 MDA。 您不能為已啟動的應用程式啟用 MDA。  
  
> [!NOTE]
>  當 MDA 啟用時，即使程式碼不是在偵錯工具之下執行，MDA 仍有效。 如果在偵錯工具不存在的情況下，發生 MDA 事件，則會在未處理的例外狀況對話方塊中顯示事件訊息，雖然 MDA 事件並不是未處理的例外狀況。 若要避免此對話方塊，請在程式碼不是在偵錯環境中執行時，移除啟用 MDA 的設定。  
  
> [!NOTE]
>  當程式碼在 Visual Studio 整合式開發環境 (IDE) 中執行時，可以避免因特定 MDA 事件而出現的例外狀況對話方塊。 若要這樣做，請在 [偵錯] 功能表中按一下 [例外狀況]。 (如果 [偵錯] 功能表沒有包含 [例外狀況] 命令，請按一下 [工具] 功能表上的 [自訂] 來新增該命令。)在 [例外狀況] 對話方塊中，展開 [Managed 偵錯助理] 清單，然後針對個別的 MDA，清除 [擲回] 核取方塊。 例如，若要避免 [contextSwitchDeadlock](../../../docs/framework/debug-trace-profile/contextswitchdeadlock-mda.md) 的例外狀況對話方塊，請在 [Managed 偵錯助理] 清單中，清除其名稱旁邊的 [擲回] 核取方塊。 您也可以使用這個對話方塊來啟用 MDA 例外狀況對話方塊的顯示。  
  
 下表列出 .NET Framework 隨附的 MDA。  
  
|||  
|-|-|  
|[asynchronousThreadAbort](../../../docs/framework/debug-trace-profile/asynchronousthreadabort-mda.md)|[bindingFailure](../../../docs/framework/debug-trace-profile/bindingfailure-mda.md)|  
|[callbackOnCollectedDelegate](../../../docs/framework/debug-trace-profile/callbackoncollecteddelegate-mda.md)|[contextSwitchDeadlock](../../../docs/framework/debug-trace-profile/contextswitchdeadlock-mda.md)|  
|[dangerousThreadingAPI](../../../docs/framework/debug-trace-profile/dangerousthreadingapi-mda.md)|[dateTimeInvalidLocalFormat](../../../docs/framework/debug-trace-profile/datetimeinvalidlocalformat-mda.md)|  
|[dirtyCastAndCallOnInterface](../../../docs/framework/debug-trace-profile/dirtycastandcalloninterface-mda.md)|[disconnectedContext](../../../docs/framework/debug-trace-profile/disconnectedcontext-mda.md)|  
|[dllMainReturnsFalse](../../../docs/framework/debug-trace-profile/dllmainreturnsfalse-mda.md)|[exceptionSwallowedOnCallFromCom](../../../docs/framework/debug-trace-profile/exceptionswallowedoncallfromcom-mda.md)|  
|[failedQI](../../../docs/framework/debug-trace-profile/failedqi-mda.md)|[fatalExecutionEngineError](../../../docs/framework/debug-trace-profile/fatalexecutionengineerror-mda.md)|  
|[gcManagedToUnmanaged](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)|[gcUnmanagedToManaged](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)|  
|[illegalPrepareConstrainedRegion](../../../docs/framework/debug-trace-profile/illegalprepareconstrainedregion-mda.md)|[invalidApartmentStateChange](../../../docs/framework/debug-trace-profile/invalidapartmentstatechange-mda.md)|  
|[invalidCERCall](../../../docs/framework/debug-trace-profile/invalidcercall-mda.md)|[invalidFunctionPointerInDelegate](../../../docs/framework/debug-trace-profile/invalidfunctionpointerindelegate-mda.md)|  
|[invalidGCHandleCookie](../../../docs/framework/debug-trace-profile/invalidgchandlecookie-mda.md)|[invalidIUnknown](../../../docs/framework/debug-trace-profile/invalidiunknown-mda.md)|  
|[invalidMemberDeclaration](../../../docs/framework/debug-trace-profile/invalidmemberdeclaration-mda.md)|[invalidOverlappedToPinvoke](../../../docs/framework/debug-trace-profile/invalidoverlappedtopinvoke-mda.md)|  
|[invalidVariant](../../../docs/framework/debug-trace-profile/invalidvariant-mda.md)|[jitCompilationStart](../../../docs/framework/debug-trace-profile/jitcompilationstart-mda.md)|  
|[loaderLock](../../../docs/framework/debug-trace-profile/loaderlock-mda.md)|[loadFromContext](../../../docs/framework/debug-trace-profile/loadfromcontext-mda.md)|  
|[marshalCleanupError](../../../docs/framework/debug-trace-profile/marshalcleanuperror-mda.md)|[marshaling](../../../docs/framework/debug-trace-profile/marshaling-mda.md)|  
|[memberInfoCacheCreation](../../../docs/framework/debug-trace-profile/memberinfocachecreation-mda.md)|[moduloObjectHashcode](../../../docs/framework/debug-trace-profile/moduloobjecthashcode-mda.md)|  
|[nonComVisibleBaseClass](../../../docs/framework/debug-trace-profile/noncomvisiblebaseclass-mda.md)|[notMarshalable](../../../docs/framework/debug-trace-profile/notmarshalable-mda.md)|  
|[openGenericCERCall](../../../docs/framework/debug-trace-profile/opengenericcercall-mda.md)|[overlappedFreeError](../../../docs/framework/debug-trace-profile/overlappedfreeerror-mda.md)|  
|[pInvokeLog](../../../docs/framework/debug-trace-profile/pinvokelog-mda.md)|[pInvokeStackImbalance](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)|  
|[raceOnRCWCleanup](../../../docs/framework/debug-trace-profile/raceonrcwcleanup-mda.md)|[reentrancy](../../../docs/framework/debug-trace-profile/reentrancy-mda.md)|  
|[releaseHandleFailed](../../../docs/framework/debug-trace-profile/releasehandlefailed-mda.md)|[reportAvOnComRelease](../../../docs/framework/debug-trace-profile/reportavoncomrelease-mda.md)|  
|[streamWriterBufferedDataLost](../../../docs/framework/debug-trace-profile/streamwriterbuffereddatalost-mda.md)|[virtualCERCall](../../../docs/framework/debug-trace-profile/virtualcercall-mda.md)|  
  
 根據預設，.NET Framework 會啟用所有 Managed 偵錯工具的 MDA 子集。 您可以按一下 [偵錯] 功能表上的 [例外狀況]，然後展開 [Managed 偵錯助理] 清單，即可檢視 Visual Studio 中的預設集。  
  
## <a name="enabling-and-disabling-mdas"></a>啟用和停用 MDA  
 若要啟用和停用 MDA，您可以使用登錄機碼、環境變數和應用程式組態設定。 您必須啟用登錄機碼或環境變數，才能使用應用程式組態設定。  
  
 在 Visual Studio 2005 (含) 以後版本中，當裝載處理序啟用時，即無法停用預設集中的 MDA，或是啟用不在預設集中的 MDA。 預設會啟用裝載處理序，所以必須明確將其停用。  
  
 若要停用 Visual Studio 中的裝載處理序，請執行下列作業：  
  
1.  在方案總管中選取專案。  
  
2.  在 [專案] 功能表上，按一下 [屬性]。  
  
     [專案設計工具] 視窗隨即出現。  
  
3.  按一下 [偵錯] 索引標籤。  
  
4.  在 [啟用偵錯工具] 區段中，清除 [啟用 Visual Studio 裝載處理序] 核取方塊。  
  
 不過，停用裝載處理序會影響效能。 只要防止 Visual Studio 在每次收到 MDA 通知時顯示 MDA 對話方塊，就可以不需要停用 MDA。 若要這樣做，請在 [偵錯] 功能表上按一下 [例外狀況]，展開 [Managed 偵錯助理] 清單，然後針對個別的 MDA，清除 [擲回] 核取方塊。  
  
### <a name="enabling-and-disabling-mdas-by-using-a-registry-key"></a>使用登錄機碼來啟用和停用 MDA  
 您可在 Windows 登錄中新增 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\MDA 子機碼 (類型 REG_SZ，值 1)，啟用 MDA。 將下列範例複製到名為 MDAEnable.reg 的文字檔中。開啟 Windows 登錄編輯程式 (RegEdit.exe)，從 [檔案] 功能表中選擇 [匯入]。 選取 MDAEnable.reg 檔案，以在該電腦上啟用 MDA。 將子機碼設為字串值 1 (不是 DWORD 值 1) 即可啟用從 *ApplicationName.suffix*.mda.config 檔案讀取 MDA 設定的功能。 (例如，[記事本] 的 MDA 組態檔會命名為 notepad.exe.mda.config)  
  
```  
Windows Registry Editor Version 5.00  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework]  
"MDA"="1"  
```  
  
 如果電腦是在 64 位元作業系統上執行 32 位元應用程式，則應將 MDA 機碼設定如下：  
  
```  
      Windows Registry Editor Version 5.00   
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework]  
"MDA"="1"  
```  
  
 如需詳細資訊，請參閱[使用應用程式特定組態設定來啟用和停用 MDA](#appConfig)。 COMPLUS_MDA 環境變數可以覆寫登錄設定。 如需詳細資訊，請參閱[使用環境變數來啟用和停用 MDA](#envVariable)。  
  
 若要停用 MDA，請使用 Windows 登錄編輯程式，將 MDA 子機碼設為 0 (零)。  
  
 根據預設，當您執行附加至偵測工具的應用程式時，會啟用某些 MDA，即使未加入登錄機碼也一樣。 這類助理的範例為 [pInvokeStackImbalance](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) 和 [invalidApartmentStateChange](../../../docs/framework/debug-trace-profile/invalidapartmentstatechange-mda.md)。 若要停用這些助理，您可以依照本節稍早的說明來執行 MDADisable.reg 檔案。  
  
<a name="envVariable"></a>   
### <a name="enabling-and-disabling-mdas-by-using-an-environment-variable"></a>使用環境變數來啟用和停用 MDA  
 MDA 的啟用也可以由環境變數 COMPLUS_MDA 來控制，它會覆寫登錄機碼。 COMPLUS_MDA 字串是 MDA 名稱或其他特殊控制項字串的清單，不區分大小寫，並以分號分隔。 在 Managed 或 Unmanaged 偵錯工具之下啟動時，會依預設啟用一組 MDA。 其做法是在環境變數或登錄機碼的值前面，隱含附加在偵錯工具之下依預設啟用的 MDA 清單 (以分號分隔)。 特殊控制項字串如下：  
  
-   `0` - 停用所有 MDA。  
  
-   `1` - 從 *ApplicationName*.mda.config 讀取 MDA 設定。  
  
-   `managedDebugger` - 明確啟用在偵錯工具之下啟動 Managed 可執行檔時，隱含啟用的所有 MDA。  
  
-   `unmanagedDebugger` - 明確啟用在偵錯工具之下啟動 Unmanaged 可執行檔時，隱含啟用的所有 MDA。  
  
 如果有設定相衝突，最新的設定會覆寫先前的設定：  
  
-   `COMPLUS_MDA=0` 會停用所有 MDA，包括在偵錯工具之下隱含啟用的 MDA。  
  
-   `COMPLUS_MDA=gcUnmanagedToManaged` 會啟用 `gcUnmanagedToManaged`，以及在偵錯工具之下隱含啟用的任何 MDA。  
  
-   `COMPLUS_MDA=0;gcUnmanagedToManaged` 會啟用 `gcUnmanagedToManaged`，但會停用在偵錯工具之下隱含啟用的 MDA。  
  
<a name="appConfig"></a>   
### <a name="enabling-and-disabling-mdas-by-using-application-specific-configuration-settings"></a>使用應用程式特定組態設定來啟用和停用 MDA  
 您可以針對該應用程式，在 MDA 組態檔中個別啟用、停用及設定某些助理。 若要啟用用來設定 MDA 的應用程式組態檔，必須設定 MDA 登錄機碼或 COMPLUS_MDA 環境變數。 應用程式組態檔通常位在與應用程式可執行檔 (.exe) 相同的目錄中。 檔名採用 *ApplicationName*.mda.config 格式；例如，notepad.exe.mda.config。應用程式組態檔中啟用的助理可能會有為了控制該助理行為而特別設計的屬性或項目。 下面範例會示範如何啟用和設定[封送處理](../../../docs/framework/debug-trace-profile/marshaling-mda.md)。  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshaling>  
      <methodFilter>  
        <match name="*"/>  
      </methodFilter>  
      <fieldFilter>  
        <match name="*"/>  
      </fieldFilter>  
    </marshaling>  
  </assistants>  
</mdaConfig>  
```  
  
 `Marshaling` MDA 會針對應用程式中每個 Managed 轉換至 Unmanaged 的作業，發出封送處理至 Unmanaged 類型之 Managed 類型的詳細資訊。 `Marshaling` MDA 也可以分別篩選 `<methodFilter>` 和 `<fieldFilter>` 子項目中提供的方法和結構欄位名稱。  
  
 下列範例示範如何使用預設值來啟用多個 MDA。  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion />  
    <invalidCERCall />  
    <openGenericCERCall />  
    <virtualCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
> [!IMPORTANT]
>  當您在組態檔中指定多個助理時，必須依字母順序將其列出。 例如，如果您想要啟用 `virtualCERCall` 和 `invalidCERCall` MDA ，則必須在 `<invalidCERCall />` 項目前面加入 `<virtualCERCall />` 項目。 如果這些項目沒有依照字母順序，就會顯示未處理的無效組態檔例外狀況訊息。  
  
### <a name="mda-output"></a>MDA 輸出  
 MDA 輸出類似下列範例，會顯示 `pInvokeStackImbalance` MDA 的輸出。  
  
 `A call to PInvoke function 'MDATest!MDATest.Program::StdCall' has unbalanced the stack. This is likely because the managed PInvoke signature does not match the unmanaged target signature. Check that the calling convention and parameters of the PInvoke signature match the target unmanaged signature.`  
  
## <a name="see-also"></a>請參閱  
 [偵錯、追蹤和程式碼剖析](../../../docs/framework/debug-trace-profile/index.md)

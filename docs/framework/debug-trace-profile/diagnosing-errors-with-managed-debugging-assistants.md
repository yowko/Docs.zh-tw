---
title: 診斷 Managed 偵錯助理的錯誤
ms.date: 08/14/2018
f1_keywords:
- EHMDA
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b745fa6a78ab2a7ab0b3a94c9921883d3c56c1b7
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2018
ms.locfileid: "42935740"
---
# <a name="diagnose-errors-with-managed-debugging-assistants"></a>診斷 Managed 偵錯助理的錯誤

Managed 偵錯助理 (MDA) 是偵錯輔助程式，可與通用語言執行平台 (CLR) 合作提供執行階段狀態的相關資訊。 這些助理會產生有關您無法設陷之執行階段事件的告知性訊息。 您可以使用 MDA 來隔離在 Managed 與 Unmanaged 程式碼之間轉換時，所發生之不易發現的應用程式 Bug。

您可以[啟用或停用](#enable-and-disable-mdas)加入至 Windows 登錄機碼，或藉由設定環境變數的所有 Mda。 若要啟用特定 MDA，您可以使用應用程式組態設定。 您可以針對應用程式組態檔中某些個別的 MDA，設定額外的組態設定。 因為在載入執行階段時，會剖析這些組態檔，所以您必須在 Managed 應用程式啟動之前，先啟用 MDA。 您不能為已啟動的應用程式啟用 MDA。

下表列出.NET framework 隨附的 Mda:

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

根據預設，.NET Framework 會啟用所有 Managed 偵錯工具的 MDA 子集。 您可以檢視的預設集在 Visual Studio 中選擇**Windows** > **例外狀況設定**上**偵錯**功能表，然後再展開**Managed 偵錯助理**清單。

![在 Visual Studio 中的例外狀況設定視窗](media/diagnosing-errors-with-managed-debugging-assistants/exception-settings-mdas.png)

## <a name="enable-and-disable-mdas"></a>啟用和停用 Mda

若要啟用和停用 MDA，您可以使用登錄機碼、環境變數和應用程式組態設定。 您必須啟用登錄機碼或環境變數，才能使用應用程式組態設定。

> [!TIP]
> 而不是停用 Mda，您可以防止 Visual Studio 時收到 MDA 通知時顯示 MDA 對話方塊。 若要這樣做，請選擇**Windows** > **例外狀況設定**上**偵錯**功能表中，展開  **Managed 偵錯助理**清單，然後選取或清除**中斷時擲回**核取方塊，針對個別的 MDA。

### <a name="registry-key"></a>登錄機碼

若要啟用 Mda，新增**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\。NETFramework\MDA**子機碼 （類型 REG_SZ，值 1） 在 Windows 登錄中的。 將下列範例複製到名為文字檔*MDAEnable.reg*。開啟 Windows 登錄編輯程式 (RegEdit.exe)，以及從**檔案**功能表中選擇 **匯入**。 選取  *MDAEnable.reg*檔，以便在該電腦上啟用 Mda。 將子機碼設定為字串值**1** (不是 DWORD 值的**1**) 可讓讀取 MDA 設定從*ApplicationName.suffix*.mda.config 檔案。 例如，[記事本] 的 MDA 組態檔會命名為 notepad.exe.mda.config。

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework]
"MDA"="1"
```

如果電腦是在 64 位元作業系統上執行 32 位元應用程式，則應將 MDA 機碼設定如下：

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework]
"MDA"="1"
```

請參閱[應用程式特定組態設定](#application-specific-configuration-settings)如需詳細資訊。 COMPLUS_MDA 環境變數可以覆寫登錄設定。 請參閱[環境變數](#environment-variable)如需詳細資訊。

若要停用 Mda，將 MDA 子機碼設為**0**使用 Windows 登錄編輯程式 （零）。

根據預設，當您執行附加至偵測工具的應用程式時，會啟用某些 MDA，即使未加入登錄機碼也一樣。 您可以藉由執行停用這些助理*MDADisable.reg*檔案，如本節稍早所述。

### <a name="environment-variable"></a>環境變數

MDA 的啟用也可以由環境變數 COMPLUS_MDA 來控制，它會覆寫登錄機碼。 COMPLUS_MDA 字串是 MDA 名稱或其他特殊控制項字串的清單，不區分大小寫，並以分號分隔。 在 Managed 或 Unmanaged 偵錯工具之下啟動時，會依預設啟用一組 MDA。 其做法是在環境變數或登錄機碼的值前面，隱含附加在偵錯工具之下依預設啟用的 MDA 清單 (以分號分隔)。 特殊控制項字串如下：

- `0` - 停用所有 MDA。

- `1` - 從 *ApplicationName*.mda.config 讀取 MDA 設定。

- `managedDebugger` - 明確啟用在偵錯工具之下啟動 Managed 可執行檔時，隱含啟用的所有 MDA。

- `unmanagedDebugger` - 明確啟用在偵錯工具之下啟動 Unmanaged 可執行檔時，隱含啟用的所有 MDA。

如果有設定相衝突，最新的設定會覆寫先前的設定：

- `COMPLUS_MDA=0` 會停用所有 MDA，包括在偵錯工具之下隱含啟用的 MDA。

- `COMPLUS_MDA=gcUnmanagedToManaged` 會啟用 `gcUnmanagedToManaged`，以及在偵錯工具之下隱含啟用的任何 MDA。

- `COMPLUS_MDA=0;gcUnmanagedToManaged` 會啟用 `gcUnmanagedToManaged`，但會停用在偵錯工具之下隱含啟用的 MDA。

### <a name="application-specific-configuration-settings"></a>應用程式特定的組態設定

您可以針對該應用程式，在 MDA 組態檔中個別啟用、停用及設定某些助理。 若要啟用用來設定 MDA 的應用程式組態檔，必須設定 MDA 登錄機碼或 COMPLUS_MDA 環境變數。 應用程式組態檔通常位在與應用程式可執行檔 (.exe) 相同的目錄中。 檔名採用 *ApplicationName*.mda.config 格式；例如，notepad.exe.mda.config。應用程式組態檔中啟用的助理可能會有為了控制該助理行為而特別設計的屬性或項目。

下列範例示範如何啟用及設定[封送處理](../../../docs/framework/debug-trace-profile/marshaling-mda.md):

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

`Marshaling` MDA 會針對應用程式中每個 Managed 轉換至 Unmanaged 的作業，發出封送處理至 Unmanaged 類型之 Managed 類型的詳細資訊。 `Marshaling` MDA 也可以篩選方法的名稱和結構欄位中提供**methodFilter**並**fieldFilter**個子項目，分別。

下列範例示範如何使用其預設設定來啟用多個 Mda:

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
> 當您在組態檔中指定多個助理時，必須依字母順序將其列出。 例如，如果您想要啟用 `virtualCERCall` 和 `invalidCERCall` MDA ，則必須在 `<invalidCERCall />` 項目前面加入 `<virtualCERCall />` 項目。 如果這些項目沒有依照字母順序，就會顯示未處理的無效組態檔例外狀況訊息。

## <a name="mda-exceptions"></a>MDA 例外狀況

啟用 MDA 時，它仍甚至當您的程式碼不執行以偵錯工具。 如果在偵錯工具不存在的情況下，發生 MDA 事件，則會在未處理的例外狀況對話方塊中顯示事件訊息，雖然 MDA 事件並不是未處理的例外狀況。 若要避免此對話方塊，請在程式碼不是在偵錯環境中執行時，移除啟用 MDA 的設定。

當您的程式碼執行 Visual Studio 整合式的開發環境 (IDE) 中時，您可以避免特定 MDA 事件會出現 [例外狀況] 對話方塊。 若要這樣做，請在**偵錯**功能表上，選擇**Windows** > **例外狀況設定**。 在 [**例外狀況設定**] 視窗中，展開**Managed 偵錯助理**清單，然後再清除**中斷時擲回**核取方塊，針對個別的 MDA。 您也可以使用此對話方塊來*啟用*MDA 例外狀況對話方塊的顯示方式。

## <a name="mda-output"></a>MDA 輸出

MDA 輸出會類似下列的範例中，顯示的輸出`PInvokeStackImbalance`MDA:

**PInvoke 函式的呼叫 ' MDATest ！MDATest.Program::StdCall' 有不對稱的堆疊。這可能是因為 managed 的 PInvoke 簽章與未受管理的目標簽章不相符。請檢查的呼叫慣例和 PInvoke 簽章的參數相符的目標 unmanaged 簽章。**

## <a name="see-also"></a>另請參閱

- [偵錯、追蹤和程式碼剖析](../../../docs/framework/debug-trace-profile/index.md)

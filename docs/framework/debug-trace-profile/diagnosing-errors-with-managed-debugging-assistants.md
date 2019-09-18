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
ms.openlocfilehash: 6cb2a240a2e7e82b7015eb7a6d99c2117fa63045
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052893"
---
# <a name="diagnose-errors-with-managed-debugging-assistants"></a>使用受管理的調試助理診斷錯誤

Managed 偵錯助理 (MDA) 是偵錯輔助程式，可與通用語言執行平台 (CLR) 合作提供執行階段狀態的相關資訊。 這些助理會產生有關您無法設陷之執行階段事件的告知性訊息。 您可以使用 MDA 來隔離在 Managed 與 Unmanaged 程式碼之間轉換時，所發生之不易發現的應用程式 Bug。

您可以藉由將金鑰新增至 Windows 登錄或設定環境變數，來[啟用或停](#enable-and-disable-mdas)用所有 mda。 若要啟用特定 MDA，您可以使用應用程式組態設定。 您可以針對應用程式組態檔中某些個別的 MDA，設定額外的組態設定。 因為在載入執行階段時，會剖析這些組態檔，所以您必須在 Managed 應用程式啟動之前，先啟用 MDA。 您不能為已啟動的應用程式啟用 MDA。

下表列出 .NET Framework 隨附的 Mda：

|||
|-|-|
|[asynchronousThreadAbort](asynchronousthreadabort-mda.md)|[bindingFailure](bindingfailure-mda.md)|
|[callbackOnCollectedDelegate](callbackoncollecteddelegate-mda.md)|[contextSwitchDeadlock](contextswitchdeadlock-mda.md)|
|[dangerousThreadingAPI](dangerousthreadingapi-mda.md)|[dateTimeInvalidLocalFormat](datetimeinvalidlocalformat-mda.md)|
|[dirtyCastAndCallOnInterface](dirtycastandcalloninterface-mda.md)|[disconnectedContext](disconnectedcontext-mda.md)|
|[dllMainReturnsFalse](dllmainreturnsfalse-mda.md)|[exceptionSwallowedOnCallFromCom](exceptionswallowedoncallfromcom-mda.md)|
|[failedQI](failedqi-mda.md)|[fatalExecutionEngineError](fatalexecutionengineerror-mda.md)|
|[gcManagedToUnmanaged](gcmanagedtounmanaged-mda.md)|[gcUnmanagedToManaged](gcunmanagedtomanaged-mda.md)|
|[illegalPrepareConstrainedRegion](illegalprepareconstrainedregion-mda.md)|[invalidApartmentStateChange](invalidapartmentstatechange-mda.md)|
|[invalidCERCall](invalidcercall-mda.md)|[invalidFunctionPointerInDelegate](invalidfunctionpointerindelegate-mda.md)|
|[invalidGCHandleCookie](invalidgchandlecookie-mda.md)|[invalidIUnknown](invalidiunknown-mda.md)|
|[invalidMemberDeclaration](invalidmemberdeclaration-mda.md)|[invalidOverlappedToPinvoke](invalidoverlappedtopinvoke-mda.md)|
|[invalidVariant](invalidvariant-mda.md)|[jitCompilationStart](jitcompilationstart-mda.md)|
|[loaderLock](loaderlock-mda.md)|[loadFromContext](loadfromcontext-mda.md)|
|[marshalCleanupError](marshalcleanuperror-mda.md)|[marshaling](marshaling-mda.md)|
|[memberInfoCacheCreation](memberinfocachecreation-mda.md)|[moduloObjectHashcode](moduloobjecthashcode-mda.md)|
|[nonComVisibleBaseClass](noncomvisiblebaseclass-mda.md)|[notMarshalable](notmarshalable-mda.md)|
|[openGenericCERCall](opengenericcercall-mda.md)|[overlappedFreeError](overlappedfreeerror-mda.md)|
|[pInvokeLog](pinvokelog-mda.md)|[pInvokeStackImbalance](pinvokestackimbalance-mda.md)|
|[raceOnRCWCleanup](raceonrcwcleanup-mda.md)|[reentrancy](reentrancy-mda.md)|
|[releaseHandleFailed](releasehandlefailed-mda.md)|[reportAvOnComRelease](reportavoncomrelease-mda.md)|
|[streamWriterBufferedDataLost](streamwriterbuffereddatalost-mda.md)|[virtualCERCall](virtualcercall-mda.md)|

根據預設，.NET Framework 會啟用所有 Managed 偵錯工具的 MDA 子集。 您可以在 [**調試**程式] 功能表上選擇 [ **Windows**  > **例外狀況設定**]，然後展開 [ **Managed 調試**程式] 清單，以在 Visual Studio 中查看預設集合。

![Visual Studio 中的 [例外狀況設定] 視窗](./media/diagnosing-errors-with-managed-debugging-assistants/exception-settings-mdas.png)

## <a name="enable-and-disable-mdas"></a>啟用和停用 Mda

若要啟用和停用 MDA，您可以使用登錄機碼、環境變數和應用程式組態設定。 您必須啟用登錄機碼或環境變數，才能使用應用程式組態設定。

> [!TIP]
> 您不需要停用 Mda，只要收到 MDA 通知，您就可以防止 Visual Studio 顯示 MDA 對話方塊。 若要這麼做，請選擇 [**調試**程式] 功能表上的 [ **Windows**  > **例外狀況設定**]，展開 [ **Managed 調試**程式] 清單，然後選取或清除個別 MDA 的 [擲回**時中斷**] 核取方塊。

### <a name="registry-key"></a>登錄機碼

若要啟用 Mda，請**新增\\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft。** Windows 登錄中的 NETFramework\MDA 子機碼（類型 REG_SZ，值1）。 將下列範例複製到名為*mdaenable.reg*的文字檔中。開啟 Windows 登錄編輯程式（Regedit.exe），然後從 [檔案 **] 功能表選擇 [** 匯**入**]。 選取 [ *mdaenable.reg* ] 檔案，以啟用該電腦上的 mda。 將子機碼設為字串值**1** （不是 DWORD 值**1**），可以從*ApplicationName*檔案讀取 mda 設定。 例如，「記事本」的 MDA 設定檔案會命名為 notepad.exe. config.xml。

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

如需詳細資訊，請參閱[應用程式特定的設定](#application-specific-configuration-settings)。 COMPLUS_MDA 環境變數可以覆寫登錄設定。 如需詳細資訊，請參閱[環境變數](#environment-variable)。

若要停用 Mda，請使用 Windows 登錄編輯程式，將 MDA 子機碼設定為**0** （零）。

根據預設，當您執行附加至偵測工具的應用程式時，會啟用某些 MDA，即使未加入登錄機碼也一樣。 如本節稍早所述，您可以執行*mdadisable.reg*來停用這些助理。

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

### <a name="application-specific-configuration-settings"></a>應用程式特定的設定

您可以針對該應用程式，在 MDA 組態檔中個別啟用、停用及設定某些助理。 若要啟用用來設定 MDA 的應用程式組態檔，必須設定 MDA 登錄機碼或 COMPLUS_MDA 環境變數。 應用程式組態檔通常位在與應用程式可執行檔 (.exe) 相同的目錄中。 檔名採用 *ApplicationName*.mda.config 格式；例如，notepad.exe.mda.config。應用程式組態檔中啟用的助理可能會有為了控制該助理行為而特別設計的屬性或項目。

下列範例顯示如何啟用和設定[封送處理](marshaling-mda.md)：

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

`Marshaling` MDA 會針對應用程式中每個 Managed 轉換至 Unmanaged 的作業，發出封送處理至 Unmanaged 類型之 Managed 類型的詳細資訊。 MDA 也可以分別篩選 methodFilter 和**fieldFilter**子項目中提供的方法和結構欄位的名稱。 `Marshaling`

下列範例顯示如何使用預設設定來啟用多個 Mda：

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

當 MDA 啟用時，即使您的程式碼不是在偵錯工具下執行，它仍是作用中狀態。 如果在偵錯工具不存在的情況下，發生 MDA 事件，則會在未處理的例外狀況對話方塊中顯示事件訊息，雖然 MDA 事件並不是未處理的例外狀況。 若要避免此對話方塊，請在程式碼不是在偵錯環境中執行時，移除啟用 MDA 的設定。

當您的程式碼在 Visual Studio 的整合式開發環境（IDE）中執行時，您可以避免出現特定 MDA 事件的例外狀況對話方塊。 若要這麼做，請在 [**調試**程式] 功能表上，選擇 [ **Windows**  > **例外狀況設定**]。 在 [**例外狀況設定**] 視窗中，展開 [ **Managed 偵錯工具助理**] 清單，然後清除個別 MDA 的 [擲回**時中斷**] 核取方塊。 您也可以使用此對話方塊來*啟用*[MDA 例外狀況] 對話方塊的顯示。

## <a name="mda-output"></a>MDA 輸出

Mda 輸出類似于下列範例，其會顯示來自`PInvokeStackImbalance` MDA 的輸出：

**呼叫 PInvoke 函數 ' MDATest！MDATest 程式：： StdCall ' 的堆疊不對稱。這很可能是因為受控 PInvoke 簽章與非受控目標籤章不相符。檢查 PInvoke 簽章的呼叫慣例和參數是否符合目標非受控簽章。**

## <a name="see-also"></a>另請參閱

- [偵錯、追蹤和程式碼剖析](index.md)

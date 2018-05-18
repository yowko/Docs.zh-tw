---
title: Fuslogvw.exe (組件繫結記錄檔檢視器)
ms.date: 03/30/2017
helpviewer_keywords:
- failed assembly binds
- Fuslogvw.exe
- displaying failed assembly bind details
- assemblies [.NET Framework], failed assembly binds
- locating assemblies
- Assembly Binding Log Viewer
ms.assetid: e32fa443-0778-4cc3-bf36-5c8ea297d296
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 73fa08f92a4572a501be65f05e8141c349cc003e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="fuslogvwexe-assembly-binding-log-viewer"></a>Fuslogvw.exe (組件繫結記錄檔檢視器)
組件繫結記錄檔檢視器會顯示組件繫結的詳細資料。 這項資訊有助於診斷 .NET Framework 為何無法在執行階段找到組件。 這類失敗通常是因為組件部署至不正確的位置、原生映像已失效，或版本號碼或文化特定不符所致。 通用語言執行平台找不到組件，通常在應用程式中會顯示為 <xref:System.TypeLoadException>。  
  
> [!IMPORTANT]
>  您必須以系統管理員權限執行 fuslogvw.exe。  
  
 此工具會自動與 Visual Studio 一起安裝。 若要執行這項工具，請使用具有系統管理員認證的開發人員命令提示字元 (或 Windows 7 中的 Visual Studio 命令提示字元)。 如需詳細資訊，請參閱[命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)。  
  
 在命令提示字元下輸入下列命令：  
  
```  
fuslogvw  
```  
  
 檢視器會針對每一個失敗的組件繫結顯示一個項目。 針對每一項失敗，檢視器會描述啟始該繫結的應用程式、所要繫結的組件 (包括名稱、版本、文化特性和公開金鑰)，以及失敗的日期和時間。  
  
### <a name="to-change-the-log-location-view"></a>若要變更記錄檔位置檢視  
  
1.  選取 [預設值] 選項按鈕，可檢視所有應用程式類型的繫結失敗。 根據預設，記錄項目會存放在 wininet 快取中磁碟上的每個使用者目錄中。  
  
2.  選取 [自訂] 選項按鈕，可檢視您指定之自訂目錄中的繫結失敗。 您必須透過將 [記錄檔設定] 對話方塊中的自訂記錄檔路徑設為有效的目錄名稱，指定要讓執行階段存放記錄檔的自訂位置。 這個目錄應該是乾淨的，只包含執行階段產生的檔案。 如果它包含會產生失敗記錄的可執行檔，則失敗將不會記錄下來，因為工具會嘗試使用與該可執行檔相同的名稱建立目錄。 此外，嘗試從記錄檔位置執行可執行檔將會失敗。  
  
    > [!NOTE]
    >  預設繫結位置要比自訂繫結位置更合適。 執行階段會將預設繫結位置存放到 wininet 快取中，因此會自動將它清除。如果您指定自訂繫結位置，則必須負責將它清除。  
  
### <a name="to-view-details-about-a-specific-failure"></a>若要檢視特定失敗的詳細資料  
  
1.  在檢視器中選取所需項目的應用程式名稱。  
  
2.  按一下 [檢視記錄檔] 按鈕。 或者，您也可以按兩下選取的項目。  
  
     工具便會顯示有關所選取繫結失敗的下列詳細資料：  
  
    -   繫結失敗的特定原因，例如「找不到檔案」或「版本不符」。  
  
    -   啟始繫結之應用程式的相關資訊，包括其名稱、應用程式的根目錄 (AppBase) 以及私用搜尋路徑的描述 (如果有的話)。  
  
    -   工具所搜尋之組件的識別。  
  
    -   已套用之任何應用程式、發行者或系統管理員版本原則的描述。  
  
    -   在[全域組件快取](../../../docs/framework/app-domains/gac.md)中是否找到組件。  
  
    -   所有探查 URL 的清單。  
  
 以下範例記錄項目將顯示失敗之組件繫結的詳細資訊。  
  
```  
*** Assembly Binder Log Entry  (3/5/2007 @ 12:54:20 PM) ***  
  
The operation failed.  
Bind result: hr = 0x80070002. The system cannot find the file specified.  
  
Assembly manager loaded from:  C:\WINNT\Microsoft.NET\Framework\v2.0.50727\fusion.dll  
Running under executable  C:\Program Files\Microsoft.NET\FrameworkSDK\Samples\Tutorials\resourcesandlocalization\graphic\cs\graphicfailtest.exe  
--- A detailed error log follows.   
  
=== Pre-bind state information ===  
LOG: DisplayName = graphicfailtest.resources, Version=0.0.0.0, Culture=en-US, PublicKeyToken=null  
 (Fully-specified)  
LOG: Appbase = C:\Program Files\Microsoft.NET\FrameworkSDK\Samples\Tutorials\resourcesandlocalization\graphic\cs\  
LOG: Initial PrivatePath = NULL  
LOG: Dynamic Base = NULL  
LOG: Cache Base = NULL  
LOG: AppName = NULL  
Calling assembly : graphicfailtest, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
===  
  
LOG: Processing DEVPATH.  
LOG: DEVPATH is not set. Falling through to regular bind.  
LOG: Policy not being applied to reference at this time (private, custom, partial, or location-based assembly bind).  
LOG: Post-policy reference: graphicfailtest.resources, Version=0.0.0.0, Culture=en-US, PublicKeyToken=null  
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources.DLL.  
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources/graphicfailtest.resources.DLL.  
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources.EXE.  
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources/graphicfailtest.resources.EXE.  
LOG: All probing URLs attempted and failed.  
```  
  
### <a name="to-delete-a-single-entry-from-the-log"></a>若要從記錄檔刪除單一項目  
  
1.  在檢視器中選取項目。  
  
2.  按一下 [刪除項目] 按鈕。  
  
### <a name="to-delete-all-entries-from-the-log"></a>若要從記錄檔刪除所有項目  
  
-   按一下 [全部刪除] 按鈕。  
  
### <a name="to-refresh-the-user-interface"></a>若要重新整理使用者介面  
  
-   按一下 [重新整理] 按鈕。 檢視器在執行時不會自動偵測新的記錄項目。 您必須使用 [重新整理] 按鈕才能顯示新項目。  
  
### <a name="to-change-the-log-settings"></a>若要變更記錄檔設定  
  
-   按一下 [設定] 按鈕，開啟 [記錄檔設定] 對話方塊。  
  
### <a name="to-view-the-about-dialog"></a>若要檢視關於對話方塊  
  
-   按一下 [關於] 按鈕。  
  
## <a name="binding-logs-for-native-images"></a>原生映像的繫結記錄檔  
 根據預設，Fuslogvw.exe 會記錄正常的組件繫結要求。 或者，您可以記錄使用 [Ngen.exe (原生映像產生器)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) 所建立之原生映像的組件繫結。  
  
#### <a name="to-log-assembly-binds-for-native-images"></a>若要記錄原生映像的組件繫結  
  
-   在 [記錄檔分類] 群組中，選取 [原生映像] 選項按鈕。  
  
 下列記錄將顯示建立應用程式的原生影像時，不存在的相依性所造成的失敗。 如果執行階段的相依性與 Ngen.exe 執行時的相依性不同，則不允許繫結至原生映像。  
  
```  
*** Assembly Binder Log Entry  (12/8/2006 @ 5:22:07 PM) ***  
  
The operation failed.  
Bind result: hr = 0x80070002. The system cannot find the file specified.  
  
Assembly manager loaded from:  E:\Windows\Microsoft.NET\Framework64\v2.0.50727\mscorwks.dll  
Running under executable  E:\test\App.exe  
--- A detailed error log follows.   
  
LOG: Start binding of native image App, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
LOG: IL assembly loaded from E:\test\App.exe.  
LOG: Start validating native image App, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
LOG: Start validating all the dependencies.  
LOG: [Level 1]Start validating native image dependency mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089.  
LOG: Dependency evaluation succeeded.  
LOG: [Level 1]Start validating IL dependency b, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
WRN: Dependency assembly was not found at ngen time, but is found at binding time. Disallow using this native image.  
WRN: No matching native image found.  
LOG: Bind to native image assembly did not succeed. Use IL image.  
```  
  
 下列記錄檔顯示的原生映像繫結失敗，是由於應用程式執行時電腦上的安全性設定，與原生映像建立時的安全性設定不同所致。  
  
```  
*** Assembly Binder Log Entry  (12/8/2006 @ 5:29:09 PM) ***  
  
The operation failed.  
Bind result: hr = 0x80004005. Unspecified error  
  
Assembly manager loaded from:  E:\Windows\Microsoft.NET\Framework64\v2.0.50727\mscorwks.dll  
Running under executable  E:\test\Application101622.exe  
--- A detailed error log follows.   
  
LOG: Start binding of native image Application101622, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
LOG: IL assembly loaded from E:\test\Application101622.exe.  
LOG: Start validating native image Application101622, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
LOG: Start validating all the dependencies.  
LOG: [Level 1]Start validating native image dependency mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089.  
LOG: Dependency evaluation succeeded.  
LOG: [Level 1]Start validating IL dependency Dependency101622, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
LOG: Dependency evaluation succeeded.  
LOG: Validation of dependencies succeeded.  
LOG: Start loading all the dependencies into load context.  
LOG: Loading of dependencies succeeded.  
LOG: Bind to native image succeeded.  
Native image has correct version information.  
Attempting to use native image E:\Windows\assembly\NativeImages_v2.0.50727_64\Application101622\1ac7fadabec4f72575d807501e9fdc72\Application101622.ni.exe.  
Rejecting native image because it failed the security check. The assembly's permissions must have changed since the time it was ngenned, or it is running with a different security context.  
Discarding native image.  
```  
  
## <a name="the-log-settings-dialog"></a>[記錄檔設定] 對話方塊  
 您可以使用 [記錄檔設定] 對話方塊執行下列動作。  
  
#### <a name="to-disable-logging"></a>若要停用記錄  
  
-   選取 [停用記錄] 選項按鈕。  請注意，這個選項預設為選取狀態。  
  
#### <a name="to-log-assembly-binds-in-exceptions"></a>若要記錄例外狀況中的組件繫結  
  
-   選取 [在例外狀況文字中記錄] 選項按鈕。 例外狀況文字中只會記錄最簡要的融合記錄資訊。 若要檢視完整資訊，請使用其中一項其他設定。  
  
     請參閱有關以定義域中性方式載入之組件的＜重要事項＞。  
  
#### <a name="to-log-assembly-bind-failures"></a>若要記錄組件繫結失敗  
  
-   選取 [在磁碟中記錄失敗的繫結] 選項按鈕。  
  
     請參閱有關以定義域中性方式載入之組件的＜重要事項＞。  
  
#### <a name="to-log-all-assembly-binds"></a>若要記錄所有組件繫結  
  
-   選取 [在磁碟中記錄所有繫結] 選項按鈕。  
  
     請參閱有關以定義域中性方式載入之組件的＜重要事項＞。  
  
> [!IMPORTANT]
>  以定義域中性方式載入組件時 (例如，將 <xref:System.AppDomainSetup.LoaderOptimization%2A> 屬性設定為 <xref:System.LoaderOptimization.MultiDomain?displayProperty=nameWithType> 或 <xref:System.LoaderOptimization.MultiDomainHost?displayProperty=nameWithType>)，開啟記錄功能在某些情況下可能會造成記憶體流失。 如果在將定義域中性模組載入至應用程式定義域時加入一筆記錄項目，稍後卸載應用程式定義域時，便可能發生這種情況。 在處理序結束之前，可能都不會發行這個記錄項目。 有些偵錯工具會自動開啟記錄功能。  
  
#### <a name="to-enable-a-custom-log-path"></a>若要啟用自訂記錄檔路徑  
  
1.  選取 [啟用自訂的記錄檔路徑] 選項按鈕。  
  
2.  在 [自訂的記錄檔路徑] 文字方塊中輸入路徑。  
  
> [!NOTE]
>  [組件繫結記錄檔檢視器 (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) 使用 Internet Explorer (IE) 快取來儲存其繫結記錄檔。 由於 IE 快取偶爾會損毀，因此[組件繫結記錄檔檢視器 (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) 有時可能會停止在檢視視窗內顯示新的繫結記錄檔。 這種損毀導致 .NET 繫結基礎結構 (融合) 無法寫入繫結記錄檔或從繫結記錄檔讀取  (如果您使用自訂的記錄檔路徑，就不會發生這個問題)。若要修復損毀並讓融合再次顯示繫結記錄檔，請從 IE 的 [網際網路選項] 對話方塊中刪除網際網路暫存檔 (Temporary Internet Files)，以便清除 IE 快取。  
>   
>  如果 Unmanaged 應用程式藉由實作 `IHostAssemblyManager` 和 `IHostAssemblyStore` 介面裝載 Common Language Runtime，則無法將記錄項目儲存在 wininet 快取中。  若要檢視實作這些介面之自訂主機的記錄項目，則必須指定替代的記錄檔路徑。  
  
#### <a name="to-enable-logging-for-apps-running-in-the-windows-app-container"></a>若要啟用在 Windows 應用程式容器中執行的應用程式記錄功能  
  
1.  啟用自訂的記錄檔路徑，如上述程序所述。 根據預設，在 Windows 應用程式容器中執行的應用程式對硬碟的存取權會受到限制。 您指定的目錄將可以對應用程式容器中的所有應用程式進行讀取/寫入。  
  
2.  選取 [啟用擬真記錄] 核取方塊。  
  
    > [!NOTE]
    >  只有在 Windows 8 (含) 以後版本中才會啟用這個方塊。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.TypeLoadException>  
 [工具](../../../docs/framework/tools/index.md)  
 [全域組件快取](../../../docs/framework/app-domains/gac.md)  
 [執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

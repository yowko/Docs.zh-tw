---
title: "MDbg.exe (.NET Framework Command-Line Debugger) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "command-line debugger [.NET Framework]"
  - "MDbg.exe"
ms.assetid: 28a3f509-07e2-4dbe-81df-874c5e969cc4
caps.latest.revision: 27
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 27
---
# MDbg.exe (.NET Framework Command-Line Debugger)
.NET Framework 命令列偵錯工具可以協助工具廠商和應用程式開發人員尋找並修復以 .NET Framework 通用語言執行平台為目標之程式的 Bug。  這個工具使用執行階段偵錯 API 來提供偵錯服務。  目前您只能使用 MDbg.exe 偵錯 Managed 程式碼；不支援偵錯 Unmanaged 程式碼。  
  
 此工具會透過 NuGet 提供。  如需安裝資訊，請參閱 [MDbg 0.1.0](http://www.nuget.org/packages/MDbg/0.1.0) \(英文\)。  若要執行此工具，請使用 Package Manager Console。  如需如何使用 Package Manager Console 的詳細資訊，請參閱[使用 Package Manager Console](http://docs.nuget.org/docs/start-here/Using-the-Package-Manager-Console) \(英文\)。  
  
 在 Package Manager 命令提示字元中，輸入下列命令：  
  
## 語法  
  
```  
MDbg [ProgramName[arguments]] [options]  
```  
  
## 命令  
 當您在偵錯工具中時 \(例如顯示 **mdbg\>** 提示時\)，請輸入下一節中所述的其中一個命令：  
  
 **command** \[*arguments*\]  
  
 MDbg.exe 命令會區分大小寫。  
  
|命令|描述|  
|--------|--------|  
|**ap**\[**rocess**\] \[*number*\]|切換至另一個已偵錯的處理序，或列印可使用的處理序。  這些數字不是實際的處理序 ID \(PID\)，而是從 0 開始建立索引的清單。|  
|**a**\[**ttach**\] \[*pid*\]|附加至處理序，或列印可使用的處理序。|  
|**b**\[**reak**\] \[*ClassName.Method* &#124; *FileName:LineNo*\]|在指定的方法上設定中斷點。  依序掃描模組。<br /><br /> -   **break** *FileName:LineNo* 會在來源的某個位置上設定中斷點。<br />-   **break** *~number* 會以 **x** 命令在最近顯示的符號上設定中斷點。<br />-   **break** *module\!ClassName.Method\+IlOffset* 會在完整限定的位置上設定中斷點。|  
|**block**\[**ingObjects**\]|顯示封鎖執行緒的監視器鎖定。|  
|**ca**\[**tch**\] \[*exceptionType*\]|會導致偵錯工具在所有例外狀況中斷，而不只是未處理的例外狀況。|  
|**cl**\[**earException**\]|將目前的例外狀況標記為已處理，以便繼續執行。  如果不處理例外狀況的原因，可能會很快再次擲回例外狀況。|  
|**conf**\[**ig**\] \[*option value*\]|顯示所有可設定的選項，並說明如何在沒有選擇項值時叫用該選項。  如果已指定選項，請設定 `value` 做為目前的選項。  下列為目前可用的選項：<br /><br /> -   `extpath` 會在使用 `load` 命令時設定搜尋擴充的路徑。<br />-   `extpath+` 會新增一個載入擴充的路徑。|  
|**del**\[**ete**\]|刪除中斷點。|  
|**de**\[**tach**\]|從已偵錯的處理序中斷連結。|  
|**d**\[**own**\] \[*frames*\]|將現用堆疊框架往下移。|  
|**echo**|回應訊息至主控台。|  
|**enableNotif**\[**ication**\] *typeName* 0&#124;1|啟用 \(1\) 或停用 \(0\) 指定類型的自訂通知。|  
|**ex**\[**it**\] \[*exitcode*\]|結束 MDbg.exe 殼層，並且選擇性指定處理序結束代碼。|  
|**fo**\[**reach**\] \[*OtherCommand*\]|在所有執行緒上執行命令。  *OtherCommand* 是在一個執行緒上作業的有效命令；**foreach** *OtherCommand* 則是在所有執行緒上執行相同的命令。|  
|**f**\[**unceval**\] \[`-ad` *Num*\] *functionName* \[*args ...*\]|在目前作用中執行緒上執行函式評估，其中要評估的函式是 *functionName*。  函式名稱必須是完整名稱，包括命名空間。<br /><br /> `-ad` 選項指定要用來解析函式的應用程式定義域。  如果未指定 `-ad` 選項，用來解析的應用程式定義域會預設為用來進行函式評估之執行緒所在的應用程式定義域。<br /><br /> 如果正在進行評估的函式並非靜態，傳入的第一個參數應該是 `this` 指標。  所有應用程式定義域都會進行搜尋，以找尋函式評估的引數。<br /><br /> 若要向應用程式定義域要求值，請用模組和應用程式定義域名稱做為變數前置詞，例如 `funceval -ad 0 System.Object.ToString hello.exe#0!MyClass.g_rootRef`。  這個命令會評估應用程式定義域 `0` 中的函式 `System.Object.ToString`。  由於 `ToString` 方法是執行個體函式，第一個參數必須是 `this` 指標。|  
|**g**\[**o**\]|會讓程式繼續執行，直到遭遇中斷點、程式結束，或是事件 \(例如，未處理的例外狀況\) 造成程式停止為止。|  
|**h**\[**elp**\] \[*command*\]<br /><br /> \-或\-<br /><br /> **?** \[*command*\]|顯示所有命令的描述，或是已指定命令的詳細描述。|  
|**ig**\[**nore**\] \[*event*\]|讓偵錯工具只在未處理的例外狀況時停止。|  
|**int**\[**ercept**\] *FrameNumber*|讓偵錯工具回復至指定的框架編號。<br /><br /> 如果偵錯工具遇到例外狀況，請使用這個命令，讓偵錯工具回復至指定的框架編號。  您可以使用 **set** 命令變更程式狀態，同時繼續使用 **go** 命令。|  
|**k**\[**ill**\]|停止使用中處理序。|  
|**l**\[**ist**\] \[*modules* &#124; *appdomains*&#124; *assemblies*\]|顯示載入的模組、應用程式定義域或組件。|  
|**lo**\[**ad**\] *assemblyName*|以下列方式載入擴充功能：載入指定的組件，然後嘗試從 `Microsoft.Tools.Mdbg.Extension.Extension` 類型執行靜態方法 `LoadExtension`。|  
|**log** \[*eventType*\]|設定或顯示要記錄的事件。|  
|**mo**\[**de**\] \[*option on\/off*\]|設定不同的偵錯工具選項。  使用 `mode` 而不指定選項，以取得偵錯模式清單及其目前設定。|  
|**mon**\[**itorInfo**\] *monitorReference*|顯示物件監視器鎖定資訊。|  
|**newo**\[**bj**\] *typeName* \[*arguments...*\]|建立 *typeName* 類型的新物件。|  
|**n**\[**ext**\]|執行程式碼，然後移至下一行 \(即使下一行包含許多函式呼叫，也要下移\)。|  
|**Opendump** *pathToDumpFile*|開啟指定的傾印檔案進行偵錯。|  
|**o**\[**ut**\]|移至目前函式的尾端。|  
|**pa**\[**th**\] \[*pathName*\]|如果二進位檔中的位置無法使用，則搜尋原始程式檔的指定路徑。|  
|**p**\[**rint**\] \[*var*\] &#124; \[`-d`\]|列印範圍中的所有變數 \(**print**\)、列印指定的變數 \(**print** *var*\)，或列印偵錯工具變數 \(**print** `-d`\)。|  
|**printe**\[**xception**\] \[*\-r*\]|列印目前執行緒上的最後一個例外狀況。  使用 `–r` \(遞迴\) 選項來周遊例外狀況物件上的 `InnerException` 屬性，以取得整個例外狀況鏈結的相關資訊。|  
|**pro**\[**cessenum**\]|顯示使用中處理序。|  
|**q**\[**uit**\] \[*exitcode*\]|終止 MDbg.exe Shell，並選擇性指定處理序結束代碼。|  
|**re**\[**sume**\] \[`*` &#124; \[`~`\]*threadNumber*\]|繼續目前的執行緒，或由 *threadNumber* 參數指定的執行緒。<br /><br /> 如果 *threadNumber* 參數指定為 `*`，或是如果執行緒編號以 `~` 開頭，則將此命令套用至所有執行緒，只有由 *threadNumber* 指定的執行緒除外。<br /><br /> 繼續非暫止的執行緒沒有任何效用。|  
|**r**\[**un**\] \[`-d`\(`ebug`\) &#124; \-`o`\(`ptimize`\) &#124;`-enc`\] \[\[*path\_to\_exe*\] \[*args\_to\_exe*\]\]|停止目前處理序 \(如果有的話\)，並啟動新的處理序。  如果沒有傳遞可執行的引數，這個命令會執行先前以 `run` 命令執行的程式。  如果已提供可執行的引數，就會使用選擇性地提供的引數執行指定的程式。<br /><br /> 如果略過類別載入、模組載入和執行緒啟動事件 \(如預設情況\)，程式就會在主要執行緒之第一個可執行的指令上停止。<br /><br /> 您可以使用下列三個旗標的其中一個，強制執行偵錯工具對程式碼進行 Just\-In\-Time \(JIT\) 編譯：<br /><br /> -   `-d`*\(*`ebug`*\)* 會停用最佳化。  這是 MDbg.exe 的預設值。<br />-   `-o`*\(*`ptimize`*\)* 會強制程式碼像在偵錯工具之外一樣執行，但同時也讓偵錯經驗更加困難。  這是供在偵錯工具之外使用的預設值。<br />-   `-enc` 會啟用「編輯後繼續」功能，但是會因而影響到效能。|  
|**Set** *variable*\=*value*|變更任何範圍內變數的值。<br /><br /> 您也可以自行建立偵錯工具變數，並從您的應用程式之內指定參考值給變數。  這些值是做為原始值的控制代碼，即使原始值超出範圍以外也無妨。  所有偵錯工具變數都必須以 `$` 開頭 \(例如，`$var`\)。  透過使用下列命令，將控制代碼設定為 nothing，清除這些控制代碼：<br /><br /> `set $var=`|  
|**Setip** \[`-il`\] *number*|將檔案中目前的指令指標 \(IP\) 設定為指定的位置。  如果指定 `-il` 選項，則數字代表方法中的 Microsoft intermediate language \(MSIL\) 位移。  否則數字表示原始程式碼行號。|  
|**sh**\[**ow**\] \[*lines*\]|指定要顯示的行數。|  
|**s**\[**tep**\]|將執行作業移入目前程式碼行上的下一個函式，或是如果沒有函式可逐步執行，即移至下一行。|  
|**su**\[**spend**\] \[\* &#124; \[~\]*threadNumber*\]|停止目前的執行緒，或由 *threadNumber* 參數指定的執行緒。  如果 *threadNumber* 是指定為 `*`，這個命令會套用至所有執行緒。  如果執行緒編號以 `~` 開頭，此命令可套用至所有執行緒，只有由 *threadNumber* 指定的執行緒除外。  在處理序由 **go** 或 **step** 命令執行時，會排除暫止的執行緒不加以執行。  如果處理序中沒有非暫止的執行緒，而您發出 **go** 命令，處理序將不會繼續。  在這種情況下，可按 CTRL\-C 中斷處理序。|  
|**sy**\[**mbol**\] *commandName* \[*commandValue*\]|指定下列任何一個命令：<br /><br /> -   `symbol path` \[`"``value``"`\]：顯示或設定目前的符號路徑。<br />-   `symbol addpath` `"``value``"` \- 加入至您目前的符號路徑。<br />-   `symbol reload` \[`"``module``"`\]：重新載入所有符號或指定模組的符號。<br />-   `symbol list` \[`module`\]：顯示所有模組或指定模組目前載入的符號。|  
|**t**\[**hread**\] \[*newThread*\] \[\-*nick nickname*`]`|不帶參數的執行緒命令會顯示目前處理序中的所有 Managed 執行緒。  執行緒通常是以其執行緒編號識別，但是如果執行緒有指定的暱稱，則改為顯示暱稱。  您可以使用 `-nick` 參數指派暱稱給執行緒。<br /><br /> -   **thread** `-nick` *threadName* 會指派暱稱給目前執行中的執行緒。<br /><br /> 暱稱不可為編號。  如果目前的執行緒已經指定暱稱，就會以新的暱稱取代舊的暱稱。  如果新暱稱是空字串 \(""\)，則刪除目前執行緒的暱稱，而不指定任何新暱稱給執行緒。|  
|**u**\[**p**\]|將現用堆疊框架往上移。|  
|**uwgc**\[**handle**\] \[*var*\] &#124; \[*address*\]|列印由控制代碼追蹤的變數。  控制代碼可以用名稱或位址加以指定。|  
|**when**|顯示目前使用中的 `when` 陳述式。<br /><br /> **when** **delete all** &#124; `num` \[`num` \[`num` …\]\]：刪除數字指定的 `when` 陳述式，若指定 `all` 則刪除所有 `when` 陳述式。<br /><br /> **when** `stopReason` \[`specific_condition`\] **do** `cmd` \[`cmd` \[`cmd` …\] \]：*stopReason* 參數可以是下列其中一個：<br /><br /> `StepComplete`, `ProcessExited`, `ThreadCreated`, `BreakpointHit`, `ModuleLoaded`, `ClassLoaded`, `AssemblyLoaded`, `AssemblyUnloaded`, `ControlCTrapped`, `ExceptionThrown`, `UnhandledExceptionThrown`, `AsyncStop`, `AttachComplete`, `UserBreak`, `EvalComplete`, `EvalException`, `RemapOpportunityReached`, `NativeStop`.<br /><br /> *specific\_condition* 可以是以下之一：<br /><br /> -   *number*：對於 `ThreadCreated` 和 `BreakpointHit`，只有在由執行緒 ID\/中斷點編號，以相同的值停止時，才會觸發動作。<br />-   \[`!`\]*name*：針對 `ModuleLoaded`、`ClassLoaded`、`AssemblyLoaded`、`AssemblyUnloaded`、`ExceptionThrown` 和 `UnhandledExceptionThrown`，只在名稱與 *stopReason* 的名稱相符時，才會觸發動作。<br /><br /> *specific\_condition* 對其他 *stopReason* 的值必須是空白。|  
|**w**\[**here**\] \[`-v`\] \[`-c` *depth*\] \[*threadID*\]|顯示有關堆疊框架的偵錯資訊。<br /><br /> -   `-v` 選項提供有關各個所顯示堆疊框架的詳細資訊。<br />-   指定 `depth` 的數字，限制所顯示的框架數目。  使用 **all** 命令，顯示所有框架。  預設值為 100。<br />-   如果指定 *threadID* 參數，您可以控制與堆疊相關聯的執行緒。  預設只有目前的執行緒。  使用 **all** 命令，取得所有執行緒。|  
|**x** \[`-c` *numSymbols*\] \[*module*\[`!`*pattern*\]\]|顯示與模組 `pattern` 相符的函式。<br /><br /> 如果指定了 *numSymbols*，則輸出僅限在指定的數目以內。  如果未指定 *pattern* 的 `!` \(指示規則運算式\)，則顯示所有功能。  如果未提供 *module*，則顯示所有載入的模組。  符號 \(*~\#*\) 可透過使用 **break** 命令，用來設定中斷點。|  
  
## 備註  
 使用編譯器專用旗標編譯要偵錯的應用程式，會讓編譯器產生偵錯符號。  如需這些旗標的詳細資訊，請參閱編譯器的文件。  您可以偵錯最佳化的應用程式，但是有些偵錯資訊將會遺失。  例如，許多區域變數將不可見，而原始程式行也會不準確。  
  
 編譯應用程式之後，請在命令提示字元輸入 **mdbg** 來啟動偵錯工作階段，如下列範例所示。  
  
```  
C:\Program Files\Microsoft Visual Studio 8\VC>mdbg  
MDbg (Managed debugger) v2.0.50727.42 (RTM.050727-4200) started.  
Copyright (C) Microsoft Corporation. All rights reserved.  
  
For information about commands type "help";  
to exit program type "quit".  
mdbg>  
```  
  
 `mdbg>` 提示表示您正在使用偵錯工具。  
  
 進入偵錯工具後，請使用上一節使用的指令和引數。  
  
## 範例  
  
## 請參閱  
 [Tools](../../../docs/framework/tools/index.md)   
 [命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
---
title: "Ngen.exe (原生映像產生器)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Native Image Generator
- images [.NET Framework], native
- side-by-side execution, native images
- assemblies [.NET Framework], native image
- Ngen.exe
- native image generation
- native image cache
- publisher policy applied for native images
- invalid images
- BypassNGenAttribute
- System.Runtime.BypassNGenAttribute
ms.assetid: 44bf97aa-a9a4-4eba-9a0d-cfaa6fc53a66
caps.latest.revision: "57"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 20c120323356171d78da35a490488f4654baece6
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="ngenexe-native-image-generator"></a>Ngen.exe (原生映像產生器)
原生映像產生器 (Ngen.exe) 是一種可以增進 Managed 應用程式效能的工具。 Ngen.exe 會建立原生映像，也就是包含已編譯之處理器特定機器碼的檔案，然後將原生映像安裝到本機電腦上的原生映像快取中。 執行階段就可以從快取中使用原生映像，而不是使用 Just-In-Time (JIT) 編譯器來編譯原始組件。  
  
 Ngen.exe 在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 中的變更：  
  
-   Ngen.exe 現在會以完全信任的方式編譯組件，而且不再評估程式碼存取安全性 (CAS) 原則。  
  
-   以 Ngen.exe 產生的原生映像已無法載入以部分信任執行的應用程式。  
  
 Ngen.exe 在 .NET Framework 2.0 版中的變更：  
  
-   安裝組件時也會安裝其相依性，因而簡化 Ngen.exe 的語法。  
  
-   現在可以在應用程式定義域之間共用原生映像。  
  
-   `update` 這個新動作可以重新建立已經失效的映像。  
  
-   可以先延後動作，再讓於電腦上使用閒置時間的服務執行該動作，以產生及安裝映像。  
  
-   已經排除影像失效的某些原因。  
  
 在 Windows 8 上，請參閱[原生映像工作](http://msdn.microsoft.com/library/9b1f7590-4e0d-4737-90ef-eaf696932afb)。  
  
 如需使用 Ngen.exe 和原生映像服務的詳細資訊，請參閱[原生映像服務][Native Image Service]。  
  
> [!NOTE]
>  您可以在[原生映像產生器 (Ngen.exe) 舊版語法](http://msdn.microsoft.com/library/5a69fc7a-103f-4afc-8ab4-606adcb46324)中找到 .NET Framework 1.0 和 1.1 版的 Ngen.exe 語法。  
  
 此工具會自動與 Visual Studio 一起安裝。 若要執行此工具，請使用 [開發人員命令提示字元] (或 Windows 7 中的 [Visual Studio 命令提示字元])。 如需詳細資訊，請參閱[命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)。  
  
 在命令提示字元下輸入下列命令：  
  
## <a name="syntax"></a>語法  
  
```  
ngen action [options]  
```  
  
```  
ngen /? | /help  
```  
  
## <a name="actions"></a>動作  
 下表顯示每個 `action` 的語法。 如需 `action` 個別部分的描述，請參閱[引數](#ArgumentTable)、[優先權層級](#PriorityTable)、[情節](#ScenarioTable)，以及[組態](#ConfigTable)表格。 [選項](#OptionTable)表格則描述 `options` 和說明參數。  
  
|動作|描述|  
|------------|-----------------|  
|`install` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`] [`/queue`[`:`{`1`&#124;`2`&#124;`3`}]]|產生組件的原生映像及其相依性，並在原生映像快取中安裝映像。<br /><br /> 如果已指定 `/queue`，原生映像服務的動作就會排入佇列。 預設優先權為 3。 請參閱[優先權層級](#PriorityTable)表格。|  
|`uninstall` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`]|從原生映像快取中刪除組件的原生映像和其相依性。<br /><br /> 若要解除安裝單一映像和其相依性，請使用安裝影像時所用的相同命令列引數。 **附註：**從 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 開始，不再支援 `uninstall`動作。*|  
|`update` [`/queue`]|更新已經變成無效的原生映像。<br /><br /> 如果已指定 `/queue`，原生映像服務的更新動作就會排入佇列。 更新動作一律會排在優先權 3，因此會在電腦為閒置時才執行。|  
|`display` [`assemblyName` &#124; `assemblyPath`]|顯示組件的原生映像狀態和其相依性。<br /><br /> 如果沒有提供任何引數，將顯示原生映像快取中的每個項目。|  
|`executeQueuedItems` [<code>1&#124;2&#124;3</code>]<br /><br /> -或-<br /><br /> `eqi` [1&#124;2&#124;3]|執行排入佇列的編譯工作。<br /><br /> 如果已指定優先權，就會執行具有較大或相同優先權的編譯工作。 如果沒有指定優先權，將會執行所有排入佇列的編譯工作。|  
|`queue` {`pause` &#124; `continue` &#124; `status`}|暫停原生映像服務，讓暫停的服務可繼續執行，或查詢服務的狀態。|  
  
<a name="ArgumentTable"></a>   
## <a name="arguments"></a>引數  
  
|引數|描述|  
|--------------|-----------------|  
|`assemblyName`|組件的完整顯示名稱。 例如，`"myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5"`。 **附註：**您可以提供組件的部分名稱 (例如 `myAssembly`) 以進行 `display` 和 `uninstall` 動作。 <br /><br /> 每一個 Ngen.exe 命令列只能指定一個組件。|  
|`assemblyPath`|組件的明確路徑。 您可以指定完整或相對路徑。<br /><br /> 如果指定檔案名稱但沒有指定路徑，則組件必須位於目前的目錄中。<br /><br /> 每一個 Ngen.exe 命令列只能指定一個組件。|  
  
<a name="PriorityTable"></a>   
## <a name="priority-levels"></a>優先權層級  
  
|優先權|描述|  
|--------------|-----------------|  
|`1`|立即產生並安裝原生映像，不等待閒置時間。|  
|`2`|產生並安裝原生映像，不等待閒置時間，但在完成所有優先權為 1 的操作 (及其相依性) 之後。|  
|`3`|當原生映像服務偵測到電腦閒置時安裝原生映像。 請參閱[原生映像服務][Native Image Service]。|  
  
<a name="ScenarioTable"></a>   
## <a name="scenarios"></a>案例  
  
|情節|描述|  
|--------------|-----------------|  
|`/Debug`|產生可以在偵錯工具下使用的原生映像。|  
|`/Profile`|產生可以在分析工具下使用的原生映像。|  
|`/NoDependencies`|產生指定的情節選項所需的最小數量原生映像。|  
  
<a name="ConfigTable"></a>   
## <a name="config"></a>組態  
  
|組態|描述|  
|-------------------|-----------------|  
|`/ExeConfig:` `exePath`|使用指定之可執行組件的組態。<br /><br /> Ngen.exe 繫結至相依性時，必須做出與載入器一樣的決定。 在執行階段載入共用元件時，如果使用 <xref:System.Reflection.Assembly.Load%2A> 方法，應用程式的組態檔就會判斷為共用元件載入的相依性，例如，載入的相依性版本。 `/ExeConfig` 參數會對 Ngen.exe 提供在執行階段時載入的相依性指引。|  
|`/AppBase:` `directoryPath`|在尋找相依性時，使用指定的目錄做為應用程式基底。|  
  
<a name="OptionTable"></a>   
## <a name="options"></a>選項  
  
|選項|描述|  
|------------|-----------------|  
|`/nologo`|隱藏 Microsoft 程式啟始資訊的顯示。|  
|`/silent`|隱藏成功訊息的顯示。|  
|`/verbose`|顯示用來偵錯的詳細資訊。 **注意：**由於作業系統限制的關係，這個選項在 Windows 98 和 Windows Millennium Edition 上不會顯示那麼多詳細資訊。|  
|`/help`, `/?`|顯示目前版本的命令語法和選項。|  
  
## <a name="remarks"></a>備註  
 若要執行 Ngen.exe，您必須具有系統管理員權限。  
  
> [!CAUTION]
>  請勿在不受完全信任的組件上執行 Ngen.exe。 從 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 開始，Ngen.exe 都以完全信任的方式來編譯組件，而且不再評估程式碼存取安全性 (CAS) 原則。  
  
 從 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 開始，以 Ngen.exe 產生的原生映像，不再載入至以部分信任執行的應用程式中。 而是會改為叫用 Just-In-Time (JIT) 編譯器。  
  
 Ngen.exe 會產生 `install` 動作的 `assemblyname` 引數所指定組件的原生映像和其所有相依性。 相依性是由組件資訊清單中的參考所決定。 唯一需要個別安裝相依性的狀況，是在應用程式使用反映將它載入時 (例如，藉由呼叫 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> 方法)。  
  
> [!IMPORTANT]
>  請勿對原生映像使用 <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> 方法。 使用這個方法載入的映像無法供執行內容中的其他組件使用。  
  
 Ngen.exe 會維護相依性的計數。 例如，假設 `MyAssembly.exe` 和 `YourAssembly.exe` 兩者都安裝在原生映像快取中，且兩者都有 `OurDependency.dll` 的參考。 如果 `MyAssembly.exe` 已解除安裝，則 `OurDependency.dll` 不會解除安裝。 只有在 `YourAssembly.exe` 也解除安裝時，才會將它移除。  
  
 如果正在全域組件快取中產生組件的原生映像，請指定它的顯示名稱。 請參閱 <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>。  
  
 Ngen.exe 產生的原生映像可以在應用程式定義域之間共用。 這表示您可以在需要跨應用程式定義域共用組件的應用程式案例中使用 Ngen.exe。 若要指定定義域中立性：  
  
-   將 <xref:System.LoaderOptimizationAttribute> 屬性套用至應用程式。  
  
-   當您建立新應用程式定義域的安裝資訊時，請設定 <xref:System.AppDomainSetup.LoaderOptimization%2A?displayProperty=nameWithType> 屬性。  
  
 將相同的組件載入多個應用程式定義域時，一律使用定義域中性程式碼。 如果原生映像在載入共用定義域之後載入未共用的應用程式定義域，就會無法使用。  
  
> [!NOTE]
>  無法卸載定義域中性程式碼，特別是在存取靜態成員時，效能可能會稍微變慢。  
  
 在＜備註＞一節中：  
  
-   [產生不同情節的映像](#Scenarios)  
  
-   [判斷使用原生映像的時機](#WhenToUse)  
  
    -   [改進記憶體使用](#Memory)  
  
    -   [應用程式啟動較快](#Startup)  
  
    -   [使用方式考量摘要](#UsageSummary)  
  
-   [組件基底位址的重要性](#BaseAddresses)  
  
-   [硬式繫結](#HardBinding)  
  
    -   [指定相依性的繫結提示](#DependencyHint)  
  
    -   [指定組件的預設繫結提示](#AssemblyHint)  
  
-   [延後處理](#Deferred)  
  
-   [原生映像和 JIT 編譯](#JITCompilation)  
  
    -   [無效的映像](#InvalidImages)  
  
-   [疑難排解](#Troubleshooting)  
  
    -   [組件繫結記錄檔檢視器](#Fusion)  
  
    -   [JITCompilationStart Managed 偵錯助理](#MDA)  
  
    -   [選擇不產生原生映像](#OptOut)  
  
<a name="Scenarios"></a>   
## <a name="generating-images-for-----different-scenarios"></a>產生不同情節的映像  
 當您產生組件的原生映像後，執行階段會在每次執行組件時自動嘗試找出並且使用這個原生映像。 視使用情節而定，可以產生多個映像。  
  
 例如，如果您是在偵錯或分析情節中執行組件，則執行階段會尋找以 `/Debug` 或 `/Profile` 選項產生的原生映像。 如果執行階段找不到符合的原生映像，就會還原成標準 JIT 編譯。 偵錯原生映像的唯一方法是以 `/Debug` 選項建立原生映像。  
  
 `uninstall` 動作也會辨識情節，因此您可以解除安裝所有情節或只解除安裝選取的情節。  
  
<a name="WhenToUse"></a>   
## <a name="determining-when-to-use-native-images"></a>判斷使用原生映像的時機  
 原生映像可提供兩個區域的效能改進：改進記憶體使用和減少啟動時間。  
  
> [!NOTE]
>  原生映像的效能取決於下列數個讓分析更加困難的因素：程式碼和資料存取模式、跨模組界限中產生多少個呼叫以及其他應用程式已載入多少個相依性等等。 判斷原生映像是否對您的應用程式帶來好處的唯一方法是在主要部署情節中，仔細地度量效能。  
  
<a name="Memory"></a>   
### <a name="improved-memory-use"></a>改進記憶體使用  
 在處理序之間共用程式碼時，原生映像可以顯著地改進記憶體使用。 原生映像是 Windows PE 檔案，因此多個處理序可以共用 .dll 檔案的單一複本；相反地，JIT 編譯器產生的機器碼則會存放在專用記憶體中，並且無法共用。  
  
 在終端機服務下執行的應用程式也可以從共用字碼頁獲益。  
  
 此外，不載入 JIT 編譯器可為每個應用程式執行個體節省固定量的記憶體。  
  
<a name="Startup"></a>   
### <a name="faster-application-startup"></a>應用程式啟動較快  
 以 Ngen.exe 先行編譯組件可以改進某些應用程式的啟動時間。 一般來說，在應用程式共用元件組件時就會獲益，這是因為啟動第一個應用程式之後，就已對後續的應用程式載入共用的元件。 冷啟動 (必須從硬碟載入應用程式中的所有組件) 的優點沒有像從原生映像中載入那麼多，因為硬碟存取時間就具決定性。  
  
 硬式繫結會影響啟動時間，這是因為硬式繫結至主應用程式組件的所有映像都必須在同時間載入。  
  
> [!NOTE]
>  在 [!INCLUDE[net_v35SP1_long](../../../includes/net-v35sp1-long-md.md)] 之前，您應該將共用、強式名稱的元件放在全域組件快取中，因為載入器會針對不在全域組件快取中的強式名稱組件執行額外驗證，進而有效地消除使用原生映像所取得的任何啟動時間改進。 在 [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] 中引入的最佳化移除額外的驗證。  
  
<a name="UsageSummary"></a>   
### <a name="summary-of-usage-considerations"></a>使用方式考量摘要  
 下列一般考量和應用程式考量可以幫助您決定是否要進行評估應用程式的原生映像：  
  
-   原生映像的載入速度比 MSIL 快，因為原生映像可以減少許多不必要的啟動活動 (例如 JIT 編譯和類型安全驗證)。  
  
-   由於不需要 JIT 編譯器，原生映像只需要較小的初始工作集。  
  
-   原生映像可啟用處理序之間的程式碼共用。  
  
-   原生映像所需的硬碟空間比 MSIL 組件更多，而且可能需要相當長的時間才能產生。  
  
-   必須維護原生映像。  
  
    -   在為原始組件或它的其中一個相依性提供服務時，需要重新產生影像。  
  
    -   單一組件可能需要多個原生映像，以供不同的應用程式或不同的情節使用。 例如，兩個應用程式中的組態資訊可能會為相同的相依組件產生不同的繫結決策。  
  
    -   原生映像必須由系統管理員產生，也就是來自系統管理員 (Administrator) 群組中的 Windows 帳戶。  
  
 除了這些一般考量之外，在判斷原生映像是否可能提供效能優勢時，應用程式的本質也必須列入考慮：  
  
-   如果應用程式是在使用許多共用元件的環境中執行，原生映像可允許多個處理序共用元件。  
  
-   如果您的應用程式使用多個應用程式定義域，原生映像就可讓字碼頁跨定義域共用。  
  
    > [!NOTE]
    >  在 .NET Framework 1.0 和 1.1 版中，無法跨應用程式定義域共用原生映像。 這不是 2.0 (含) 以後版本的情況。  
  
-   如果將在終端伺服器下執行應用程式，則原生映像允許共用字碼頁。  
  
-   大型應用程式通常可以透過編譯取得原生映像的優勢。 小型應用程式通常就沒有差別。  
  
-   若是長時間執行的應用程式，執行階段 JIT 編譯的執行效能要比原生映像稍微好一點  (硬式繫結在某種程度上可稍微緩和這個效能差異)。  
  
<a name="BaseAddresses"></a>   
## <a name="importance-of-assembly-base-addresses"></a>組件基底位址的重要性  
 由於原生映像是 Windows PE 檔案，因此和其他可執行檔一樣會有重定基底的問題。 重新配置所耗用的效能甚至會比使用硬式繫結來得多。  
  
 若要設定原生映像的基底位址 (Base Address)，請使用適當的編譯器選項以設定組件的基底位址。 Ngen.exe 會對原生映像使用此基底位址。  
  
> [!NOTE]
>  原生映像會比它們的建立來源 Managed 組件更大。 必須計算基底位址是否允許較大的大小。  
  
 您可以使用 dumpbin.exe 這類工具，檢視原生映像偏好的基底位址。  
  
<a name="HardBinding"></a>   
## <a name="hard-binding"></a>硬式繫結  
 硬式繫結會增加原生映像的輸送量，並降低工作集的大小。 硬式繫結的缺點是載入組件時，必須載入所有硬式繫結至組件的映像。 這樣會大量增加大型應用程式的啟動時間。  
  
 硬式繫結適用於在所有應用程式的重要效能情節中載入的相依性。 使用原生映像時，仔細的效能度量是唯一能判斷硬式繫結是否改進您應用程式效能的方法。  
  
 <xref:System.Runtime.CompilerServices.DependencyAttribute> 和 <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> 屬性可讓您對 Ngen.exe 提供硬式繫結提示。  
  
> [!NOTE]
>  這些屬性是 Ngen.exe 的提示，而非命令。 使用這些屬性不會保證執行硬式繫結。 這些屬性的意義在以後的版本中可能會變更。  
  
<a name="DependencyHint"></a>   
### <a name="specifying-a-binding-hint-for-a-dependency"></a>指定相依性的繫結提示  
 將 <xref:System.Runtime.CompilerServices.DependencyAttribute> 套用至組件，表示可能會載入指定的相依性組件。 <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> 表示硬式繫結適用，<xref:System.Runtime.CompilerServices.LoadHint.Default> 表示應該使用相依性的預設值，而 <xref:System.Runtime.CompilerServices.LoadHint.Sometimes> 表示硬式繫結不適用。  
  
 在下列程式碼中，示範具有兩個相依性的組件屬性。 第一個相依性 (Assembly1) 是硬式繫結的適當候選，但第二個 (Assembly2) 則不是。  
  
```vb  
Imports System.Runtime.CompilerServices  
<Assembly:DependencyAttribute("Assembly1", LoadHint.Always)>  
<Assembly:DependencyAttribute("Assembly2", LoadHint.Sometimes)>  
```  
  
```csharp  
using System.Runtime.CompilerServices;  
[assembly:DependencyAttribute("Assembly1", LoadHint.Always)]  
[assembly:DependencyAttribute("Assembly2", LoadHint.Sometimes)]  
```  
  
```cpp  
using namespace System::Runtime::CompilerServices;  
[assembly:DependencyAttribute("Assembly1", LoadHint.Always)];  
[assembly:DependencyAttribute("Assembly2", LoadHint.Sometimes)];  
```  
  
 組件名稱不包含副檔名。 可以使用顯示名稱。  
  
<a name="AssemblyHint"></a>   
### <a name="specifying-a-default-binding-hint-for-an-assembly"></a>指定組件的預設繫結提示  
 只有其中具有組件相依性的應用程式將立即且經常使用組件時，才會需要用到預設繫結提示。 將具有 <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> 的 <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> 套用至這類組件，以指定應該使用硬式繫結。  
  
> [!NOTE]
>  沒有理由要將 <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> 套用至不屬於這個分類的 .dll 組件，因為套用具有非 <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> 值的屬性，其作用就和完全不套用屬性一樣。  
  
 Microsoft 使用 <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> 指定硬式繫結是 .NET Framework 中極少數組件的預設值，例如 mscorlib.dll。  
  
<a name="Deferred"></a>   
## <a name="deferred-processing"></a>延後處理  
 對極大型的應用程式產生原生映像會需要相當長的時間。 同樣地，變更共用元件或變更電腦設定可能都需要更新許多原生映像。 `install` 和 `update` 動作具有 `/queue` 選項，可將原生映像服務的延後執行作業加入佇列。 此外，Ngen.exe 具有提供部分服務控制權的 `queue` 和 `executeQueuedItems` 動作。 如需詳細資訊，請參閱[原生映像服務][Native Image Service]。  
  
<a name="JITCompilation"></a>   
## <a name="native-images-and-jit-compilation"></a>原生映像和 JIT 編譯  
 如果 Ngen.exe 在組件上遇到它無法產生的任何方法，就會將其從原生映像排除。 當執行階段執行這個組件時，它將會對這些沒有包括在原生映像中的方法還原成 JIT 編譯。  
  
 此外，如果已升級組件，或者映像因任何原因而失效，都不會使用原生映像。  
  
<a name="InvalidImages"></a>   
### <a name="invalid-images"></a>無效的映像  
 當您使用 Ngen.exe 建立組件的原生映像時，輸出會依您指定的命令列選項和電腦上的特定設定而有所不同。 這些設定包括下列各項：  
  
-   .NET Framework 的版本。  
  
-   如果是從 Windows 9x 系列變更到 Windows NT 系列，則表示作業系統的版本。  
  
-   組件的確切識別 (重新編譯會變更識別)。  
  
-   這個組件所參考之所有組件的確切識別 (重新編譯會變更識別)。  
  
-   安全性因素。  
  
 Ngen.exe 會在產生原生映像時記錄這項資訊。 當您執行組件時，執行階段會尋找由符合電腦目前執行環境之選項和設定所產生的原生映像。 如果找不到符合的原生映像，執行階段就會還原成組件的 JIT 編譯。 下列對電腦設定和環境的變更會使原生映像變成無效：  
  
-   .NET Framework 的版本。  
  
     如果您對 .NET Framework 套用更新，則使用 Ngen.exe 建立的所有原生映像都會變成無效。 因此，.NET Framework 的所有更新都會執行 `Ngen Update` 命令，以確保重新產生所有的原生映像。 .NET Framework 會自動為它所安裝的 .NET Framework 程式庫建立新的原生映像。  
  
-   如果是從 Windows 9x 系列變更為 Windows NT 系列，則表示作業系統的版本。  
  
     例如，如果電腦上執行的作業系統版本從 Windows 98 變更為 Windows XP，則存放在原生映像快取中的所有原生映像都會變成無效。 但是，如果作業系統從 Windows 2000 變更為 Windows XP，則映像不會失效。  
  
-   組件的確切識別。  
  
     如果您重新編譯某個組件，這個組件對應的原生映像會變成無效。  
  
-   這個組件所參考之任一組件的確切識別。  
  
     如果您更新 Managed 組件，所有直接或間接以該組件為依據的原生映像都會變成無效，必須重新產生。 這其中包括一般性的參考和硬式繫結的相依性。 每當套用軟體更新時，安裝程式都應執行 `Ngen Update` 命令，以確保重新產生所有相依的原生映像。  
  
-   安全性因素。  
  
     變更電腦安全性原則，以限制先前對組件允許的使用權限，會使該組件先前已編譯的原生映像變成無效。  
  
     如需 Common Language Runtime 如何管理程式碼存取安全性，以及如何使用權限的詳細資訊，請參閱[程式碼存取安全性](../../../docs/framework/misc/code-access-security.md)。  
  
<a name="Troubleshooting"></a>   
## <a name="troubleshooting"></a>疑難排解  
 下列疑難排解主題可讓您查看正在使用的原生映像以及您的應用程式不能使用的原生映像、判斷 JIT 編譯器開始編譯方法的時機，以及顯示如何選擇不編譯所指定方法的原生映像。  
  
<a name="Fusion"></a>   
### <a name="assembly-binding-log-viewer"></a>組件繫結記錄檔檢視器  
 若要確認您的應用程式正在使用原生映像，可以使用 [Fuslogvw.exe (組件繫結記錄檔檢視器)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md)。 在繫結記錄檔檢視器視窗的 [記錄檔類別] 方塊中，選取 [原生映像]。 Fuslogvw.exe 會提供為何會拒絕原生映像的詳細資訊。  
  
<a name="MDA"></a>   
### <a name="the-jitcompilationstart-managed-debugging-assistant"></a>JITCompilationStart Managed 偵錯助理  
 您可以使用 [jitCompilationStart](../../../docs/framework/debug-trace-profile/jitcompilationstart-mda.md) Managed 偵錯助理 (MDA)，判斷 JIT 編譯器開始編譯函式的時間。  
  
<a name="OptOut"></a>   
### <a name="opting-out-of-native-image-generation"></a>選擇不產生原生映像  
 在某些情況下，NGen.exe 可能無法產生特定方法的原生映像，或者，您可能會偏好使用 JIT 編譯的方法，而不是編譯成原生映像。 在此情況下，您可以使用 `System.Runtime.BypassNGenAttribute` 屬性，防止 NGen.exe 產生特定方法的原生映像。 如果您不想要將方法的程式碼包含在原生映像中，則必須將此屬性個別套用至這類方法。 NGen.exe 會辨識此屬性，而且不會在原生影像中產生對應方法的程式碼。  
  
 不過，請注意，`BypassNGenAttribute` 未定義為 .NET Framework 類別庫中的類型。 若要取用您程式碼中的屬性，您必須先定義它，如下所示︰  
  
 [!code-csharp[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#1)]
 [!code-vb[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#1)]  
  
 您接著可以根據方法來套用屬性。 下列範例指示原生映像產生器不應該產生 `ExampleClass.ToJITCompile` 方法的原生影像。  
  
 [!code-csharp[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#2)]
 [!code-vb[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#2)]  
  
## <a name="examples"></a>範例  
 下列命令會在目前的目錄中產生 `ClientApp.exe` 的原生映像，並在原生映像快取中安裝映像。 如果組件有組態檔，Ngen.exe 就會使用它。 此外，會針對 `ClientApp.exe` 參考的任何 .dll 檔案產生原生映像。  
  
```  
ngen install ClientApp.exe  
```  
  
 使用 Ngen.exe 安裝的映像也稱為根 (Root)。 根可以是應用程式或共用元件。  
  
 下列命令會對指定路徑的 `MyAssembly.exe` 產生原生映像。  
  
```  
ngen install c:\myfiles\MyAssembly.exe  
```  
  
 尋找組件和它們的相依性時，Ngen.exe 使用的探查邏輯和通用語言執行平台所使用的一樣。 根據預設，包含 `ClientApp.exe` 的目錄會當做應用程式基底目錄使用，並且會在這個目錄中開始所有組件探查。 您可以使用 `/AppBase` 選項覆寫這個行為。  
  
> [!NOTE]
>  這是 .NET Framework 1.0 和 1.1 版之 Ngen.exe 行為的變更，其中的應用程式基底會設為目前的目錄。  
  
 組件可以擁有相依性，而不含參考，例如，當組件在使用 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> 方法載入 .dll 檔時。 您可以利用 `/ExeConfig` 選項，針對使用應用程式組件之組態資訊的這種 .dll 檔建立原生映像。 下列命令會針對使用 `MyLib.dll,` 組態資訊的 `MyApp.exe` 產生原生映像。  
  
```  
ngen install c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe  
```  
  
 在移除應用程式時，不會移除以這種方式所安裝的組件。  
  
 若要解除安裝相依性，請使用安裝時所用的相同命令列選項。 下列命令會解除安裝上一個範例的 `MyLib.dll`。  
  
```  
ngen uninstall c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe  
```  
  
 若要在全域組件快取中建立組件的原生映像，請使用組件的顯示名稱。 例如:   
  
```  
ngen install "ClientApp, Version=1.0.0.0, Culture=neutral,   
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL"  
```  
  
 NGen.exe 會對所安裝的每個情節產生不同的映像集。 例如，下列命令會安裝一般作業的完整原生映像集，再安裝另一個完整集供偵錯使用，然後針對程式碼剖析安裝第三個完整集：  
  
```  
ngen install MyApp.exe  
ngen install MyApp.exe /debug  
ngen install MyApp.exe /profile  
```  
  
### <a name="displaying-the-native-image-cache"></a>顯示原生映像快取  
 一旦原生映像安裝在快取中，即可使用 Ngen.exe 顯示它們。 下列命令會顯示原生映像快取中的所有原生映像。  
  
```  
ngen display  
```  
  
 `display` 動作會先列出所有根組件，接下來是電腦上所有原生映像的清單。  
  
 使用組件的簡單名稱，僅顯示該組件的資訊。 下列命令會顯示原生映像快取中所有符合部分名稱 `MyAssembly` 的原生映像、它們的相依性和所有在 `MyAssembly` 上具有相依性的根：  
  
```  
ngen display MyAssembly  
```  
  
 在升級共用元件之後，判斷 `update` 動作所造成的影響時，了解哪些根會相依於共用元件組件將很有幫助。  
  
 如果指定組件的副檔名，您必須指定路徑或從包含組件的目錄執行 Ngen.exe：  
  
```  
ngen display c:\myApps\MyAssembly.exe  
```  
  
 下列命令會顯示原生映像快取中名稱為 `MyAssembly` 且版本為 1.0.0.0 的所有原生映像。  
  
```  
ngen display "myAssembly, version=1.0.0.0"  
```  
  
### <a name="updating-images"></a>更新映像  
 通常會在升級共用元件之後更新映像。 若要更新已變更或已變更其相依性的所有原生映像，請使用 `update` 動作且不搭配任何引數。  
  
```  
ngen update  
```  
  
 更新所有映像可能是耗時的處理。 您可以使用 `/queue` 選項，依原生映像服務將要執行的更新加入佇列。 如需 `/queue` 選項和安裝優先權的詳細資訊，請參閱[原生映像服務][Native Image Service]。  
  
```  
ngen update /queue  
```  
  
### <a name="uninstalling-images"></a>解除安裝映像  
 Ngen.exe 會維護相依性清單，因此只有當相依於共用元件的所有組件已移除時，才會移除共用元件。 此外，如果共用元件已安裝為根，則不會將它移除。  
  
 下列命令會解除安裝根 `ClientApp.exe` 的所有情節：  
  
```  
ngen uninstall ClientApp  
```  
  
 `uninstall` 動作可以用來移除特定的情節。 下列命令會解除安裝 `ClientApp.exe` 的所有偵錯情節：  
  
```  
ngen uninstall ClientApp /debug  
```  
  
> [!NOTE]
>  解除安裝 `/debug` 情節不會解除安裝同時包含 `/profile` 和 `/debug.` 的情節。  
  
 下列命令會解除安裝 `ClientApp.exe` 特定版本的所有情節：  
  
```  
ngen uninstall "ClientApp, Version=1.0.0.0"  
```  
  
 下列命令會解除安裝 `"ClientApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL",` 的所有情節，或僅解除安裝該組件的偵錯情節：  
  
```  
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,   
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL"  
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,   
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL" /debug  
```  
  
 搭配使用 `install` 動作時，提供副檔名需要從含有組件的目錄執行 Ngen.exe 或指定完整路徑。  
  
 如需與原生映像服務相關的範例，請參閱[原生映像服務][Native Image Service]。  
  
## <a name="native-image-task"></a>原生映像工作  
 原生映像工作是產生及維護原生映像的 Windows 工作。 原生映像工作會自動為受支援的案例產生及回收原生映像。 (請參閱[建立原生映像](http://msdn.microsoft.com/library/2bc8b678-dd8d-4742-ad82-319e9bf52418))。它也可以讓安裝程式使用 [Ngen.exe (原生映像產生器)](../../../docs/framework/tools/ngen-exe-native-image-generator.md)，在延後的時間建立及更新原生映像。  
  
 針對電腦上支援的每個 CPU 架構，會各註冊一次原生映像工作，以允許針對以各架構為目標的應用程式進行編譯：  
  
|工作名稱|32 位元電腦|64 位元電腦|  
|---------------|----------------------|----------------------|  
|NET Framework NGEN v4.0.30319|[是]|[是]|  
|NET Framework NGEN v4.0.30319 64|否|[是]|  
  
 在 Windows 8 或更新版本上執行時，可在 .NET Framework 4.5 和更新版本中使用原生映像工作。 在舊版 Windows 中，.NET Framework 會使用 [原生映像服務][Native Image Service]。  
  
### <a name="task-lifetime"></a>工作存留期  
 一般而言，Windows 工作排程器會在每天晚上電腦閒置時，開始原生映像工作。 此工作會檢查應用程式安裝程式佇列的任何延後工作、任何延後的原生映像更新要求，以及任何自動建立映像的工作。 此工作會完成未完成的工作項目，然後才關閉。 如果電腦在工作執行時停止閒置，該工作就會停止。  
  
 您也可以透過工作排程器 UI，或是透過手動呼叫 NGen.exe，以手動啟動原生映像工作。 如果是透過上述其中一種方法來啟動工作，即使電腦不再閒置，還是會繼續執行該工作。 使用 NGen.exe 手動建立的映像會列為優先順序，以為應用程式安裝程式啟用可預期的行為。  
  
## <a name="native-image-service"></a>原生映像服務  
 原生映像服務是產生及維護原生映像的 Windows 服務。 原生映像服務可讓開發人員將原生映像的安裝和更新延後到電腦閒置時的時段。  
  
 一般來說，會由安裝程式 (installer) 為應用程式或更新啟始原生映像服務。 針對優先順序 3 的動作，此服務會在電腦閒置期間執行。 此服務會儲存其狀態，而且必要時，可以在多次重新開機後再繼續。 多個影像編譯可排入佇列。  
  
 此服務也會與手動 Ngen.exe 命令互動。 手動命令優先於背景活動。  
  
> [!NOTE]
>  在 Windows Vista 上，為原生映像服務顯示的名稱是 "Microsoft.NET Framework NGEN v2.0.50727_X86" 或 "Microsoft.NET Framework NGEN v2.0.50727_X64"。 在所有舊版 Microsoft Windows 上，名稱為「.NET 執行階段最佳化服務  v2.0.50727_X86」或「.NET 執行階段最佳化服務  v2.0.50727_X64」。  
  
### <a name="launching-deferred-operations"></a>啟動延後的作業  
 在開始安裝或升級之前，建議先暫停服務。 這樣可以確保當安裝程式正在複製檔案或是在全域組件快取中放置組件時，該服務不會執行。 下列 Ngen.exe 命令列會暫停服務：  
  
```  
ngen queue pause  
```  
  
 當所有延後的作業都排入佇列時，下列命令可讓服務繼續：  
  
```  
ngen queue continue  
```  
  
 若要在安裝新應用程式或是更新共用元件時，延後產生原生映像，請使用 `/queue` 選項搭配 `install` 或 `update` 動作。 下列 Ngen.exe 命令列會為共用元件安裝原生映像，並針對可能受影響的所有根目錄執行更新：  
  
```  
ngen install MyComponent /queue  
ngen update /queue  
```  
  
 `update` 動作會重新產生已經失效的所有原生映像，而不只是使用 `MyComponent` 的那些原生映像。  
  
 如果您的應用程式包含許多根目錄，您可以控制延後動作的優先順序。 下列命令會將三個根目錄的安裝排入佇列。 會先安裝 `Assembly1`，而不會等到閒置時間。 `Assembly2` 也是不會等到閒置時間，但要等到所有優先權 1 動作都完成之後才安裝。 `Assembly3` 則會在服務偵測到電腦閒置時安裝。  
  
```  
ngen install Assembly1 /queue:1  
ngen install Assembly2 /queue:2  
ngen install Assembly3 /queue:3  
```  
  
 您可以使用 `executeQueuedItems` 動作，強制佇列的動作同步執行。 如果您提供選擇性的優先權，這個動作只會影響具有相等或較低優先權的佇列動作。 預設優先權為 3，因此下列 Ngen.exe 命令會立即處理所有佇列的動作，並且在完成之前都不會傳回：  
  
```  
ngen executeQueuedItems  
```  
  
 同步命令是由 Ngen.exe 執行，而且不會使用原生映像服務。 您可以在原生映像服務執行時，使用 Ngen.exe 來執行動作。  
  
### <a name="service-shutdown"></a>服務關閉  
 在執行包含 `/queue` 選項的 Ngen.exe 命令來啟始服務之後，服務會在背景執行，直到所有動作完成為止。 此服務會儲存其狀態，因此必要時，可以在多次重新開機後再繼續。 當服務偵測到已經沒有動作佇列時，會重設其狀態，使其不會在下次電腦開機時重新啟動，然後將服務本身關閉。  
  
### <a name="service-interaction-with-clients"></a>服務與用戶端互動  
 在 .NET Framework 2.0 版中，與原生映像服務的唯一互動，是透過命令列工具 Ngen.exe。 在安裝指令碼中使用命令列工具，將原生映像服務的動作加入佇列中，並與服務互動。  
  
## <a name="see-also"></a>請參閱  
 [工具](../../../docs/framework/tools/index.md)  
 [Managed 執行程序](../../../docs/standard/managed-execution-process.md)  
 [執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

[Native Image Service]: #native-image-service

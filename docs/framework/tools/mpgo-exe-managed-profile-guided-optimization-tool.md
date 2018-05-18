---
title: Mpgo.exe (Managed 特性指引最佳化工具)
ms.date: 03/30/2017
helpviewer_keywords:
- Mpgo.exe
- training scenarios, generating profiles with
- Managed Profile Guided Optimization Tool
- Ngen.exe
- Ngen.exe, profilers and native images
ms.assetid: f6976502-a000-4fbe-aaf5-a7aab9ce4ec2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 42e1fb080ac0af34c621cef3a991cad7bcf603ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="mpgoexe-managed-profile-guided-optimization-tool"></a>Mpgo.exe (Managed 特性指引最佳化工具)
Managed 特性指引最佳化工具 (Mpgo.exe) 是一項命令列工具，它會使用常見的使用者情節最佳化[原生映像產生器 (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) 所建立的原生映像組件。 此工具可讓您執行產生分析資料的訓練情節。 [原生映像產生器 (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) 會使用這項資料最佳化其產生的原生映像應用程式組件。 訓練情節是指嘗試執行應用程式的預期使用方式。 Mpgo.exe 會隨 Visual Studio Ultimate 2012 (含) 以後版本提供。 從 [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)] 開始，您也可以使用 Mpgo.exe 最佳化 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式。  
  
 特性指引最佳化會從訓練情節收集資料並使用該資料最佳化原生映像的配置，藉此改善應用程式啟動時間、記憶體使用率 (工作組大小) 以及輸送量。  
  
 當 Intermediate Language (IL) 組件的啟動時間和工作組大小發生效能問題時，建議您先使用 Ngen.exe 消除 Just-in-Time (JIT) 編譯成本和促進程式碼共用。 如果您需要進一步改進，可以使用 Mpgo.exe 進一步最佳化您的應用程式。 您可以使用非最佳化原生映像組件的效能資料做為評估效能改善的基準。 使用 Mpgo.exe 能夠縮短冷啟動時間和縮小工作組大小。 Mpgo.exe 會將資訊加入至 Ngen.exe 用來建立最佳化原生映像組件的 IL 組件。 如需詳細資訊，請參閱 .NET 部落格中的 [Improving Launch Performance for your Desktop Applications](http://go.microsoft.com/fwlink/p/?LinkId=248943) (改善桌面應用程式的啟動效能) 文章。  
  
 此工具會自動與 Visual Studio 一起安裝。 若要執行這項工具，請使用具有系統管理員認證的開發人員命令提示字元 (或 Windows 7 中的 Visual Studio 命令提示字元)，然後在命令提示字元中輸入下列內容。 如需詳細資訊，請參閱[命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)。  
  
 針對桌面應用程式：  
  
```  
mpgo –Scenario <command> [-Import <directory>] –AssemblyList <assembly1>  <assembly2> ... -OutDir <directory> [options]  
```  
  
 針對 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式：  
  
## <a name="syntax"></a>語法  
  
```  
mpgo –Scenario <packageName> -AppID <appId> -Timeout <seconds>  
```  
  
#### <a name="parameters"></a>參數  
 Mpgo.exe 的所有引數都不區分大小寫。 命令前面會加上虛線。  
  
> [!NOTE]
>  您可以使用 `–Scenario` 或 `–Import` 做為必要的命令，但兩者不能同時使用。 如果您指定 `–Reset` 選項，將不會使用任何必要參數。  
  
|必要參數|描述|  
|------------------------|-----------------|  
|`-Scenario` \<*命令*><br /><br /> -或-<br /><br /> `-Scenario` \<*套件名稱*><br /><br /> -或-<br /><br /> `-Import` \<*目錄*>|若是桌面應用程式，請使用 `–Scenario` 指定執行您要最佳化之應用程式的命令，包括任何命令列引數。 如果 *「命令」* 指定的路徑包含空格，請在前後加上三組雙引號。例如：`mpgo.exe -scenario """C:\My App\myapp.exe""" -assemblylist """C:\My App\myapp.exe""" -outdir "C:\optimized files"`。 不使用雙引號。如果 *「命令」* 包含空格就無法正確運作。<br /><br /> -或-<br /><br /> 若是 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式，請使用 `–Scenario` 來指定要產生其設定檔資訊的套件。 如果您指定套件顯示名稱或套件系列名稱而不是完整套件名稱，Mpgo.exe 在只有一個套件相符的情況下，將選取與您所提供名稱相符的套件。 如果有多個套件與指定的名稱相符，Mpgo.exe 將會提示您選擇一個套件。<br /><br /> -或-<br /><br /> 使用 `-Import` 可指定應該使用先前最佳化之組件的最佳化資料來最佳化 `-AssemblyList` 中的組件。 *「目錄」* 可指定包含先前最佳化之檔案的目錄。 `–AssemblyList` 或 `–AssemblyListFile` 中指定的組件是新版組件，其將使用匯入檔案的資料進行最佳化。 使用舊版組件的最佳化資料可讓您最佳化新版組件，而不需重新執行情節。  不過，如果匯入的組件和目標組件包含的程式碼相當不同，則最佳化資料將沒有作用。 在 `–AssemblyList` 或 `–AssemblyListFile` 中指定的組件名稱，必須出現在 `–Import`*目錄* 所指定的目錄中。 如果 *「目錄」* 指定的路徑包含空格，請在前後加上三組雙引號。<br /><br /> 您必須指定 `–Scenario` 或 `–Import`，但兩者不能同時指定。|  
|`-OutDir` \<*目錄*>|放置最佳化組件的目錄。 如果輸出目錄資料夾中已有組件，則會建立新的複本，並將索引編號附加至其名稱，例如： *組件名稱*-1.exe。 如果 *「目錄」* 指定的路徑包含空格，請在前後加上雙引號。|  
|`-AssemblyList` \<*組件 1 組件 2 ...*><br /><br /> -或-<br /><br /> `-AssemblyListFile` \<*檔案*>|您要收集其相關設定檔資訊的空格分隔組件清單 (包括 .exe 和 .dll 檔)。 您可以指定 `C:\Dir\*.dll` 或 `*.dll`以選取指定或目前工作目錄中的所有組件。 如需詳細資訊，請參閱＜備註＞一節。<br /><br /> -或-<br /><br /> 包含您要收集其相關設定檔資訊之組件清單的文字檔，每行列出一個組件。 如果組件名稱開頭是連字號 (-)，請使用組件檔清單或重新命名組件。|  
|`-AppID` \<*應用程式識別碼*>|所指定套件中的應用程式 ID。 如果您使用萬用字元 (\*)，Mpgo.exe 將嘗試列舉套件中的 AppID，如果失敗則會返回 \<套件系列名稱>!App。 如果您指定的字串前面加上驚嘆號 (!)，Mpgo.exe 將串連套件系列名稱與提供的引數。|  
|`-Timeout` \<*秒*>|在應用程式結束之前允許 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式執行的時間長度。|  
  
|選擇性參數|描述|  
|------------------------|-----------------|  
|`-64bit`|檢測 64 位元系統的組件。  即使您的組件本身宣告為 64 位元，您仍必須為 64 位元組件指定此參數。|  
|`-ExeConfig` \<*檔案名稱*>|指定您的情節用來提供版本和載入器資訊的組態檔。|  
|`-f`|在二進位組件中強制包含分析資料，即使組件已簽署也一樣。  如果組件已簽署，則必須重新簽署，否則，組件將無法載入及執行。|  
|`-Reset`|重設環境，以確保中止的程式碼剖析工作階段不會影響您的組件，然後退出。 根據預設，在程式碼剖析工作階段之前與之後，環境都會重設。|  
|`-Timeout` \<*時間 (秒)*>|以秒為單位指定程式碼剖析期間。 使用比您觀察所得的 GUI 應用程式啟動時間稍微長一點的值。 在逾時期間結束時，雖然應用程式繼續執行，但是會記錄分析資料。 如果您未設定此選項，程式碼剖析將會繼續，直到應用程式關閉為止，而且此時才會記錄資料。|  
|`-LeaveNativeImages`|指定執行情節之後不應移除檢測的原生映像。 此選項主要是在您要取得針對執行的情節指定的應用程式時使用。 它會防止 Mpgo.exe 後續執行後重新建立原生映像。 如果您指定此選項，當您完成執行應用程式時，可能會有失去關聯的原生映像留在快取中。 在這種情況下，請使用相同的案例與組件清單執行 Mpgo.exe，並使用 `–RemoveNativeImages` 參數移除這些原生映像。|  
|`-RemoveNativeImages`|從已指定 `–LeaveNativeImages` 的回合進行清理。 如果指定了 `-RemoveNativeImages`，Mpgo.exe 就會忽略除了 `-64bit` 和 `–AssemblyList` 以外的所有引數，並會在移除所有已檢測的原生映像之後結束。|  
  
## <a name="remarks"></a>備註  
 您可以在命令列上多次使用 `–AssemblyList` 和 `- AssemblyListFile`。  
  
 如果您在指定組件時未指定完整路徑名稱，Mpgo.exe 將在目前目錄中尋找。 如果您指定了不正確的路徑，Mpgo.exe 就會顯示錯誤訊息，但仍繼續產生其他組件的資料。 如果您指定的組件不是在訓練情節期間載入，則不會產生該組件的訓練資料。  
  
 如果清單中的某個組件位於全域組件快取中，則不會更新該組件使其包含設定檔資訊。  請從全域組件快取中將它移除，以便收集設定檔資訊。  
  
 建議您只對大型 Managed 應用程式使用 Ngen.exe 和 Mpgo.exe，因為預先編譯原生映像的優點通常是在執行階段消除大量 JIT 編譯時才會看見。 在不會耗用太多工作組的 "Hello World" 樣式應用程式上執行 Mpgo.exe 不會提供任何好處，Mpgo.exe 甚至可能無法成功收集分析資料。  
  
> [!NOTE]
>  不建議您將 Ngen.exe 和 Mpgo.exe 用於 ASP.NET 應用程式和 Windows Communication Foundation (WCF) 服務。  
  
## <a name="to-use-mpgoexe"></a>若要使用 Mpgo.exe  
  
1.  使用已安裝 Visual Studio Ultimate 2012 和您的應用程式的電腦。  
  
2.  以系統管理員身分執行 Mpgo.exe 及必要的參數。  請參閱下一節了解範例命令。  
  
     最佳化中繼語言 (IL) 組件會建立在 `–OutDir` 參數所指定的資料夾中 (在範例中，此為 `C:\Optimized` 資料夾)。  
  
3.  將 Ngen.exe 使用的 IL 組件取代為新的 IL 組件，該組件包含 `–OutDir` 所指定之目錄中的設定檔資訊。  
  
4.  應用程式設定 (使用 Mpgo.exe 提供的映像) 將安裝最佳化的原生映像。  
  
## <a name="suggested-workflow"></a>建議的工作流程  
  
1.  使用 Mpgo.exe 與 `–Scenario` 參數建立一組最佳化的 IL 組件。  
  
2.  將最佳化的 IL 組件簽入原始檔控制中。  
  
3.  在建置流程中，呼叫 Mpgo.exe 並使用 `–Import` 參數做為建置後步驟，以產生要傳遞至 Ngen.exe 的最佳化 IL 映像。  
  
 這個程序可確保所有組件都擁有最佳化資料。 如果您經常簽入更新的最佳化組件 (步驟 1 和 2)，則產品開發期間的整體效能數字將會更一致。  
  
## <a name="using-mpgoexe-from-visual-studio"></a>從 Visual Studio 使用 Mpgo.exe  
 您可以從 Visual Studio 執行 Mpgo.exe (請參閱[如何：指定建置事件 (C#)](http://msdn.microsoft.com/library/b4ce1ad9-5215-4b6f-b6a2-798b249aa335) 一文)，但有下列限制：  
  
-   因為 Visual Studio 巨集預設也會使用結尾斜線標記，所以您無法使用前後加上引號且包含結尾斜線標記的路徑  (例如，`–OutDir "C:\Output Folder\"` 無效。)若要解決此限制，您可以逸出結尾斜線  (例如，請改用 `-OutDir "$(OutDir)\"`。)  
  
-   根據預設，Mpgo.exe 不在 Visual Studio 組建路徑上。 您必須將路徑加入至 Visual Studio，或是在 Mpgo 命令列上指定完整路徑。 您可以在 Visual Studio 的建置後事件中使用 `–Scenario` 或 `–Import` 參數。 但一般的程序會從 Visual Studio 開發人員命令提示字元中使用一次 `–Scenario`，然後在每次建置之後，再使用 `–Import` 更新最佳化組件。例如：`"C:\Program Files\Microsoft Visual Studio 11.0\Team Tools\Performance Tools\mpgo.exe" -import "$(OutDir)tmp" -assemblylist "$(TargetPath)" -outdir "$(OutDir)\"`。  
  
<a name="samples"></a>   
## <a name="examples"></a>範例  
 下列 Visual Studio 開發人員命令提示字元中的 Mpgo.exe 命令會最佳化稅務應用程式：  
  
```  
mpgo –scenario "C:\MyApp\MyTax.exe /params par" –AssemblyList Mytax.dll MyTaxUtil2011.dll –OutDir C:\Optimized –TimeOut 15  
```  
  
 下列 Mpgo.exe 命令會最佳化音效應用程式：  
  
```  
mpgo –scenario "C:\MyApp\wav2wma.exe –input song1.wav –output song1.wma" –AssemblyList transcode.dll –OutDir C:\Optimized –TimeOut 15  
```  
  
 下列 Mpgo.exe 命令會使用先前最佳化組件的資料最佳化新版的組件：  
  
```  
mpgo.exe -import "C:\Optimized" -assemblylist "C:\MyApp\MyTax.dll" "C:\MyApp\MyTaxUtil2011.dll" -outdir C:\ReOptimized  
```  
  
## <a name="see-also"></a>請參閱  
 [Ngen.exe (原生映像產生器)](../../../docs/framework/tools/ngen-exe-native-image-generator.md)  
 [命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)  
 [改善桌面應用程式的啟動效能](http://go.microsoft.com/fwlink/p/?LinkId=248943)  
 [An Overview of Performance Improvements in .NET 4.5](http://go.microsoft.com/fwlink/p/?LinkId=249131) (.NET 4.5 的效能改進概觀)

---
title: "Resgen.exe (資源檔產生器)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- resource files, .resources files
- resource files, .resx files
- resx files (resource files)
- .resources files
- files, converting
- Resource File Generator
- .resx files
- Resgen.exe
- resource files, converting
- converting files, Resource File Generator
- binary resources files
- embedding files in runtime binary executable
ms.assetid: 8ef159de-b660-4bec-9213-c3fbc4d1c6f4
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ca54817183b5e659b62ef04b1693698bd689370b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="resgenexe-resource-file-generator"></a>Resgen.exe (資源檔產生器)
資源檔產生器 (Resgen.exe) 可以將文字檔 (.txt 或 .restext) 及 XML 架構資源格式檔 (.resx)，轉換成通用語言執行平台二進位檔 (.resources)，這種檔案可以嵌入至執行階段二進位可執行檔或附屬組件  (請參閱[建立資源檔](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md))。  
  
 Resgen.exe 為執行下列工作的通用資源轉換公用程式：  
  
-   將 .txt 或 .restext 檔轉換成 .resources 或 .resx 檔  (.restext 檔案的格式與 .txt 檔案的格式相同。 不過，.restext 副檔名可以幫助您更容易識別內含資源定義的文字檔)。  
  
-   將 .resources 檔轉換成文字或 .resx 檔。  
  
-   將 .resx 檔轉換成文字或 .resources 檔。  
  
-   從組譯碼擷取字串資源到適用於 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式的 .resw 檔案。  
  
-   建立可存取個別具名資源和對於 <xref:System.Resources.ResourceManager> 執行個體的強類型類別。  
  
 如果 Resgen.exe 因任何理由而失敗，則傳回值將會是 –1。  
  
 若要取得 Resgen.exe 的說明，您可以使用下列未指定選項的命令，以顯示 Resgen.exe 的命令語法和選項：  
  
```  
resgen  
```  
  
 您也可以使用 `/?` 參數：  
  
```  
resgen /?  
```  
  
 如果您使用 Resgen.exe 產生二進位的 .resources 檔案，您可以使用語言編譯器將二進位檔案內嵌至可執行的組件，或使用[組件連結器 (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) 將它們編譯到附屬組件。  
  
 此工具會自動與 Visual Studio 一起安裝。 若要執行此工具，請使用 [開發人員命令提示字元] \(或 Windows 7 中的 [Visual Studio 命令提示字元])。 如需詳細資訊，請參閱[命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)。  
  
 在命令提示字元下輸入下列命令：  
  
## <a name="syntax"></a>語法  
  
```  
resgen  [/define:symbol1[,symbol2,...]] [/useSourcePath] filename.extension  | /compile filename.extension... [outputFilename.extension] [/r:assembly] [/str:lang[,namespace[,class[,file]]] [/publicclass]]   
```  
  
```  
resgen filename.extension [outputDirectory]  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|-------------------------|-----------------|  
|`/define:` *symbol1*[, *symbol2*,...]|從 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 開始，支援文字資源檔 (.txt 或 .restext) 的條件式編譯。 如果 *symbol* 對應至在 `#ifdef` 建構內輸入文字檔中的符號，關聯字串資源會包含在 .resources 檔案中。 如果輸入文字檔包含有不是 `#if !` 參數所定義之符號的 `/define` 陳述式，關聯的字串資源會包含在資源檔中。<br /><br /> 使用非文字檔案則會忽略 `/define`。 符號會區分大小寫。<br /><br /> 如需這個選項的詳細資訊，請參閱本主題稍後的[條件式編譯資源](#Conditional)。|  
|`useSourcePath`|具體指明輸入檔的目前目錄是用來解析相對檔案路徑。|  
|`/compile`|可讓您指定在單一大量作業中，將多個 .resx 或文字檔轉換成多個 .resources 檔案。 如果您不指定這個選項，則只能指定一個輸入檔引數。 輸出檔案的名稱為 <檔案名稱>.resources。<br /><br /> 這個選項無法與 `/str:` 選項搭配使用。<br /><br /> 如需這個選項的詳細資訊，請參閱本主題稍後的[編譯或轉換多個檔案](#Multiple)。|  
|`/r:` `assembly`|從指定的組件參考中繼資料。 在轉換 .resx 檔時，以及讓 Resgen.exe 序列化或還原序列化物件資源時使用。 它類似 C# 和 Visual Basic 編譯器的 `/reference:` 或 `/r:` 選項。|  
|`filename.extension`|指定要轉換的輸入檔名稱。 如果您使用的是這個資料表前的命令列語法中的第一個、較長者，`extension` 必須是下列其中一項：<br /><br /> .txt 或 .restext<br /> 要轉換成 .resources 或 .resx 檔的文字檔。 文字檔只能包含字串資源。 如需檔案格式的詳細資訊，請參閱[建立資源檔](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)的＜文字檔中的資源＞一節。<br /><br /> .resx<br /> 要轉換成 .resources 或文字檔 (.txt 或 .restext) 的 XML 架構資源檔。<br /><br /> .resources<br /> 要轉換成 .resx 或文字檔 (.txt 或 .restext) 的二進位資源檔。<br /><br /> 如果您使用的是這個資料表前的命令列語法中的第二個、較短者，`extension` 必須為下列其中一項：<br /><br /> .exe 或 .dll。<br /> 字串資源要擷取至 .resw 檔以利開發 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式的 .NET Framework 組件 (可執行檔或程式庫)。|  
|`outputFilename.extension`|指定要建立之資源檔的名稱和類型。<br /><br /> 從 .txt、.restext 或 .resx 檔案轉換至 .resource 檔時，這是選擇性的引數。 如果沒有指定 `outputFilename`，Resgen.exe 會將 .resources 副檔名附加至輸入 `filename` 中，並且將檔案寫入包含 `filename,extension` 的目錄中。<br /><br /> 從 .resources 檔轉換時，`outputFilename.extension` 是強制的引數。 在將 .resources 檔轉換成 XML 架構資源檔時指定檔案名稱及 .resx 副檔名。 將 .resources 檔案轉換成文字檔時，指定檔案名稱及 .txt 或 .restext 副檔名。 當 .resources 檔只包含字串值時，您應將 .resources 檔轉換成 .txt 檔。|  
|`outputDirectory`|[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式中，指定其字串資源將被寫入且包含在 `filename.extension` 中的 .resw 檔案之目錄。 `outputDirectory` 必須已經存在。|  
|`/str:` `language[,namespace[,classname[,filename]]]`|以 `language` 選項所指定的程式設計語言建立強類型資源類別檔案。 `language` 可包含下列其中一種常值：<br /><br /> -   C#：`c#`、`cs` 或 `csharp`。<br />-   Visual Basic：`vb` 或 `visualbasic`。<br />-   VBScript：`vbs` 或 `vbscript`。<br />-   C++：`c++`、`mc` 或 `cpp`。<br />-   JavaScript：`js`、`jscript` 或 `javascript`。<br /><br /> 您可以使用 `namespace` 選項指定專案的預設命名空間，使用 `classname` 選項指定所產生類別的名稱，以及使用 `filename` 選項指定類別檔的名稱。<br /><br /> `/str:` 選項只允許一個輸入檔，因此無法搭配 `/compile` 選項使用。<br /><br /> 如果有指定 `namespace` 但未指定 `classname`，此時類別名稱便會衍生自該輸出檔名稱 (例如，以底線替代句號)。 這樣一來，強類型資源可能無法正確運作。 若要避免此問題，請同時指定類別名稱和輸出檔名稱。<br /><br /> 如需這個選項的詳細資訊，請參閱本主題稍後的[產生強型別資源類別](#Strong)。|  
|`/publicClass`|建立強類型資源類別做為公用類別。 根據預設，資源類別是在 C# 中的 `internal` 和 Visual Basic 中的 `Friend`。<br /><br /> 如果沒有使用 `/str:` 選項，則會忽略這個選項。|  
  
## <a name="resgenexe-and-resource-file-types"></a>Resgen.exe 和資源檔類型  
 要成功地用 Resgen.exe 轉換資源，文字檔和 .resx 檔必須遵守正確格式。  
  
### <a name="text-txt-and-restext-files"></a>文字檔 (.txt 和 .restext)  
 文字檔 (.txt 或 .restext) 只能包含字串資源。 如果您所撰寫的應用程式必須將字串轉譯成多種語言，字串資源是非常有用的。 例如，使用適當的字串資源，您可以輕易地按地區安排功能表字串。 Resgen.exe 會讀取含有名稱/值組的文字檔，其中名稱是描述資源的字串，而值是資源字串本身。  
  
> [!NOTE]
>  如需 .txt 或 .restext 檔格式的詳細資訊，請參閱[建立資源檔](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)的＜文字檔中的資源＞一節。  
  
 包含資源的文字檔除非其只包含基本拉丁範圍 (到 U+007F) 內的字元，否則必須以 UTF-8 或 Unicode (UTF-16) 的編碼方式保存。 Resgen.exe 在處理使用 ANSI 編碼方式儲存的文字檔時，會移除延伸的 ANSI 字元。  
  
 Resgen.exe 會針對重複的資源名稱檢查文字檔。 如果文字檔包含重複的資源名稱，Resgen.exe 將會發出警告並忽略第二個值。  
  
### <a name="resx-files"></a>.resx 檔  
 .resx 資源檔格式由 XML 項目組成。 您可以在這些 XML 項目中指定字串資源，就像在文字檔中的方式一樣。 .resx 檔優於文字檔的原因，就是您也可以指定或內嵌物件。 在檢視 .resx 檔時，您可以實際看到內嵌物件 (如圖片) 的二進位格式 (當這個二進位資訊是資源資訊清單的一部分時)。 與文字檔一樣，您可以使用文字編輯器開啟 .resx 檔案 (例如 [記事本] 或 Microsoft Word) 並寫入、剖析和操作其內容。 請注意您必須對 XML 標記和 .resx 檔案結構有相當的認識才能這麼做。 如需 .resx 檔案格式的詳細資訊，請參閱[建立資源檔](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)＜.resx 檔中的資源＞一節。  
  
 若要建立含有內嵌非字串物件的 .resources 檔，您必須使用 Resgen.exe 來轉換含有物件的 .resx 檔，或使用 <xref:System.Resources.ResourceWriter> 類別提供的方法，直接從程式碼中將物件資源加入您的檔案。  
  
 如果使用 Resgen.exe 將含有物件的 .resx 檔或 .resources 檔轉換成文字檔，則所有字串資源都會正確的轉換，但是非字串物件的資料類型也會以字串的形式寫入檔案中。 在進行轉換時您將會遺漏內嵌物件，而 Resgen.exe 將會報告擷取資源時發生錯誤。  
  
### <a name="converting-between-resources-file-types"></a>資源檔案類型間的轉換  
 當您在不同資源檔類型之間轉換時，根據來源和目標檔案的類型，Resgen.exe 可能無法執行轉換也可能會遺漏特定資源的詳細資訊。 從某種資源檔案類型轉換為另一種類型時，下表指定成功轉換的類型。  
  
|來源檔|轉至文字檔|轉至 .resx 檔|轉至 .resw 檔|轉至 .resources 檔|  
|------------------|------------------|-------------------|-------------------|------------------------|  
|文字檔 (.txt 或 .restext)|--|沒有問題|不支援|沒有問題|  
|.resx 檔|檔案包含非字串資源 (包括文件連結) 時轉換失敗|--|不支援|沒有問題|  
|.resources 檔|檔案包含非字串資源 (包括文件連結) 時轉換失敗|沒有問題|不支援|--|  
|.exe 或 .dll 組譯碼|不支援|不支援|只有字串資源 (包括路徑名稱) 被當做資源|不支援|  
  
## <a name="performing-specific-resgenexe-tasks"></a>執行特定 Resgen.exe 工作  
 您可以透過不同方式來使用 Resgen.exe：將文字或 XML 架構資源檔編譯成二進位檔案、資源檔格式間的轉換和產生包裝 <xref:System.Resources.ResourceManager> 功能並提供存取資源的類別。 本節提供各項工作的詳細資訊：  
  
-   [將資源編譯成二進位檔](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Compiling)  
  
-   [資源檔類型間的轉換](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Convert)  
  
-   [編譯或轉換多個檔案](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Multiple)  
  
-   [將資源匯出至 .resw 檔案](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Exporting)  
  
-   [條件式編譯資源](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Conditional)  
  
-   [產生強型別資源類別](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Strong)  
  
<a name="Compiling"></a>   
### <a name="compiling-resources-into-a-binary-file"></a>將資源編譯成二進位檔  
 最常見的 Resgen.exe 是用來將文字架構的資源檔 (.txt 或 .restext 檔) 或 XML 架構資源檔 (.resx 檔) 編譯成二進位 .resources 檔案。 輸出檔可以由語言編譯器內嵌在主要組件或由[組件連結器 (AL.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) 內嵌在附屬組件。  
  
 編譯資源檔的語法是：  
  
```  
resgen inputFilename [outputFilename]   
```  
  
 其中的參數：  
  
 `inputFilename`  
 要編譯的資源檔檔案名稱 (包括副檔名)。 Resgen.exe 只編譯使用 .txt、.restext 或 .resx 為副檔名的檔案。  
  
 `outputFilename`  
 輸出檔的名稱。 如果您省略 `outputFilename`，Resgen.exe 會在和 `inputFilename` 相同的目錄下建立具有 `inputFilename` 之根檔案名稱的 .resources 檔。 如果 `outputFilename` 包含一個目錄路徑，則目錄必須存在。  
  
 您可以在 .resource 檔的檔案名稱中指定並將命名空間與根檔案名稱以一個句號分隔，為 .resources 檔案提供完整命名空間。 例如，如果 `outputFilename` 是 `MyCompany.Libraries.Strings.resources`，則命名空間是 MyCompany.Libraries。  
  
 下列命令會讀取 Resources.txt 中的名稱/值組，並且寫入名為 Resources.resources 的二進位 .resources 檔。 由於並未明確指定輸出檔名，因此預設會接收與輸入檔相同的名稱。  
  
```  
resgen Resources.txt   
```  
  
 下列命令會讀取 Resources.restext 中的名稱/值組，並且寫入名為 StringResources.resources 的二進位 .resources 檔。  
  
```  
resgen Resources.restext StringResources.resources  
```  
  
 下列命令會讀取 XML 架構檔案且名稱為 Resources.resx 的輸入檔，並寫入命名為 Resources.resources 的二進位 .resources 檔案。  
  
```  
resgen Resources.resx Resources.resources  
```  
  
<a name="Convert"></a>   
### <a name="converting-between-resource-file-types"></a>資源檔類型間的轉換  
 除了將文字或 XML 架構的資源檔編譯成二進位 .resources 檔外，Resgen.exe 能將任何支援的檔案類型轉換為其他任何支援的檔案類型。 這表示它可以執行下列轉換：  
  
-   .txt 檔和 .restext 檔轉換為 .resx 檔。  
  
-   .resx 檔轉換為 .txt 和 .restext 檔。  
  
-   .resources 檔轉換為 .txt 檔和 .restext 檔。  
  
-   .resources 檔轉換為 .resx 檔。  
  
 語法與上一節顯示的內容相同。  
  
 此外，您也可以使用 Resgen.exe 來將在 .NET Framework 組件中的內嵌資源轉換成 .resw 檔案，做為 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式。  
  
 下列命令會讀取名為 Resources.resources 的二進位 .resources 檔案，並寫入名為 Resources.resx 的 XML 架構輸出檔案。  
  
```  
resgen Resources.resources Resources.resx  
```  
  
 下列命令會讀取命名為 StringResources.txt 的文字架構資源檔，並寫入名為 LibraryResources.resx 的 XML 架構資源檔。 除了包含字串資源之外，.resx 檔也可以用來儲存非字串資源。  
  
```  
resgen StringResources.txt LibraryResources.resx  
```  
  
 下列兩個命令會讀取名稱為 Resources.resx 的 XML 架構資源檔案，並寫入名為 Resources.txt 和 Resources.restext 的文字檔。 請注意，如果 .resx 檔內含任何嵌入的物件，就無法正確的轉換成文字檔。  
  
```  
resgen Resources.resx Resources.txt  
resgen Resources.resx Resources.restext  
```  
  
<a name="Multiple"></a>   
### <a name="compiling-or-converting-multiple-files"></a>編譯或轉換多個檔案  
 您可以使用 `/compile` 參數將一個資源檔清單透過單一作業轉換格式。 其語法為：  
  
```  
resgen /compile filename.extension [filename.extension...]  
```  
  
 下列命令會將三個檔案：StringResources.txt、TableResources.resw 和 ImageResources.resw，編譯成不同檔名的 .resources 檔案，分別為 StringResources.resources、TableResources.resources 和 ImageResources.resources。  
  
```  
resgen /compile StringResources.txt TableResources.resx ImageResources.resx  
```  
  
<a name="Exporting"></a>   
### <a name="exporting-resources-to-a-resw-file"></a>將資源匯出至 .resw 檔案  
 如果您正在開發 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式，您可能會想使用桌面上現有的應用程式資源。 然而，這兩種應用程式支援不同的檔案格式。 在桌面應用程式中，文字檔 (.txt 或 .restext) 或 .resx 檔案的資源會編譯為二進位 .resources 檔案。 在 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式中，.resw 檔案會編譯為二進位制封裝資源索引 (PRI) 檔案。 您可以從可執行檔或附屬組件擷取資源，並將它們寫入在開發 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式時使用的一個或多個 .resw 檔案，以使用 Resgen.exe 來縮小差距。  
  
> [!IMPORTANT]
>  Visual Studio 會自動處理並將所有轉換所需之可攜式程式庫中的合併資源加入至 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式中。 直接使用 Resgen.exe 來將組件中的資源轉換為 .resw 檔案格式僅適用於對開發在 Visual Studio 以外的 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式有興趣的開發人員。  
  
 從組件產生 .resw 檔案的語法是：  
  
```  
resgen filename.extension  [outputDirectory]  
```  
  
 其中的參數：  
  
 `filename.extension`  
 .NET Framework 組件的名稱 (可執行檔或 .dll)。 如果檔案不包含資源，Resgen.exe 不會建立任何檔案。  
  
 `outputDirectory`  
 .resw 檔案欲寫入的現有目錄。 如果省略 `outputDirectory`，.resw 檔案會寫入目前的目錄。 Resgen.exe 會為每個在組件中的 .resources 檔案建立 .resw 檔案。 .resw 檔案的根檔案名稱與 .resources 檔的根名稱相同。  
  
 下列命令會在 Win8Resources 目錄中為每個內嵌在 MyApp.exe 的 .resources 檔建立 .resw 檔案：  
  
```  
resgen MyApp.exe Win8Resources  
```  
  
<a name="Conditional"></a>   
### <a name="conditionally-compiling-resources"></a>條件式編譯資源  
 從 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 開始，Resgen.exe 支援文字檔 (.txt 和 .restext) 中字串資源的條件式編譯。 這可讓您在多個組建組態中使用單一文字資源檔。  
  
 在 .txt 或 .restext 檔中，如果有定義符號，您可以使用 `#ifdef`…`#endif` 結構以包含二進位 .resources 檔的資源，如果未下義符號，則可以使用 `#if !`... `#endif` 結構以包含資源。 在編譯時期，您可以使用 `/define:` 選項緊接著符號的逗號分隔清單來定義符號。 這個對照會區分大小寫，`/define` 定義的符號大小寫必須與欲編譯的文字檔中的大小寫吻合。  
  
 例如，下列名為 UIResources.rext 的檔案包含名為 `AppTitle` 的字串資源，根據是否定義符號，可以接受三個值之一：`PRODUCTION`、`CONSULT` 或 `RETAIL`。  
  
```  
#ifdef PRODUCTION  
AppTitle=My Software Company Project Manager   
#endif  
#ifdef CONSULT  
AppTitle=My Consulting Company Project Manager  
#endif  
#ifdef RETAIL  
AppTitle=My Retail Store Project Manager  
#endif  
FileMenuName=File  
```  
  
 檔案接下來可以藉由下列命令編譯成二進位的 .resources 檔案：  
  
```  
resgen /define:CONSULT UIResources.restext  
```  
  
 這會導致該 .resources 檔案中包含兩個字串資源。 `AppTitle` 資源的值為 "My Consulting Company Project Manager"。  
  
<a name="Strong"></a>   
### <a name="generating-a-strongly-typed-resource-class"></a>產生強類型資源類別  
 Resgen.exe 支援強類型資源 (會建立包含一組靜態唯讀屬性的類別，以封裝對資源的存取)。 這提供直接呼叫 <xref:System.Resources.ResourceManager> 類別的方法來擷取資源。 您可以使用 Resgen.exe 中的 `/str` 選項來啟用強類型資源的支援，以包裝 <xref:System.Resources.Tools.StronglyTypedResourceBuilder> 類別的功能。 當您指定 `/str` 選項時，Resgen.exe 的輸出會是一個包含強類型屬性的類別 (這類屬性與輸入參數中所參考的資源相符)。 這個類別可對已處理檔案中可取得資源的強類型提供唯讀存取。  
  
 建立強類型資源的語法是：  
  
```  
resgen inputFilename [outputFilename] /str:language[,namespace,[classname[,filename]]] [/publicClass]  
```  
  
 參數為：  
  
 `inputFilename`  
 欲產生強類型資源類別的資源檔之檔案名稱 (包括副檔名)。 檔案可以是文字、XML 架構或二進位 .resources 檔，它可以使用 .txt、.restext、.resw 或 .resources 副檔名。  
  
 `outputFilename`  
 輸出檔的名稱。 如果 `outputFilename` 包含一個目錄路徑，則目錄必須存在。 如果您省略 `outputFilename`，Resgen.exe 會在和 `inputFilename` 相同的目錄下建立具有 `inputFilename` 之根檔案名稱的 .resources 檔。  
  
 `outputFilename` 可以是文字、XML 架構或二進位 .resources 檔案。 如果 `outputFilename` 的副檔名與 `inputFilename` 的副檔名不同，Resgen.exe 會執行檔案轉換。  
  
 如果 `inputFilename` 為 .resources 檔案且 `outputFilename` 也是 .resources 檔，則 Resgen.exe 會複製 .resources 檔案。 如果省略 `outputFilename`，Resgen.exe 會覆寫具有相同 .resources 檔案的 `inputFilename`。  
  
 *language*  
 產生強類型資源類別的原始程式碼時，所使用的語言。 針對 C# 程式碼，可能的值為 `cs`、`C#` 和 `csharp`；針對 Visual Basic 程式碼，為 `vb` 和 `visualbasic`；針對 VBScript 程式碼，為 `vbs` 和 `vbscript`；針對 C++ 程式碼，為 `c++`、`mc` 和 `cpp`。  
  
 *命名空間*  
 包含強類型資源類別的命名空間。 .resources 檔案和資源類別應該有相同的命名空間。 如需指定 `outputFilename` 的命名空間之詳細資訊，請參閱[編譯資源至二進位檔中](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Compiling)。 如果省略 *namespace*，則命名空間不會包含資源類別。  
  
 *classname*  
 強類型資源類別的名稱。 這應該會對應於 .resources 檔的根名稱。 例如，如果 Resgen.exe 產生名為 MyCompany.Libraries.Strings.resources 的 .resources 檔案，強類型資源類別的名稱會為 Strings。 如果省略 *classname*，產生的類別會衍生自 `outputFilename` 的根目錄名稱。 如果省略 `outputFilename`，產生的類別會衍生自 `inputFilename` 的根目錄名稱。  
  
 *classname* 無法包含無效的字元 (如空白字元)。 如果 *classname* 包含空白字元，或如果 *classname* 預設是由 *inputFilename* 產生，並且 *inputFilename* 包含空白字元，則 Resgen.exe 會以底線 (_) 取代所有無效的字元。  
  
 *filename*  
 類別檔案的名稱。  
  
 `/publicclass`  
 讓強類型資源類別為公用類別而不是 `internal` (C#) 或 `Friend` (Visual Basic)。 這可讓資源從它們的內嵌組件外部存取。  
  
> [!IMPORTANT]
>  當您建立強類型資源類別時，您的 .resources 檔案的名稱必須符合所產生程式碼的命名空間和類別名稱。 不過，Resgen.exe 可讓您指定所產生 .resources 檔案有不相容名稱的選項。 為了解決這個行為，可在它產生之後重新命名輸出檔案。  
  
 強類型資源類別具有下列成員：  
  
-   無參數建構函式，可以使用來具現化強類型資源類別。  
  
-   `static` (C#) 或 `Shared` (Visual Basic) 和唯讀 `ResourceManager` 屬性，可傳回 <xref:System.Resources.ResourceManager> 管理強類型資源的執行個體。  
  
-   靜態 `Culture` 屬性，可讓您將文化特性設定為資源擷取使用。 根據預設，它的值是為 `null`，表示已使用目前的 UI 文化特性。  
  
-   在 .resource 檔中每個 resource 的 `static` (C#) 或 `Shared` (Visual Basic) 和唯讀屬性。 屬性名稱是資源的名稱。-  
  
 例如，下列命令會將名為 StringResources.txt 編譯為 StringResources.resources，並且在一個名為 StringResources.vb 的 Visual Basic 原始程式碼中產生名為 `StringResources` 的類別，可用於存取資源管理員。  
  
```  
resgen StringResources.txt /str:vb,,StringResources   
```  
  
## <a name="see-also"></a>請參閱  
 [工具](../../../docs/framework/tools/index.md)  
 [桌面應用程式中的資源](../../../docs/framework/resources/index.md)  
 [建立資源檔](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)  
 [Al.exe (組件連結器)](../../../docs/framework/tools/al-exe-assembly-linker.md)  
 [命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

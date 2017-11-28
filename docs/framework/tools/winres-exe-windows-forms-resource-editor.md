---
title: "Winres.exe (Windows Form 資源編輯器)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Winres.exe
- Windows Forms Resource Editor
- localization
- Windows Forms, localization
- forms, localizing
- resx files
- .resx files
ms.assetid: cb8bc835-9221-4888-af53-1a4f5fad6c48
caps.latest.revision: "23"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8009f832434d6bbad2ad7bee9cbfd62c81d623c7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="winresexe-windows-forms-resource-editor"></a>Winres.exe (Windows Form 資源編輯器)
Windows Form 資源編輯器 (Winres.exe) 是一項視覺化配置工具，可以幫助當地語系化專家將表單所使用的 Windows Form 使用者介面 (UI) 資源當地語系化。 做為 Winres.exe 輸入內容的 .resx 或 .resources 檔案，可以利用視覺化設計環境 (例如 Microsoft Visual Studio) 建立。 如需在 .NET Framework 應用程式中部署資源的資訊，請參閱[桌面應用程式中的資源](../../../docs/framework/resources/index.md)。  
  
 此工具會自動與 Visual Studio 一起安裝。 若要執行此工具，請使用 [開發人員命令提示字元] (或 Windows 7 中的 [Visual Studio 命令提示字元])。 如需詳細資訊，請參閱[命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)。  
  
 在命令提示字元下輸入下列命令：  
  
## <a name="syntax"></a>語法  
  
```  
winres resourceFile   
winres /?   
```  
  
## <a name="remarks"></a>備註  
  
|引數|說明|  
|--------------|-----------------|  
|`resourceFile`|要當地語系化的資源檔。 這個檔案必須是 Visual Studio 設計工具所產生的 Windows Form 表單 .resx 或 .resources 檔案。 Winres.exe 無法開啟泛型 .resx 或 .resources 檔案。|  
  
|選項|描述|  
|------------|-----------------|  
|**/?**|顯示工具的命令語法和選項。|  
  
 Windows Form 專案中表單的 UI 項目狀態通常儲存在資源檔內，它可能是副檔名為 .resx 的 XML 檔案，或是副檔名為 .resources 的已編譯對應二進位版本。 Winres.exe 是一項工具，可以在 Visual Studio 設計環境外對這兩種類型的檔案進行有限的編輯。 具體而言，這項工具允許下列類型的編輯作業：  
  
-   編輯中性或特定文化特性的資源檔可以變更表單或其控制項的 UI 屬性，例如文字、大小或位置。  
  
-   中性或特定文化特性的資源檔可以從預設資源檔產生。  
  
-   文化特性資源檔可以儲存為另一個文化特性資源檔。 例如，英文 (美國) 資源檔可以儲存為波蘭文資源檔。 通常對新檔案會進行後續編輯，以便與新的文化特性相容。  
  
 另請參閱[階層式組織當地語系化的資源](http://msdn.microsoft.com/library/756hydy4\(v=vs.110\))或[階層式組織當地語系化的資源](http://msdn.microsoft.com/library/756hydy4\(v=vs.120\))。  
  
 Winres.exe 無法將 .resx 檔案轉換成對應的 .resources 檔案，請改用 Resgen.exe 工具。 如需 Resgen.exe 的詳細資訊，請參閱 [Resgen.exe (資源檔產生器)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)。  
  
 Winres.exe 是圖形應用程式，只需從資源檔即可重新建立設計階段版本的 Windows Form 表單，不需要存取原始程式碼。 Winres.exe 可裝載 Visual Studio 的 Windows Form 表單設計工具和 [屬性] 視窗。 這些功能可以對內含 Windows Form 表單的 .resources 或 .resx 檔案進行視覺化編輯。 當地語系化人員通常會使用 Winres.exe 來編輯控制項標籤，並調整控制項的位置和大小，以納入目標文化特性的標籤。  
  
 如果 Winres.exe 無法解析控制項的類型，它會在已當地語系化的 .resx 或 .resources 檔案中建立預留位置控制項。 預留位置控制項在 Windows Form 表單上會顯示為規劃視窗。 規劃視窗的大小和位置與實際控制項的大小和位置相符。 預留位置控制項可使用的所有可當地語系化屬性都會出現在 [屬性] 視窗中。 您對預留位置控制項所做的任何變更都會儲存起來，供實際的控制項使用。  
  
## <a name="winresexe-versus-visual-studio"></a>Winres.exe 與 Visual Studio 比較  
 一般說來，在開始將應用程式的 Windows Form 表單當地語系化之前，應該先決定要使用 Visual Studio 或 Winres.exe 做為當地語系化工具。 由於版本相容性 (稍後說明) 的緣故，您可能無法在這兩種工具之間切換。  
  
 Visual Studio 的優點就是您可以用它來開發應用程式，並且將應用程式當地語系化。 若要在開發完成後將表單當地語系化，請將表單的 <xref:System.ComponentModel.LocalizableAttribute> (屬性編輯器中的 **Localizable** 屬性) 設定為 `true`，並將其 **Language** 屬性變更為所要的目標文化特性。 然後編輯字串並調整控制項的位置和大小，以容納目標文化特性的字串。 當您儲存當地語系化的 .resx 檔案時，Visual Studio 只會將可當地語系化的屬性 (也就是在目標文化特性中會改變的屬性) 寫入檔案中。 Visual Studio 會在正確的目錄位置中，自動為當地語系化的 .resx 檔案建立附屬組件。  另請參閱[逐步解說：將 Windows Forms 當地語系化](http://msdn.microsoft.com/library/y99d1cd3\(v=vs.110\))。  
  
 雖然 Visual Studio 提供整合式開發和當地語系化環境，但是，如果當地語系化工作是由協力廠商的當地語系化人員執行，則建議您使用 Winres.exe 工具。 由於 Winres.exe 只是一個當地語系化工具，因此可以讓應用程式的程式碼與要當地語系化的表單更清楚劃分開來，在管理大型專案時，這樣的功能非常實用。  
  
## <a name="using-winresexe"></a>使用 Winres.exe  
 若要使用 Winres.exe 進行當地語系化，您必須先使用像是 Visual Studio 的表單設計工具這類視覺化設計工具來開發應用程式。 開發完成時，請將表單的 <xref:System.ComponentModel.LocalizableAttribute> (屬性編輯器中的 **Localizable** 屬性) 設定為 `true`，然後將預設文化特性的 .resx 檔案交給協力廠商的當地語系化人員。 這個 .resx 檔案包含 Winres.exe 重新建立原始表單的設計階段版本所使用的額外資訊。  
  
> [!CAUTION]
>  Winres.exe 無法用來編輯預設資源檔。 Winres.exe 會將所有變更過的屬性解譯為已當地語系化的屬性，並將這些屬性儲存到目標文化特性資源檔中。  
  
 最後，最終版本的文化特性資源檔即可用來建立應用程式的當地語系化版本。 如需詳細資訊，請參閱[桌面應用程式中的資源](../../../docs/framework/resources/index.md)。  
  
 Winres.exe 2.0 版具有以下的特性和功能：  
  
-   Winres 可以採用單一檔案模式 (SFM) 或 Visual Studio 檔案模式 (VSFM) 運作。 SFM 是舊版模式，此模式是將表單及其內容的完整資訊儲存於資源檔內。 VSFM 則只將文化特性變更儲存到資源檔內。  
  
-   介面中新增了錯誤報告視窗，停駐於主視窗左下角。  
  
-   可以使用熱鍵來檢查是否有重複：從 [格式] 功能表，按一下 [檢查熱鍵] 命令。  
  
## <a name="version-compatibility"></a>版本相容性  
 由於 Visual Studio .NET 2002 和 Visual Studio 2005 的資源檔格式不同，Winres.exe 也做了相對的改變以求相容。 因此，通常您應該使用要用來建立應用程式的 .NET Framework 隨附的 Winres.exe 版本。 下表列出相容的版本。  
  
|Visual Studio|.NET Framework|Winres.exe|  
|-------------------|--------------------|----------------|  
|Visual Studio .NET 2002|1.0|1.0|  
|Visual Studio .NET 2003|1.1|1.1|  
|Visual Studio 2005|2.0|2.0|  
|Visual Studio 2008|3.0 和 3.5|3.0 和 3.5|  
|Visual Studio 2010|4.0|4.0|  
  
 如果您嘗試以 Winres.exe 2.0 版開啟舊版資源檔，系統將會提示您升級至與 .NET Framework 2.0 版相容的檔案格式。  
  
 在 .NET Framework 2.0 版之前的版本中，Winres.exe 和 Visual Studio 的表單設計工具會建立不相容的文化特性中性 (Culture-Neutral) 和文化特性特定 (Culture-Specific) 資源檔。 因此，一旦開始進行當地語系化流程，您就必須繼續使用同一項工具。 不過，Winres.exe 2.0 版已經新加入增了 Visual Studio 檔案模式 (VSFM)。 如其名稱所示，以這個相容模式儲存的資源檔可以利用任一種工具編輯。  
  
> [!NOTE]
>  雖然 VSFM 有和 Visual Studio 相容的優點，但由於它只儲存資源檔中變更過的值，因此 Winres.exe 要求目前資源檔的父代必須位於相同的目錄內。 例如，編輯 `TestApp.de-DE.resources` 德文 (德國) 資源檔時，必須要有預設資源檔 `TestApp.resx`，而且可能也需要文化特性中性資源檔 `TestApp.de.resources`。  
  
## <a name="examples"></a>範例  
  
#### <a name="to-localize-a-resx-or-resources-file-associated-with-a-form"></a>將與表單相關聯的 .resx 或 .resources 檔案當地語系化  
  
1.  在開發人員命令提示字元中輸入 `winres`，執行 Winres.exe。  
  
2.  若要開啟要當地語系化之表單的預設資源，請按一下 [檔案] 功能表上的 [開啟] 命令，並巡覽至檔案將它開啟。  
  
     -或-  
  
     啟動 Winres.exe 時，在命令列中指定要開啟的檔案。  
  
     下列命令會啟動 Winres.exe，並且在表單設計工具中載入與 `TestApp.resx` 相關聯的表單。  
  
    ```  
    winres TestApp.resx  
    ```  
  
     下列命令會啟動 Winres.exe，並且在表單設計工具中載入與 `TestApp.resources` 相關聯的表單。  
  
    ```  
    winres TestApp.resources  
    ```  
  
    > [!NOTE]
    >  如果您要編輯之資源的所屬表單是繼承的表單，則包含繼承之表單的組件和包含衍生表單的組件都必須在全域組件快取 (GAC) 中註冊，或是必須與 WinRes.exe 位於相同的目錄中。 如需將 .NET Framework 元件安裝到 GAC 的詳細資訊，請參閱[全域組件快取](../../../docs/framework/app-domains/gac.md)。  
  
3.  選取表單上的控制項，並且變更這些控制項的 <xref:System.Windows.Forms.Control.Text%2A> 和其他屬性，以反映當地語系化的文化特性及其語言。 視需要移動或調整控制項大小，以容納當地語系化的文字。  
  
4.  若要儲存 .resx 或 .resources 檔案的當地語系化版本，請按一下**儲存**圖示或 [檔案] 功能表上的相同命令。 工具會顯示 [選取文化特性] 視窗。  
  
5.  選取適當的文化特性和檔案模式，然後按一下 [確定]。 工具會使用執行階段所需的當地語系化資源檔命名規範來儲存檔案。 例如，如果您針對德國境內的德國人當地語系化 `TestApp.resources`，則工具會將檔案儲存為 `TestApp.de-DE.resources`。 如果您針對德國境內的德國人當地語系化 `TestApp.resx`，則工具會將檔案儲存為 `TestApp.de-DE.resx`。 如需資源命名慣例的詳細資訊，請參閱[封裝和部署資源](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)。 如需執行階段所使用之預先定義的文化特性名稱清單，請參閱 <xref:System.Globalization.CultureInfo> 類別。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ComponentModel.LocalizableAttribute>  
 <xref:System.Globalization.CultureInfo>  
 <xref:System.Resources.ResourceManager>  
 <xref:System.Resources.ResourceReader>  
 <xref:System.Resources.ResourceWriter>  
 [工具](../../../docs/framework/tools/index.md)  
 [桌面應用程式中的資源](../../../docs/framework/resources/index.md)  
 [全球化和當地語系化](../../../docs/standard/globalization-localization/index.md)

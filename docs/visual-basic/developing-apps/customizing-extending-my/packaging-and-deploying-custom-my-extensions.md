---
title: 封裝和部署自訂的 My 擴充 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
ms.openlocfilehash: 901d0b80a18d2f4d262cc65eb485dcc628bc6a08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="packaging-and-deploying-custom-my-extensions-visual-basic"></a>封裝和部署自訂的 My 擴充 (Visual Basic)
Visual Basic 提供簡單的方法，以部署您的自訂`My`使用 Visual Studio 範本命名空間擴充功能。 如果您要建立專案範本，您`My`延伸模組是新的專案類型中不可或缺的一部分，您可以包含自訂`My`與專案中，當您將範本匯出時的延伸模組程式碼。 如需匯出專案範本的詳細資訊，請參閱[How to： 建立專案範本](/visualstudio/ide/how-to-create-project-templates)。  
  
 如果您的自訂`My`延伸模組是在單一程式碼檔案中，您可以將檔案匯出為使用者可以將任何類型的 Visual Basic 專案加入的項目範本。 您可以自訂項目範本，若要啟用其他功能與您的自訂行為`My`Visual Basic 專案中的擴充功能。 這些功能包括：  
  
-   允許使用者管理您的自訂`My`延伸**My 擴充**頁面 Visual Basic 專案設計工具。  
  
-   自動加入您的自訂`My`延伸模組時指定的組件的參考加入至專案。  
  
-   隱藏`My`延伸模組中的項目範本**加入項目**對話方塊，讓它不會包含在清單中的專案項目。  
  
 本主題討論如何封裝自訂`My`副檔名為隱藏的項目範本，可以從管理**My 擴充**頁面 Visual Basic 專案設計工具。 自訂`My`延伸模組也可以加入自動時指定的組件的參考加入至專案。  
  
## <a name="create-a-my-namespace-extension"></a>建立我的命名空間擴充功能  
 建立自訂的部署封裝的第一個步驟`My`延伸模組是建立為單一程式碼檔案的副檔名。 詳細資料和有關如何建立自訂指引`My`延伸模組，請參閱[擴充 Visual Basic 中的 My 命名空間](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)。  
  
## <a name="export-a-my-namespace-extension-as-an-item-template"></a>匯出 My 命名空間擴充功能，做為項目範本  
 包含程式碼檔案之後您`My`命名空間擴充功能，您可以將程式碼檔案匯出為 Visual Studio 項目範本。 如需有關如何將檔案匯出為 Visual Studio 項目範本的指示，請參閱[How to： 建立項目範本](/visualstudio/ide/how-to-create-item-templates)。  
  
> [!NOTE]
>  如果您`My`命名空間擴充功能相依於特定的組件，您可以自訂項目範本，以自動安裝您`My`命名空間擴充功能時在加入該組件的參考。 如此一來，您會想要排除的組件參考，當您匯出的程式碼檔案與 Visual Studio 項目範本。  
  
## <a name="customize-the-item-template"></a>自訂項目範本  
 您可以啟用，從管理項目範本**My 擴充**頁面 Visual Basic 專案設計工具。 您也可以啟用指定的組件的參考加入至專案時，自動新增項目範本。 若要啟用這些自訂項目，您會加入新的檔案，稱為 CustomData 檔，以您的範本，以及.vstemplate 檔案中，然後將新的項目加入到 XML。  
  
### <a name="add-the-customdata-file"></a>加入 CustomData 檔案  
 CustomData 檔案是副檔名的文字檔。CustomData （檔案名稱可以設定為任何值，以您的範本有意義），其中包含 XML。 CustomData 檔案中的 XML 會指示 Visual Basic，包括您`My`延伸模組，當使用者使用時**My 擴充**頁面 Visual Basic 專案設計工具。 您可以選擇性地加入 <`AssemblyFullName>` CustomData 檔的 XML 屬性。 這會指示 Visual Basic 自動安裝您的自訂`My`延伸模組時的特定組件參考加入至專案。 您可以使用任何文字編輯器或 XML 編輯器來建立 CustomData 檔案，並將它新增至您的項目範本壓縮的資料夾 （.zip 檔）。  
  
 例如，下列 XML 顯示 CustomData 檔案會將範本項目加入到 Microsoft.VisualBasic.PowerPacks.Vs.dll 組件的參考時，Visual Basic 專案的 我的擴充功能資料夾的內容加入至專案。  
  
```xml  
<VBMyExtensionTemplate   
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"   
    Version="1.0.0.0"  
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"  
/>  
```  
  
 CustomData 檔案包含 <`VBMyExtensionTemplate>`具有屬性，如下表中所列的項目。  
  
|屬性|描述|  
|---|---|  
|`ID`|必要。 延伸模組的唯一識別碼。 如果具有此識別碼的擴充功能已加入專案中，新增一次不會提示使用者。|  
|`Version`|必要。 項目範本的版本號碼。|  
|`AssemblyFullName`|選擇性。 組件名稱。 當此組件的參考加入至專案時，會提示使用者加入`My`延伸模組，從這個項目範本。|  
  
### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a>新增\<CustomDataSignature > 的.vstemplate 檔的項目  
 若要識別您的 Visual Studio 項目範本作為`My`命名空間擴充功能，您也必須修改.vstemplate 檔案的項目範本。 您必須新增`<CustomDataSignature>`元素`<TemplateData>`項目。 `<CustomDataSignature>`元素必須包含文字`Microsoft.VisualBasic.MyExtension`，如下列範例所示。  
  
```xml  
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>  
```  
  
 您無法直接修改壓縮的資料夾 （.zip 檔） 中的檔案。 您必須複製.vstemplate 檔案從壓縮的資料夾、 修改它，並使用更新的複本取代.vstemplate 檔案，將壓縮資料夾中。  
  
 下列範例示範具有.vstemplate 檔案的內容`<CustomDataSignature>`加入項目。  
  
```xml  
<VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">  
  <TemplateData>  
    <DefaultName>MyCustomExtensionModule.vb</DefaultName>  
    <Name>MyPrinterInfo</Name>  
    <Description>Custom My Extensions Item Template</Description>  
    <ProjectType>VisualBasic</ProjectType>  
    <SortOrder>10</SortOrder>  
    <Icon>__TemplateIcon.ico</Icon>  
    <CustomDataSignature      >Microsoft.VisualBasic.MyExtension</CustomDataSignature>  
  </TemplateData>  
  <TemplateContent>  
    <References />  
    <ProjectItem SubType="Code"   
                 TargetFileName="$fileinputname$.vb"  
                 ReplaceParameters="true"  
     >MyCustomExtensionModule.vb</ProjectItem>  
  </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="install-the-template"></a>安裝範本  
 若要安裝的範本，您可以將壓縮的資料夾 （.zip 檔案） 複製到 Visual Basic 項目範本資料夾 （例如，My Documents\Visual Studio 2008\Templates\Item Templates\Visual 基本）。 或者，您可以為 Visual Studio 安裝程式 (.vsi) 檔案發佈的範本。  
  
## <a name="see-also"></a>另請參閱  
 [擴充 Visual Basic 中的 My 命名空間](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)  
 [擴充 Visual Basic 應用程式模型](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)  
 [自訂 My 中可用的物件](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)  
 [專案設計工具 my 擴充頁](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)

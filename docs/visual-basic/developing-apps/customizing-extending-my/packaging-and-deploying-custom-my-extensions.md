---
title: "封裝和部署自訂的 My 擴充 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- My namespace, customizing
- My namespace
- My namespace, extending
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 950592c0fb197959ce1c3cf6128093846a022709
ms.lasthandoff: 03/13/2017

---
# <a name="packaging-and-deploying-custom-my-extensions-visual-basic"></a>封裝和部署自訂的 My 擴充 (Visual Basic)
Visual Basic 提供簡單的方法，您才能部署您的自訂`My`命名空間擴充，使用 Visual Studio 範本。 如果您要建立專案範本，您`My`延伸模組是新的專案類型中不可或缺的一部分，您可以包含自訂`My`延伸模組程式碼專案中，當您匯出的範本。 如需匯出專案範本的詳細資訊，請參閱[How to︰ 建立專案範本](http://msdn.microsoft.com/library/a1a6999d-a34c-48a8-b1cf-027eb5c76398)。  
  
 如果您的自訂`My`延伸模組是在單一程式碼檔案中，您可以將檔案匯出成項目範本讓使用者可以加入至任何類型的 Visual Basic 專案。 您可以自訂項目範本，若要啟用其他功能與您的自訂行為`My`Visual Basic 專案中的延伸模組。 這些功能包括︰  
  
-   允許使用者管理您的自訂`My`副檔名， **My 擴充**Visual Basic 專案設計工具頁面。  
  
-   自動新增您的自訂`My`延伸模組時指定的組件的參考加入至專案。  
  
-   隱藏`My`延伸模組中的項目範本**加入項目**對話方塊，讓它不會納入專案項目的清單。  
  
 本主題討論如何將封裝自訂`My`副檔名為隱藏的項目範本，可從**My 擴充**Visual Basic 專案設計工具頁面。 自訂`My`延伸模組也會自動加入當指定的組件的參考加入至專案。  
  
## <a name="create-a-my-namespace-extension"></a>建立 My 命名空間擴充  
 建立自訂的部署封裝的第一個步驟`My`擴充功能是建立一個程式碼檔案的延伸模組。 如需詳細資訊和有關如何建立自訂的指引`My`延伸模組，請參閱[擴充 My 命名空間，在 Visual Basic 中](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)。  
  
## <a name="export-a-my-namespace-extension-as-an-item-template"></a>匯出為項目範本的 My 命名空間擴充  
 包含的程式碼檔案之後您`My`命名空間擴充，您可以將程式碼檔匯出為 Visual Studio 項目範本。 如需如何將檔案匯出成 Visual Studio 項目範本的指示，請參閱[How to︰ 建立項目範本](http://msdn.microsoft.com/library/77bc53d4-d607-4820-a032-7e3b365891b5)。  
  
> [!NOTE]
>  如果您`My`命名空間擴充具有特定的組件相依性，您可以自訂項目範本，以自動安裝您`My`命名空間擴充功能時在加入該組件的參考。 如此一來，您會想要排除的組件參考，當您匯出的程式碼檔案做為 Visual Studio 項目範本。  
  
## <a name="customize-the-item-template"></a>自訂項目範本  
 您可以啟用項目範本，從管理**My 擴充**Visual Basic 專案設計工具頁面。 您也可以啟用指定的組件的參考加入至專案時，自動新增項目範本。 若要啟用這些自訂項目，您將會新增一個新的檔案，稱為 CustomData 檔案，您的範本，並新增新的項目 xml.vstemplate 檔案中。  
  
### <a name="add-the-customdata-file"></a>加入 CustomData 檔案  
 CustomData 檔案是副檔名的文字檔。CustomData （檔案名稱可以設定為任何值有意義的範本），其中包含 XML。 CustomData 檔案中的 XML 會指示 Visual Basic，以包含您`My`延伸模組，當使用者使用**My 擴充**Visual Basic 專案設計工具頁面。 您可以選擇性地加入`AssemblyFullName>`CustomData 檔的 XML 屬性。 這會指示 Visual Basic，以自動安裝您的自訂`My`延伸模組，當特定的組件的參考加入至專案。 您可以使用任何文字編輯器或 XML 編輯器建立 CustomData 檔案，並將其加入項目範本的壓縮資料夾 （.zip 檔案）。  
  
 例如，下列 XML 顯示 CustomData 檔案會將範本項目加入至 Microsoft.VisualBasic.PowerPacks.Vs.dll 組件的參考時，Visual Basic 專案的 My 擴充資料夾的內容加入至專案。  
  
```  
<VBMyExtensionTemplate   
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"   
    Version="1.0.0.0"  
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"  
/>  
```  
  
 CustomData 檔案包含`VBMyExtensionTemplate>`具有屬性，如下列表格所列的項目。  
  
|屬性|描述|  
|---|---|  
|`ID`|必要項。 延伸模組的唯一識別碼。 如果具有此識別碼的延伸模組已加入至專案，再加入不會提示使用者。|  
|`Version`|必要項。 項目範本的版本號碼。|  
|`AssemblyFullName`|選擇項。 組件名稱。 當此組件的參考加入至專案時，會提示使用者加入`My`副檔名，這個項目範本。|  
  
### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a>新增\<CustomDataSignature > 的.vstemplate 檔的項目  
 若要識別您的 Visual Studio 項目範本，作為`My`命名空間擴充，您也必須修改項目範本的.vstemplate 檔。 您必須新增`<CustomDataSignature>`項目`<TemplateData>`項目。 `<CustomDataSignature>`元素必須包含文字`Microsoft.VisualBasic.MyExtension`，如下列範例所示。  
  
```  
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>  
```  
  
 您無法直接修改壓縮的資料夾 （.zip 檔案） 中的檔案。 您必須從壓縮資料夾中複製.vstemplate 檔案，進行修改，然後將壓縮資料夾中的.vstemplate 檔取代更新的複製。  
  
 下列範例顯示具有.vstemplate 檔案的內容`<CustomDataSignature>`加入項目。  
  
```  
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
  
## <a name="install-the-template"></a>安裝的範本  
 若要安裝的範本，您可以將壓縮的資料夾 （.zip 檔案） 複製到 Visual Basic 項目範本資料夾 （例如 My Documents\Visual Studio 2008\Templates\Item templates\item Templates\Visual 基本）。 或者，您可以發行範本，為 Visual Studio 安裝程式 (.vsi) 檔案。  
  
## <a name="see-also"></a>請參閱  
 [擴充 Visual Basic 中的 My 命名空間](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)   
 [擴充 Visual Basic 應用程式模型](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)   
 [自訂可用的物件在我](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)   
 [專案設計工具 my 擴充頁](https://docs.microsoft.com/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)

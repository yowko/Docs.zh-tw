---
title: "Packaging and Deploying Custom My Extensions (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My namespace, customizing"
  - "My namespace"
  - "My namespace, extending"
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# Packaging and Deploying Custom My Extensions (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Visual Basic 提供簡易的方法，讓您使用 Visual Studio 範本來部署自訂的 `My` 命名空間擴充。  如果您正在建立專案範本，而 `My` 擴充是新的專案類型中不可或缺的部分，您可以在匯出範本時在專案中包含自訂的 `My` 擴充程式碼。  如需匯出專案範本的詳細資訊，請參閱 [如何：建立專案範本](../Topic/How%20to:%20Create%20Project%20Templates.md)。  
  
 如果您的自訂 `My` 擴充是在一個程式碼檔案中，您可以將檔案匯出成項目範本，讓使用者將其加入至任何類型的 Visual Basic 專案中。  然後您就可以自訂項目範本，為 Visual Basic 專案中的 `My` 擴充啟用其他功能與行為。  這些功能包括：  
  
-   允許使用者管理 Visual Basic 專案設計工具中 \[**My 擴充**\] 頁面上的自訂 `My` 擴充。  
  
-   當指定之組件的參考加入至專案中時，就會自動加入您的自訂 `My` 擴充。  
  
-   隱藏 \[**加入項目**\] 對話方塊中的 `My` 擴充項目範本，如此範本就不會包含在專案項目清單中。  
  
 本主題說明如何將自訂的 `My` 擴充封裝成隱藏的項目範本，使其可以從 Visual Basic 專案設計工具的 \[**My 擴充**\] 頁面進行管理。  當指定的組件之參考加入至專案中時，也會自動加入自訂的 `My` 擴充。  
  
## 建立 My 命名空間擴充  
 為自訂 `My` 擴充建立部署套件的第一步，就是建立擴充以做為單一程式碼檔案。  如需如何建立自訂 `My` 擴充的詳細資訊及方針，請參閱[Extending the My Namespace in Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)。  
  
## 將 My 命名空間擴充匯出成項目範本  
 當您具有包含 `My` 命名空間擴充的程式碼檔案後，就可以將程式碼檔案匯出成 Visual Studio 項目範本。  如需將檔案匯出成 Visual Studio 項目範本的指示，請參閱 [如何：建立項目範本](../Topic/How%20to:%20Create%20Item%20Templates.md)。  
  
> [!NOTE]
>  如果您的 `My` 命名空間擴充和特定組件具有相依性，您就可以自訂項目範本，以便在加入組件的參考時自動安裝您的 `My` 命名空間擴充。  因此，當您在將程式碼檔案匯出成 Visual Studio 項目範本時，就必須排除組件參考。  
  
## 自訂項目範本  
 您可以讓項目範本成為可以從 Visual Basic 專案設計工具的 \[**My 擴充**\] 頁面進行管理，  也可以在指定的組件之參考加入專案時，讓項目範本自動加入。  若要啟用這些自訂功能，您要將名稱為 CustomData 的新檔案加入至範本，然後將新的項目加入至 .vstemplate 檔案中的 XML。  
  
### 加入 CustomData 檔案  
 CustomData 檔案是一個文字檔，副檔名為 .CustomData \(檔案名稱可以設定為對您的範本有意義的任何值\) 且內含 XML。  CustomData 檔案中的 XML 會指示 Visual Basic，在使用者使用 Visual Basic 專案設計工具的 \[**My 擴充**\] 頁面時，包含您的 `My` 擴充。  您也可以選擇將 \<`AssemblyFullName>` 屬性加入至 CustomData 檔案 XML。  這麼做會指示 Visual Basic 在特定組件的參考加入至專案時，自動安裝您的自訂 `My` 擴充。  您可以使用任何文字編輯器或 XML 編輯器來建立 CustomData 檔案，然後將檔案加入至項目範本的壓縮資料夾 \(.zip 檔\) 中。  
  
 例如，下列 XML 顯示 CustomData 檔案的內容，當 Microsoft.VisualBasic.PowerPacks.Vs.dll 組件的參考加入專案時，該檔案會將範本項目加入 Visual Basic 專案的 \[My 擴充\] 資料夾中。  
  
```  
<VBMyExtensionTemplate   
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"   
    Version="1.0.0.0"  
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"  
/>  
```  
  
 CustomData 檔案內含 \<`VBMyExtensionTemplate>` 項目，其屬性如下。  
  
|||  
|-|-|  
|屬性|描述|  
|`ID`|必要項。  這是擴充的唯一識別項。  如果具有這個 ID 的擴充已經加入至之專案中，就不會再提示使用者加入。|  
|`Version`|必要項。  這是項目範本的版本號碼。|  
|`AssemblyFullName`|選擇項。  這是組件名稱。  當這個組件的參考加入至專案時，會提示使用者加入這個項目範本中的 `My` 擴充。|  
  
### 將 \<CustomDataSignature\> 項目加入至 .vstemplate 檔案  
 若要將您的 Visual Studio 項目範本識別為 `My` 命名空間擴充，您也必須修改項目範本的 .vstemplate 檔案。  您必須將 `<CustomDataSignature>` 項目加入至 `<TemplateData>` 項目中。  `<CustomDataSignature>` 項目必須內含文字 `Microsoft.VisualBasic.MyExtension`，如下列範例所示。  
  
```  
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>  
```  
  
 您不能直接修改壓縮資料夾 \(.zip 檔案\) 中的檔案。  您必須複製、修改壓縮資料夾中的 .vstemplate 檔案，然後以更新過的版本取代壓縮資料夾中的 .vstemplate 檔案。  
  
 下列範例顯示已加入 `<CustomDataSignature>` 項目之 .vstemplate 檔案的內容。  
  
```  
<VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">  
  <TemplateData>  
    <DefaultName>MyCustomExtensionModule.vb</DefaultName>  
    <Name>MyPrinterInfo</Name>  
    <Description>Custom My Extensions Item Template</Description>  
    <ProjectType>VisualBasic</ProjectType>  
    <SortOrder>10</SortOrder>  
    <Icon>__TemplateIcon.ico</Icon>  
    <CustomDataSignature       >Microsoft.VisualBasic.MyExtension</CustomDataSignature>  
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
  
## 安裝範本  
 若要安裝範本，您可以將壓縮的資料夾 \(.zip 檔案\) 複製至 Visual Basic 項目範本資料夾中 \(例如，My Documents\\Visual Studio 2008\\Templates\\Item Templates\\Visual Basic\)。  或者，您可以將範本發行成 Visual Studio Installer \(.vsi\) 檔案。  如需將範本發行成 Visual Studio Installer 檔案的詳細資訊，請參閱 [NIB: How to: Publish Project Templates](http://msdn.microsoft.com/zh-tw/b9087f58-64e9-4767-bf54-e3bf40d63b20)。  
  
## 請參閱  
 [Extending the My Namespace in Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)   
 [Extending the Visual Basic Application Model](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)   
 [Customizing Which Objects are Available in My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)   
 [專案設計工具、My 擴充頁](/visual-studio/ide/reference/my-extensions-page-project-designer-visual-basic)
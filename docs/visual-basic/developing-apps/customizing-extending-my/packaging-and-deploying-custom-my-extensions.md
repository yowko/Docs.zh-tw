---
title: 封裝和部署自訂的 My 延伸模組 (Visual Basic)
ms.date: 08/14/2018
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
ms.openlocfilehash: 4212f58c39f63be6ba20c3b79e5d9c98d0615c5e
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43745369"
---
# <a name="package-and-deploy-custom-my-extensions-visual-basic"></a>封裝及部署自訂的 My 延伸模組 (Visual Basic)

Visual Basic 提供簡單的方法，以部署您的自訂`My`使用 Visual Studio 範本的命名空間延伸模組。 如果您要建立的專案範本，讓您`My`擴充功能是新的專案類型中不可或缺的一部分，您可以只包含您的自訂`My`延伸模組程式碼使用專案中，當您匯出的範本。 如需有關匯出專案範本的詳細資訊，請參閱[如何： 建立專案範本](/visualstudio/ide/how-to-create-project-templates)。

如果您的自訂`My`延伸模組是在單一程式碼檔案中，您可以將檔案匯出為使用者可以將任何類型的 Visual Basic 專案中加入的項目範本。 您可以自訂的項目範本，以啟用其他功能與您的自訂行為`My`Visual Basic 專案中的延伸模組。 這些功能包括下列各項：

- 讓使用者能夠管理您的自訂`My`延伸模組，從**My 擴充**Visual Basic 專案設計工具的頁面。

- 自動加入您的自訂`My`延伸模組時指定的組件的參考新增至專案。

- 隱藏`My`延伸模組中的項目範本**加入項目**對話方塊，讓它將不會包含在清單中的專案項目。

本主題討論如何封裝自訂`My`延伸模組為隱藏的項目範本，可由**My 擴充**Visual Basic 專案設計工具的頁面。 自訂`My`可以也會自動新增擴充功能時指定的組件的參考新增至專案。

## <a name="create-a-my-namespace-extension"></a>建立我的命名空間延伸模組

建立自訂的部署封裝的第一個步驟`My`擴充功能是建立為單一程式碼檔案的副檔名。 如需詳細資料和有關如何建立自訂的指引`My`延伸模組，請參閱 <<c2> [ 擴充 My 命名空間，在 Visual Basic 中](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)。

## <a name="export-a-my-namespace-extension-as-an-item-template"></a>匯出我的命名空間延伸模組，做為項目範本

包含的程式碼檔案之後您`My`命名空間延伸模組，您可以將程式碼檔案匯出為 Visual Studio 項目範本。 如需有關如何將檔案匯出為 Visual Studio 項目範本的指示，請參閱 <<c0> [ 如何： 建立項目範本](/visualstudio/ide/how-to-create-item-templates)。

> [!NOTE]
> 如果您`My`命名空間延伸模組相依於特定的組件，您可以自訂您的項目範本，以自動安裝您`My`命名空間擴充功能時在加入該組件的參考。 如此一來，您會想要排除的組件參考，當您匯出的程式碼檔案做為 Visual Studio 項目範本。

## <a name="customize-the-item-template"></a>自訂項目範本

您可以讓您從管理的項目範本**My 擴充**Visual Basic 專案設計工具的頁面。 您也可以啟用指定的組件的參考新增至專案時，自動新增項目範本。 若要啟用這些自訂項目，您會加入新的檔案，稱為 CustomData 檔案，以您的範本，，，然後在.vstemplate 檔案中的 xml 新增新的項目。

### <a name="add-the-customdata-file"></a>新增 CustomData 檔案

CustomData 檔案是具有副檔名的文字檔。CustomData （檔案名稱可以設定為任何值至您的範本有意義） 並包含 XML。 CustomData 檔案中的 XML 會指示 Visual Basic，以包含您`My`當使用者使用時的擴充功能**My 擴充**Visual Basic 專案設計工具的頁面。 您可以選擇性地加入 <`AssemblyFullName>` CustomData 檔的 XML 屬性。 這會指示 Visual Basic，以自動安裝您的自訂`My`擴充功能特定的組件的參考加入至專案。 您可以使用任何文字編輯器或 XML 編輯器建立 CustomData 檔案，並再將它新增至您的項目範本壓縮的資料夾 （.zip 檔案）。

例如，下列 XML 會顯示將範本項目加入時 Microsoft.VisualBasic.PowerPacks.Vs.dll 組件的參考是 Visual Basic 專案的 My 延伸模組資料夾 CustomData 檔案的內容加入至專案。

```xml
<VBMyExtensionTemplate
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"
    Version="1.0.0.0"
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"
/>
```

CustomData 檔案包含 <`VBMyExtensionTemplate>`具有屬性下, 表所列的項目。

|屬性|描述|
|---|---|
|`ID`|必要項。 延伸模組的唯一識別碼。 如果有此識別碼的延伸模組已新增至專案，將它再度新增不會提示使用者。|
|`Version`|必要項。 項目範本的版本號碼。|
|`AssemblyFullName`|選擇項。 組件名稱。 當此組件的參考加入專案中時，會提示使用者加入`My`從這個項目範本的延伸模組。|

### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a>新增\<CustomDataSignature > 的.vstemplate 檔的項目

若要識別您的 Visual Studio 項目範本，作為`My`命名空間延伸模組，您也必須修改.vstemplate 檔案項目範本。 您必須新增`<CustomDataSignature>`項目`<TemplateData>`項目。 `<CustomDataSignature>`項目必須包含文字`Microsoft.VisualBasic.MyExtension`，如下列範例所示。

```xml
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>
```

您無法直接修改壓縮的資料夾 （.zip 檔案） 中的檔案。 您必須複製.vstemplate 檔案壓縮的資料夾中，修改它，然後將壓縮的資料夾中的.vstemplate 檔案取代更新的複製。

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

若要安裝的範本，您可以複製壓縮的資料夾 (*.zip*檔案) 至 Visual Basic 項目範本資料夾。 根據預設，使用者項目範本位於 *%USERPROFILE%\Documents\Visual Studio\<版本\>\Templates\ItemTemplates\Visual Basic*。 或者，您可以發行為 Visual Studio 安裝程式的範本 (*.vsi*) 檔案。

## <a name="see-also"></a>另請參閱

- [擴充 Visual Basic 中的 My 命名空間](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)
- [擴充 Visual Basic 應用程式模型](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
- [自訂 My 中可用的物件](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [我的延伸模組頁面、專案設計工具](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)

---
title: 封裝和部署自訂 My 擴充功能
ms.date: 08/14/2018
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
ms.openlocfilehash: 6d2cc2b01b04b30bd3b1a4371352ded20ea8664b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411749"
---
# <a name="package-and-deploy-custom-my-extensions-visual-basic"></a>封裝和部署自訂 My extensions （Visual Basic）

Visual Basic 提供簡單的方法，讓您使用 Visual Studio 範本來部署自訂 `My` 命名空間延伸模組。 如果您要建立的專案範本 `My` 中的延伸模組是新專案類型不可或缺的一部分，則當您匯出範本時，可以直接在專案中包含自訂 `My` 擴充程式碼。 如需匯出專案範本的詳細資訊，請參閱[如何：建立專案範本](/visualstudio/ide/how-to-create-project-templates)。

如果您的自訂 `My` 擴充功能在單一程式碼檔案中，您可以將檔案匯出為專案範本，讓使用者可以加入至任何類型的 Visual Basic 專案。 接著，您可以自訂專案範本，以 `My` 在 Visual Basic 專案中啟用自訂延伸模組的其他功能和行為。 這些功能包括下列各項：

- 允許使用者 `My` 從 Visual Basic 專案設計工具的 [**我的延伸**模組] 頁面管理您的自訂延伸模組。

- `My`當指定元件的參考新增至專案時，自動加入您的自訂延伸模組。

- 隱藏 `My` [**加入專案**] 對話方塊中的延伸模組專案範本，使其不會包含在專案專案清單中。

本主題討論如何將自訂 `My` 延伸模組封裝為隱藏專案範本，以便從 [Visual Basic 專案設計工具] 的 [**我的擴充**功能] 頁面進行管理。 `My`當指定元件的參考新增至專案時，也可以自動加入自訂延伸模組。

## <a name="create-a-my-namespace-extension"></a>建立 My 命名空間延伸模組

建立自訂延伸模組之部署套件的第一個步驟 `My` ，是將擴充功能建立為單一程式碼檔案。 如需有關如何建立自訂延伸模組的詳細資訊和指引 `My` ，請參閱[在 Visual Basic 中擴充 My 命名空間](extending-the-my-namespace.md)。

## <a name="export-a-my-namespace-extension-as-an-item-template"></a>將 My namespace 延伸模組匯出為專案範本

在您擁有包含命名空間延伸模組的程式碼檔案之後 `My` ，您可以將程式碼檔案匯出為 Visual Studio 專案範本。 如需如何將檔案匯出為 Visual Studio 專案範本的指示，請參閱[如何：建立專案範本](/visualstudio/ide/how-to-create-item-templates)。

> [!NOTE]
> 如果您的 `My` 命名空間延伸相依于特定元件，您可以自訂專案範本，以便 `My` 在加入該元件的參考時，自動安裝您的命名空間延伸模組。 因此，當您將程式碼檔案匯出為 Visual Studio 專案範本時，您會想要排除該元件參考。

## <a name="customize-the-item-template"></a>自訂專案範本

您可以從 [Visual Basic 專案設計工具] 的 [**我的擴充**功能] 頁面中，啟用專案範本的管理。 您也可以啟用在將指定元件的參考加入至專案時，自動加入專案範本。 若要啟用這些自訂，您要將名為 CustomData 檔案的新檔案新增至您的範本，然後將新的專案加入至 .vstemplate 檔案中的 XML。

### <a name="add-the-customdata-file"></a>新增 CustomData 檔案

CustomData 檔案是副檔名為的文字檔。CustomData （檔案名可以設定為對您的範本有意義的任何值），而且包含 XML。 `My`當使用者使用 Visual Basic 專案設計工具的 [**我的延伸**模組] 頁面時，CustomData 檔案中的 XML 會指示 Visual Basic 納入您的延伸模組。 您可以選擇性地將 <`AssemblyFullName>` 屬性加入至 CustomData 檔案 XML。 這會指示 Visual Basic 在將 `My` 特定元件的參考新增至專案時，自動安裝您的自訂延伸模組。 您可以使用任何文字編輯器或 XML 編輯器來建立 CustomData 檔案，然後將它新增至專案範本的壓縮資料夾（.zip 檔案）。

例如，下列 XML 會顯示 CustomData 檔案的內容，此檔案會在 PowerPacks 的參考新增至專案時，將範本專案新增至 Visual Basic 專案的 [My Extensions] 資料夾。

```xml
<VBMyExtensionTemplate
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"
    Version="1.0.0.0"
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"
/>
```

CustomData 檔案包含 `VBMyExtensionTemplate>` 具有下表所列屬性的 <元素。

|屬性|描述|
|---|---|
|`ID`|必要。 延伸模組的唯一識別碼。 如果已將具有此識別碼的延伸模組新增至專案，則不會提示使用者重新加入該擴充功能。|
|`Version`|必要。 專案範本的版本號碼。|
|`AssemblyFullName`|選擇性。 組件名稱。 當此元件的參考新增至專案時，系統會提示使用者 `My` 從這個專案範本加入延伸模組。|

### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a>將 \<CustomDataSignature> 元素新增至 .vstemplate 檔案

若要將 Visual Studio 專案範本識別為 `My` 命名空間延伸模組，您也必須修改專案範本的 .vstemplate 檔案。 您必須將 `<CustomDataSignature>` 元素加入至專案 `<TemplateData>` 。 `<CustomDataSignature>`元素必須包含文字 `Microsoft.VisualBasic.MyExtension` ，如下列範例所示。

```xml
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>
```

您無法直接修改壓縮資料夾（.zip 檔案）中的檔案。 您必須從壓縮的資料夾複製 .vstemplate 檔案，加以修改，然後將壓縮資料夾中的 .vstemplate 檔案取代為更新後的複本。

下列範例顯示已加入專案之 .vstemplate 檔案的內容 `<CustomDataSignature>` 。

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

若要安裝範本，您可以將壓縮資料夾（*.zip*檔案）複製到 Visual Basic 專案範本] 資料夾。 根據預設，使用者專案範本位於 *%USERPROFILE%\Documents\Visual Studio \<Version\> \Templates\ItemTemplates\Visual Basic*中。 或者，您也可以將範本發佈為 Visual Studio 安裝程式（*.vsi*）檔案。

## <a name="see-also"></a>另請參閱

- [擴充 Visual Basic 中的 My 命名空間](extending-the-my-namespace.md)
- [擴充 Visual Basic 應用程式模型](extending-the-visual-basic-application-model.md)
- [自訂 My 可以使用的物件](customizing-which-objects-are-available-in-my.md)
- [My 擴充頁、專案設計工具](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)

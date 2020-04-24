---
title: 封裝和部署自訂 My 擴充功能
ms.date: 08/14/2018
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
ms.openlocfilehash: a2e2a6705fb3d8d4424d46d96bbf49b41e1414af
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330252"
---
# <a name="package-and-deploy-custom-my-extensions-visual-basic"></a><span data-ttu-id="1e89f-102">封裝和部署自訂 My extensions （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="1e89f-102">Package and deploy custom My extensions (Visual Basic)</span></span>

<span data-ttu-id="1e89f-103">Visual Basic 提供簡單的方法，讓您使用 Visual Studio 範本`My`來部署自訂命名空間延伸模組。</span><span class="sxs-lookup"><span data-stu-id="1e89f-103">Visual Basic provides an easy way for you to deploy your custom `My` namespace extensions by using Visual Studio templates.</span></span> <span data-ttu-id="1e89f-104">如果您要建立的專案範本中的`My`延伸模組是新專案類型不可或缺的一部分，則當您匯出範本時， `My`可以直接在專案中包含自訂擴充程式碼。</span><span class="sxs-lookup"><span data-stu-id="1e89f-104">If you are creating a project template for which your `My` extensions are an integral part of the new project type, you can just include your custom `My` extension code with the project when you export the template.</span></span> <span data-ttu-id="1e89f-105">如需匯出專案範本的詳細資訊，請參閱[如何：建立專案範本](/visualstudio/ide/how-to-create-project-templates)。</span><span class="sxs-lookup"><span data-stu-id="1e89f-105">For more information about exporting project templates, see [How to: Create Project Templates](/visualstudio/ide/how-to-create-project-templates).</span></span>

<span data-ttu-id="1e89f-106">如果您的`My`自訂擴充功能在單一程式碼檔案中，您可以將檔案匯出為專案範本，讓使用者可以加入至任何類型的 Visual Basic 專案。</span><span class="sxs-lookup"><span data-stu-id="1e89f-106">If your custom `My` extension is in a single code file, you can export the file as an item template that users can add to any type of Visual Basic project.</span></span> <span data-ttu-id="1e89f-107">接著，您可以自訂專案範本，以在 Visual Basic 專案中啟用自`My`定義延伸模組的其他功能和行為。</span><span class="sxs-lookup"><span data-stu-id="1e89f-107">You can then customize the item template to enable additional capabilities and behavior for your custom `My` extension in a Visual Basic project.</span></span> <span data-ttu-id="1e89f-108">這些功能包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="1e89f-108">Those capabilities include the following:</span></span>

- <span data-ttu-id="1e89f-109">允許使用者從 Visual Basic 專案設計`My`工具的 [**我的延伸**模組] 頁面管理您的自訂延伸模組。</span><span class="sxs-lookup"><span data-stu-id="1e89f-109">Allowing users to manage your custom `My` extension from the **My Extensions** page of the Visual Basic Project Designer.</span></span>

- <span data-ttu-id="1e89f-110">當指定元件的`My`參考新增至專案時，自動加入您的自訂延伸模組。</span><span class="sxs-lookup"><span data-stu-id="1e89f-110">Automatically adding your custom `My` extension when a reference to a specified assembly is added to a project.</span></span>

- <span data-ttu-id="1e89f-111">隱藏 [ `My` **加入專案**] 對話方塊中的延伸模組專案範本，使其不會包含在專案專案清單中。</span><span class="sxs-lookup"><span data-stu-id="1e89f-111">Hiding the `My` extension item template in the **Add Item** dialog box so that it is not included in the list of project items.</span></span>

<span data-ttu-id="1e89f-112">本主題討論如何將自訂`My`延伸模組封裝為隱藏專案範本，以便從 [Visual Basic 專案設計工具] 的 [我的**擴充**功能] 頁面進行管理。</span><span class="sxs-lookup"><span data-stu-id="1e89f-112">This topic discusses how to package a custom `My` extension as a hidden item template that can be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="1e89f-113">當指定`My`元件的參考新增至專案時，也可以自動加入自訂延伸模組。</span><span class="sxs-lookup"><span data-stu-id="1e89f-113">The custom `My` extension can also be added automatically when a reference to a specified assembly is added to a project.</span></span>

## <a name="create-a-my-namespace-extension"></a><span data-ttu-id="1e89f-114">建立 My 命名空間延伸模組</span><span class="sxs-lookup"><span data-stu-id="1e89f-114">Create a My namespace extension</span></span>

<span data-ttu-id="1e89f-115">建立自訂`My`延伸模組之部署套件的第一個步驟，是將擴充功能建立為單一程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="1e89f-115">The first step in creating a deployment package for a custom `My` extension is to create the extension as a single code file.</span></span> <span data-ttu-id="1e89f-116">如需有關如何建立自訂`My`延伸模組的詳細資訊和指引，請參閱[在 Visual Basic 中擴充 My 命名空間](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="1e89f-116">For details and guidance about how to create a custom `My` extension, see [Extending the My Namespace in Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).</span></span>

## <a name="export-a-my-namespace-extension-as-an-item-template"></a><span data-ttu-id="1e89f-117">將 My namespace 延伸模組匯出為專案範本</span><span class="sxs-lookup"><span data-stu-id="1e89f-117">Export a My namespace extension as an item template</span></span>

<span data-ttu-id="1e89f-118">在您擁有包含命名空間延伸模組的`My`程式碼檔案之後，您可以將程式碼檔案匯出為 Visual Studio 專案範本。</span><span class="sxs-lookup"><span data-stu-id="1e89f-118">After you have a code file that includes your `My` namespace extension, you can export the code file as a Visual Studio item template.</span></span> <span data-ttu-id="1e89f-119">如需如何將檔案匯出為 Visual Studio 專案範本的指示，請參閱[如何：建立專案範本](/visualstudio/ide/how-to-create-item-templates)。</span><span class="sxs-lookup"><span data-stu-id="1e89f-119">For instructions on how to export a file as a Visual Studio item template, see [How to: Create Item Templates](/visualstudio/ide/how-to-create-item-templates).</span></span>

> [!NOTE]
> <span data-ttu-id="1e89f-120">如果您`My`的命名空間延伸相依于特定元件，您可以自訂專案範本，以便在加入該`My`元件的參考時，自動安裝您的命名空間延伸模組。</span><span class="sxs-lookup"><span data-stu-id="1e89f-120">If your `My` namespace extension has a dependency on a particular assembly, you can customize your item template to automatically install your `My` namespace extension when a reference to that assembly is added.</span></span> <span data-ttu-id="1e89f-121">因此，當您將程式碼檔案匯出為 Visual Studio 專案範本時，您會想要排除該元件參考。</span><span class="sxs-lookup"><span data-stu-id="1e89f-121">As a result, you will want to exclude that assembly reference when you export the code file as a Visual Studio item template.</span></span>

## <a name="customize-the-item-template"></a><span data-ttu-id="1e89f-122">自訂專案範本</span><span class="sxs-lookup"><span data-stu-id="1e89f-122">Customize the item template</span></span>

<span data-ttu-id="1e89f-123">您可以從 [Visual Basic 專案設計工具] 的 [**我的擴充**功能] 頁面中，啟用專案範本的管理。</span><span class="sxs-lookup"><span data-stu-id="1e89f-123">You can enable your item template to be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="1e89f-124">您也可以啟用在將指定元件的參考加入至專案時，自動加入專案範本。</span><span class="sxs-lookup"><span data-stu-id="1e89f-124">You can also enable the item template to be added automatically when a reference to a specified assembly is added to a project.</span></span> <span data-ttu-id="1e89f-125">若要啟用這些自訂，您要將名為 CustomData 檔案的新檔案新增至您的範本，然後將新的專案加入至 .vstemplate 檔案中的 XML。</span><span class="sxs-lookup"><span data-stu-id="1e89f-125">To enable these customizations, you will add a new file, called the CustomData file, to your template, and then add a new element to the XML in your .vstemplate file.</span></span>

### <a name="add-the-customdata-file"></a><span data-ttu-id="1e89f-126">新增 CustomData 檔案</span><span class="sxs-lookup"><span data-stu-id="1e89f-126">Add the CustomData file</span></span>

<span data-ttu-id="1e89f-127">CustomData 檔案是副檔名為的文字檔。CustomData （檔案名可以設定為對您的範本有意義的任何值），而且包含 XML。</span><span class="sxs-lookup"><span data-stu-id="1e89f-127">The CustomData file is a text file that has a file name extension of .CustomData (the file name can be set to any value meaningful to your template) and that contains XML.</span></span> <span data-ttu-id="1e89f-128">當使用者使用 Visual Basic 專案設計工具的 [我的`My` **延伸**模組] 頁面時，CUSTOMDATA 檔案中的 XML 會指示 Visual Basic 納入您的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="1e89f-128">The XML in the CustomData file instructs Visual Basic to include your `My` extension when users use the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="1e89f-129">您可以選擇性地將 <`AssemblyFullName>`屬性加入至 CUSTOMDATA 檔案 XML。</span><span class="sxs-lookup"><span data-stu-id="1e89f-129">You can optionally add the <`AssemblyFullName>` attribute to your CustomData file XML.</span></span> <span data-ttu-id="1e89f-130">這會指示 Visual Basic 在將特定元件`My`的參考新增至專案時，自動安裝您的自訂延伸模組。</span><span class="sxs-lookup"><span data-stu-id="1e89f-130">This instructs Visual Basic to automatically install your custom `My` extension when a reference to a particular assembly is added to the project.</span></span> <span data-ttu-id="1e89f-131">您可以使用任何文字編輯器或 XML 編輯器來建立 CustomData 檔案，然後將它新增至專案範本的壓縮資料夾（.zip 檔案）。</span><span class="sxs-lookup"><span data-stu-id="1e89f-131">You can use any text editor or XML editor to create the CustomData file, and then add it to your item template's compressed folder (.zip file).</span></span>

<span data-ttu-id="1e89f-132">例如，下列 XML 會顯示 CustomData 檔案的內容，此檔案會在 PowerPacks 的參考新增至專案時，將範本專案新增至 Visual Basic 專案的 [My Extensions] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="1e89f-132">For example, the following XML shows the contents of a CustomData file that will add the template item to the My Extensions folder of a Visual Basic project when a reference to the Microsoft.VisualBasic.PowerPacks.Vs.dll assembly is added to the project.</span></span>

```xml
<VBMyExtensionTemplate
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"
    Version="1.0.0.0"
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"
/>
```

<span data-ttu-id="1e89f-133">CustomData 檔案包含具有下表`VBMyExtensionTemplate>`所列屬性的 <元素。</span><span class="sxs-lookup"><span data-stu-id="1e89f-133">The CustomData file contains a <`VBMyExtensionTemplate>` element that has attributes as listed in the following table.</span></span>

|<span data-ttu-id="1e89f-134">屬性</span><span class="sxs-lookup"><span data-stu-id="1e89f-134">Attribute</span></span>|<span data-ttu-id="1e89f-135">說明</span><span class="sxs-lookup"><span data-stu-id="1e89f-135">Description</span></span>|
|---|---|
|`ID`|<span data-ttu-id="1e89f-136">必要。</span><span class="sxs-lookup"><span data-stu-id="1e89f-136">Required.</span></span> <span data-ttu-id="1e89f-137">延伸模組的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="1e89f-137">A unique identifier for the extension.</span></span> <span data-ttu-id="1e89f-138">如果已將具有此識別碼的延伸模組新增至專案，則不會提示使用者重新加入該擴充功能。</span><span class="sxs-lookup"><span data-stu-id="1e89f-138">If the extension that has this ID has already been added to the project, the user will not be prompted to add it again.</span></span>|
|`Version`|<span data-ttu-id="1e89f-139">必要。</span><span class="sxs-lookup"><span data-stu-id="1e89f-139">Required.</span></span> <span data-ttu-id="1e89f-140">專案範本的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="1e89f-140">A version number for the item template.</span></span>|
|`AssemblyFullName`|<span data-ttu-id="1e89f-141">選擇性。</span><span class="sxs-lookup"><span data-stu-id="1e89f-141">Optional.</span></span> <span data-ttu-id="1e89f-142">組件名稱。</span><span class="sxs-lookup"><span data-stu-id="1e89f-142">An assembly name.</span></span> <span data-ttu-id="1e89f-143">當此元件的參考新增至專案時，系統會提示使用者從這個專案範本加入`My`延伸模組。</span><span class="sxs-lookup"><span data-stu-id="1e89f-143">When a reference to this assembly is added to the project, the user will be prompted to add the `My` extension from this item template.</span></span>|

### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a><span data-ttu-id="1e89f-144">將\<CustomDataSignature> 元素新增至 .vstemplate 檔案</span><span class="sxs-lookup"><span data-stu-id="1e89f-144">Add the \<CustomDataSignature> element to the .vstemplate file</span></span>

<span data-ttu-id="1e89f-145">若要將 Visual Studio 專案範本識別為`My`命名空間延伸模組，您也必須修改專案範本的 .vstemplate 檔案。</span><span class="sxs-lookup"><span data-stu-id="1e89f-145">To identify your Visual Studio item template as a `My` namespace extension, you must also modify the .vstemplate file for your item template.</span></span> <span data-ttu-id="1e89f-146">您必須將`<CustomDataSignature>`元素加入至`<TemplateData>`專案。</span><span class="sxs-lookup"><span data-stu-id="1e89f-146">You must add a `<CustomDataSignature>` element to the `<TemplateData>` element.</span></span> <span data-ttu-id="1e89f-147">`<CustomDataSignature>`元素必須包含文字`Microsoft.VisualBasic.MyExtension`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="1e89f-147">The `<CustomDataSignature>` element must contain the text `Microsoft.VisualBasic.MyExtension`, as shown in the following example.</span></span>

```xml
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>
```

<span data-ttu-id="1e89f-148">您無法直接修改壓縮資料夾（.zip 檔案）中的檔案。</span><span class="sxs-lookup"><span data-stu-id="1e89f-148">You cannot modify files in a compressed folder (.zip file) directly.</span></span> <span data-ttu-id="1e89f-149">您必須從壓縮的資料夾複製 .vstemplate 檔案，加以修改，然後將壓縮資料夾中的 .vstemplate 檔案取代為更新後的複本。</span><span class="sxs-lookup"><span data-stu-id="1e89f-149">You must copy the .vstemplate file from the compressed folder, modify it, and then replace the .vstemplate file in the compressed folder with your updated copy.</span></span>

<span data-ttu-id="1e89f-150">下列範例顯示已`<CustomDataSignature>`加入專案之 .vstemplate 檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="1e89f-150">The following example shows the contents of a .vstemplate file that has the `<CustomDataSignature>` element added.</span></span>

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

## <a name="install-the-template"></a><span data-ttu-id="1e89f-151">安裝範本</span><span class="sxs-lookup"><span data-stu-id="1e89f-151">Install the template</span></span>

<span data-ttu-id="1e89f-152">若要安裝範本，您可以將壓縮資料夾（*.zip*檔案）複製到 Visual Basic 專案範本] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="1e89f-152">To install the template, you can copy the compressed folder (*.zip* file) to the Visual Basic item templates folder.</span></span> <span data-ttu-id="1e89f-153">根據預設，使用者專案範本位於 *%USERPROFILE%\Documents\Visual Studio \< \>版本 \Templates\ItemTemplates\Visual Basic*中。</span><span class="sxs-lookup"><span data-stu-id="1e89f-153">By default, user item templates are located in *%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ItemTemplates\Visual Basic*.</span></span> <span data-ttu-id="1e89f-154">或者，您也可以將範本發佈為 Visual Studio 安裝程式（*.vsi*）檔案。</span><span class="sxs-lookup"><span data-stu-id="1e89f-154">Alternatively, you can publish the template as a Visual Studio Installer (*.vsi*) file.</span></span>

## <a name="see-also"></a><span data-ttu-id="1e89f-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e89f-155">See also</span></span>

- [<span data-ttu-id="1e89f-156">擴充 Visual Basic 中的 My 命名空間</span><span class="sxs-lookup"><span data-stu-id="1e89f-156">Extending the My Namespace in Visual Basic</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)
- [<span data-ttu-id="1e89f-157">擴充 Visual Basic 應用程式模型</span><span class="sxs-lookup"><span data-stu-id="1e89f-157">Extending the Visual Basic Application Model</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
- [<span data-ttu-id="1e89f-158">自訂 My 中可用的物件</span><span class="sxs-lookup"><span data-stu-id="1e89f-158">Customizing Which Objects are Available in My</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [<span data-ttu-id="1e89f-159">My 擴充頁、專案設計工具</span><span class="sxs-lookup"><span data-stu-id="1e89f-159">My Extensions Page, Project Designer</span></span>](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)

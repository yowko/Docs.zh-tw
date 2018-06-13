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
ms.locfileid: "33591855"
---
# <a name="packaging-and-deploying-custom-my-extensions-visual-basic"></a><span data-ttu-id="87420-102">封裝和部署自訂的 My 擴充 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87420-102">Packaging and deploying custom My extensions (Visual Basic)</span></span>
<span data-ttu-id="87420-103">Visual Basic 提供簡單的方法，以部署您的自訂`My`使用 Visual Studio 範本命名空間擴充功能。</span><span class="sxs-lookup"><span data-stu-id="87420-103">Visual Basic provides an easy way for you to deploy your custom `My` namespace extensions by using Visual Studio templates.</span></span> <span data-ttu-id="87420-104">如果您要建立專案範本，您`My`延伸模組是新的專案類型中不可或缺的一部分，您可以包含自訂`My`與專案中，當您將範本匯出時的延伸模組程式碼。</span><span class="sxs-lookup"><span data-stu-id="87420-104">If you are creating a project template for which your `My` extensions are an integral part of the new project type, you can just include your custom `My` extension code with the project when you export the template.</span></span> <span data-ttu-id="87420-105">如需匯出專案範本的詳細資訊，請參閱[How to： 建立專案範本](/visualstudio/ide/how-to-create-project-templates)。</span><span class="sxs-lookup"><span data-stu-id="87420-105">For more information about exporting project templates, see [How to: Create Project Templates](/visualstudio/ide/how-to-create-project-templates).</span></span>  
  
 <span data-ttu-id="87420-106">如果您的自訂`My`延伸模組是在單一程式碼檔案中，您可以將檔案匯出為使用者可以將任何類型的 Visual Basic 專案加入的項目範本。</span><span class="sxs-lookup"><span data-stu-id="87420-106">If your custom `My` extension is in a single code file, you can export the file as an item template that users can add to any type of Visual Basic project.</span></span> <span data-ttu-id="87420-107">您可以自訂項目範本，若要啟用其他功能與您的自訂行為`My`Visual Basic 專案中的擴充功能。</span><span class="sxs-lookup"><span data-stu-id="87420-107">You can then customize the item template to enable additional capabilities and behavior for your custom `My` extension in a Visual Basic project.</span></span> <span data-ttu-id="87420-108">這些功能包括：</span><span class="sxs-lookup"><span data-stu-id="87420-108">Those capabilities include the following:</span></span>  
  
-   <span data-ttu-id="87420-109">允許使用者管理您的自訂`My`延伸**My 擴充**頁面 Visual Basic 專案設計工具。</span><span class="sxs-lookup"><span data-stu-id="87420-109">Allowing users to manage your custom `My` extension from the **My Extensions** page of the Visual Basic Project Designer.</span></span>  
  
-   <span data-ttu-id="87420-110">自動加入您的自訂`My`延伸模組時指定的組件的參考加入至專案。</span><span class="sxs-lookup"><span data-stu-id="87420-110">Automatically adding your custom `My` extension when a reference to a specified assembly is added to a project.</span></span>  
  
-   <span data-ttu-id="87420-111">隱藏`My`延伸模組中的項目範本**加入項目**對話方塊，讓它不會包含在清單中的專案項目。</span><span class="sxs-lookup"><span data-stu-id="87420-111">Hiding the `My` extension item template in the **Add Item** dialog box so that it is not included in the list of project items.</span></span>  
  
 <span data-ttu-id="87420-112">本主題討論如何封裝自訂`My`副檔名為隱藏的項目範本，可以從管理**My 擴充**頁面 Visual Basic 專案設計工具。</span><span class="sxs-lookup"><span data-stu-id="87420-112">This topic discusses how to package a custom `My` extension as a hidden item template that can be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="87420-113">自訂`My`延伸模組也可以加入自動時指定的組件的參考加入至專案。</span><span class="sxs-lookup"><span data-stu-id="87420-113">The custom `My` extension can also be added automatically when a reference to a specified assembly is added to a project.</span></span>  
  
## <a name="create-a-my-namespace-extension"></a><span data-ttu-id="87420-114">建立我的命名空間擴充功能</span><span class="sxs-lookup"><span data-stu-id="87420-114">Create a My namespace extension</span></span>  
 <span data-ttu-id="87420-115">建立自訂的部署封裝的第一個步驟`My`延伸模組是建立為單一程式碼檔案的副檔名。</span><span class="sxs-lookup"><span data-stu-id="87420-115">The first step in creating a deployment package for a custom `My` extension is to create the extension as a single code file.</span></span> <span data-ttu-id="87420-116">詳細資料和有關如何建立自訂指引`My`延伸模組，請參閱[擴充 Visual Basic 中的 My 命名空間](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="87420-116">For details and guidance about how to create a custom `My` extension, see [Extending the My Namespace in Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).</span></span>  
  
## <a name="export-a-my-namespace-extension-as-an-item-template"></a><span data-ttu-id="87420-117">匯出 My 命名空間擴充功能，做為項目範本</span><span class="sxs-lookup"><span data-stu-id="87420-117">Export a My namespace extension as an item template</span></span>  
 <span data-ttu-id="87420-118">包含程式碼檔案之後您`My`命名空間擴充功能，您可以將程式碼檔案匯出為 Visual Studio 項目範本。</span><span class="sxs-lookup"><span data-stu-id="87420-118">After you have a code file that includes your `My` namespace extension, you can export the code file as a Visual Studio item template.</span></span> <span data-ttu-id="87420-119">如需有關如何將檔案匯出為 Visual Studio 項目範本的指示，請參閱[How to： 建立項目範本](/visualstudio/ide/how-to-create-item-templates)。</span><span class="sxs-lookup"><span data-stu-id="87420-119">For instructions on how to export a file as a Visual Studio item template, see [How to: Create Item Templates](/visualstudio/ide/how-to-create-item-templates).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="87420-120">如果您`My`命名空間擴充功能相依於特定的組件，您可以自訂項目範本，以自動安裝您`My`命名空間擴充功能時在加入該組件的參考。</span><span class="sxs-lookup"><span data-stu-id="87420-120">If your `My` namespace extension has a dependency on a particular assembly, you can customize your item template to automatically install your `My` namespace extension when a reference to that assembly is added.</span></span> <span data-ttu-id="87420-121">如此一來，您會想要排除的組件參考，當您匯出的程式碼檔案與 Visual Studio 項目範本。</span><span class="sxs-lookup"><span data-stu-id="87420-121">As a result, you will want to exclude that assembly reference when you export the code file as a Visual Studio item template.</span></span>  
  
## <a name="customize-the-item-template"></a><span data-ttu-id="87420-122">自訂項目範本</span><span class="sxs-lookup"><span data-stu-id="87420-122">Customize the item template</span></span>  
 <span data-ttu-id="87420-123">您可以啟用，從管理項目範本**My 擴充**頁面 Visual Basic 專案設計工具。</span><span class="sxs-lookup"><span data-stu-id="87420-123">You can enable your item template to be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="87420-124">您也可以啟用指定的組件的參考加入至專案時，自動新增項目範本。</span><span class="sxs-lookup"><span data-stu-id="87420-124">You can also enable the item template to be added automatically when a reference to a specified assembly is added to a project.</span></span> <span data-ttu-id="87420-125">若要啟用這些自訂項目，您會加入新的檔案，稱為 CustomData 檔，以您的範本，以及.vstemplate 檔案中，然後將新的項目加入到 XML。</span><span class="sxs-lookup"><span data-stu-id="87420-125">To enable these customizations, you will add a new file, called the CustomData file, to your template, and then add a new element to the XML in your .vstemplate file.</span></span>  
  
### <a name="add-the-customdata-file"></a><span data-ttu-id="87420-126">加入 CustomData 檔案</span><span class="sxs-lookup"><span data-stu-id="87420-126">Add the CustomData file</span></span>  
 <span data-ttu-id="87420-127">CustomData 檔案是副檔名的文字檔。CustomData （檔案名稱可以設定為任何值，以您的範本有意義），其中包含 XML。</span><span class="sxs-lookup"><span data-stu-id="87420-127">The CustomData file is a text file that has a file name extension of .CustomData (the file name can be set to any value meaningful to your template) and that contains XML.</span></span> <span data-ttu-id="87420-128">CustomData 檔案中的 XML 會指示 Visual Basic，包括您`My`延伸模組，當使用者使用時**My 擴充**頁面 Visual Basic 專案設計工具。</span><span class="sxs-lookup"><span data-stu-id="87420-128">The XML in the CustomData file instructs Visual Basic to include your `My` extension when users use the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="87420-129">您可以選擇性地加入 <`AssemblyFullName>` CustomData 檔的 XML 屬性。</span><span class="sxs-lookup"><span data-stu-id="87420-129">You can optionally add the <`AssemblyFullName>` attribute to your CustomData file XML.</span></span> <span data-ttu-id="87420-130">這會指示 Visual Basic 自動安裝您的自訂`My`延伸模組時的特定組件參考加入至專案。</span><span class="sxs-lookup"><span data-stu-id="87420-130">This instructs Visual Basic to automatically install your custom `My` extension when a reference to a particular assembly is added to the project.</span></span> <span data-ttu-id="87420-131">您可以使用任何文字編輯器或 XML 編輯器來建立 CustomData 檔案，並將它新增至您的項目範本壓縮的資料夾 （.zip 檔）。</span><span class="sxs-lookup"><span data-stu-id="87420-131">You can use any text editor or XML editor to create the CustomData file, and then add it to your item template's compressed folder (.zip file).</span></span>  
  
 <span data-ttu-id="87420-132">例如，下列 XML 顯示 CustomData 檔案會將範本項目加入到 Microsoft.VisualBasic.PowerPacks.Vs.dll 組件的參考時，Visual Basic 專案的 我的擴充功能資料夾的內容加入至專案。</span><span class="sxs-lookup"><span data-stu-id="87420-132">For example, the following XML shows the contents of a CustomData file that will add the template item to the My Extensions folder of a Visual Basic project when a reference to the Microsoft.VisualBasic.PowerPacks.Vs.dll assembly is added to the project.</span></span>  
  
```xml  
<VBMyExtensionTemplate   
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"   
    Version="1.0.0.0"  
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"  
/>  
```  
  
 <span data-ttu-id="87420-133">CustomData 檔案包含 <`VBMyExtensionTemplate>`具有屬性，如下表中所列的項目。</span><span class="sxs-lookup"><span data-stu-id="87420-133">The CustomData file contains a <`VBMyExtensionTemplate>` element that has attributes as listed in the following table.</span></span>  
  
|<span data-ttu-id="87420-134">屬性</span><span class="sxs-lookup"><span data-stu-id="87420-134">Attribute</span></span>|<span data-ttu-id="87420-135">描述</span><span class="sxs-lookup"><span data-stu-id="87420-135">Description</span></span>|  
|---|---|  
|`ID`|<span data-ttu-id="87420-136">必要。</span><span class="sxs-lookup"><span data-stu-id="87420-136">Required.</span></span> <span data-ttu-id="87420-137">延伸模組的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="87420-137">A unique identifier for the extension.</span></span> <span data-ttu-id="87420-138">如果具有此識別碼的擴充功能已加入專案中，新增一次不會提示使用者。</span><span class="sxs-lookup"><span data-stu-id="87420-138">If the extension that has this ID has already been added to the project, the user will not be prompted to add it again.</span></span>|  
|`Version`|<span data-ttu-id="87420-139">必要。</span><span class="sxs-lookup"><span data-stu-id="87420-139">Required.</span></span> <span data-ttu-id="87420-140">項目範本的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="87420-140">A version number for the item template.</span></span>|  
|`AssemblyFullName`|<span data-ttu-id="87420-141">選擇性。</span><span class="sxs-lookup"><span data-stu-id="87420-141">Optional.</span></span> <span data-ttu-id="87420-142">組件名稱。</span><span class="sxs-lookup"><span data-stu-id="87420-142">An assembly name.</span></span> <span data-ttu-id="87420-143">當此組件的參考加入至專案時，會提示使用者加入`My`延伸模組，從這個項目範本。</span><span class="sxs-lookup"><span data-stu-id="87420-143">When a reference to this assembly is added to the project, the user will be prompted to add the `My` extension from this item template.</span></span>|  
  
### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a><span data-ttu-id="87420-144">新增\<CustomDataSignature > 的.vstemplate 檔的項目</span><span class="sxs-lookup"><span data-stu-id="87420-144">Add the \<CustomDataSignature> element to the .vstemplate file</span></span>  
 <span data-ttu-id="87420-145">若要識別您的 Visual Studio 項目範本作為`My`命名空間擴充功能，您也必須修改.vstemplate 檔案的項目範本。</span><span class="sxs-lookup"><span data-stu-id="87420-145">To identify your Visual Studio item template as a `My` namespace extension, you must also modify the .vstemplate file for your item template.</span></span> <span data-ttu-id="87420-146">您必須新增`<CustomDataSignature>`元素`<TemplateData>`項目。</span><span class="sxs-lookup"><span data-stu-id="87420-146">You must add a `<CustomDataSignature>` element to the `<TemplateData>` element.</span></span> <span data-ttu-id="87420-147">`<CustomDataSignature>`元素必須包含文字`Microsoft.VisualBasic.MyExtension`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="87420-147">The `<CustomDataSignature>` element must contain the text `Microsoft.VisualBasic.MyExtension`, as shown in the following example.</span></span>  
  
```xml  
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>  
```  
  
 <span data-ttu-id="87420-148">您無法直接修改壓縮的資料夾 （.zip 檔） 中的檔案。</span><span class="sxs-lookup"><span data-stu-id="87420-148">You cannot modify files in a compressed folder (.zip file) directly.</span></span> <span data-ttu-id="87420-149">您必須複製.vstemplate 檔案從壓縮的資料夾、 修改它，並使用更新的複本取代.vstemplate 檔案，將壓縮資料夾中。</span><span class="sxs-lookup"><span data-stu-id="87420-149">You must copy the .vstemplate file from the compressed folder, modify it, and then replace the .vstemplate file in the compressed folder with your updated copy.</span></span>  
  
 <span data-ttu-id="87420-150">下列範例示範具有.vstemplate 檔案的內容`<CustomDataSignature>`加入項目。</span><span class="sxs-lookup"><span data-stu-id="87420-150">The following example shows the contents of a .vstemplate file that has the `<CustomDataSignature>` element added.</span></span>  
  
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
  
## <a name="install-the-template"></a><span data-ttu-id="87420-151">安裝範本</span><span class="sxs-lookup"><span data-stu-id="87420-151">Install the template</span></span>  
 <span data-ttu-id="87420-152">若要安裝的範本，您可以將壓縮的資料夾 （.zip 檔案） 複製到 Visual Basic 項目範本資料夾 （例如，My Documents\Visual Studio 2008\Templates\Item Templates\Visual 基本）。</span><span class="sxs-lookup"><span data-stu-id="87420-152">To install the template, you can copy the compressed folder (.zip file) to the Visual Basic item templates folder (for example, My Documents\Visual Studio 2008\Templates\Item Templates\Visual Basic).</span></span> <span data-ttu-id="87420-153">或者，您可以為 Visual Studio 安裝程式 (.vsi) 檔案發佈的範本。</span><span class="sxs-lookup"><span data-stu-id="87420-153">Alternatively, you can publish the template as a Visual Studio Installer (.vsi) file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87420-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87420-154">See also</span></span>  
 [<span data-ttu-id="87420-155">擴充 Visual Basic 中的 My 命名空間</span><span class="sxs-lookup"><span data-stu-id="87420-155">Extending the My Namespace in Visual Basic</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)  
 [<span data-ttu-id="87420-156">擴充 Visual Basic 應用程式模型</span><span class="sxs-lookup"><span data-stu-id="87420-156">Extending the Visual Basic Application Model</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)  
 [<span data-ttu-id="87420-157">自訂 My 中可用的物件</span><span class="sxs-lookup"><span data-stu-id="87420-157">Customizing Which Objects are Available in My</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)  
 [<span data-ttu-id="87420-158">專案設計工具 my 擴充頁</span><span class="sxs-lookup"><span data-stu-id="87420-158">My Extensions Page, Project Designer</span></span>](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)

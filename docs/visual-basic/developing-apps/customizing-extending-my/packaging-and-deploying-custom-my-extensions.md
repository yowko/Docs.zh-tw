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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 81483722227873d1b145219ae5c4326d841ff876
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="packaging-and-deploying-custom-my-extensions-visual-basic"></a><span data-ttu-id="578db-102">封裝和部署自訂的 My 擴充 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="578db-102">Packaging and deploying custom My extensions (Visual Basic)</span></span>
<span data-ttu-id="578db-103">Visual Basic 提供簡單的方法，您才能部署您的自訂`My`命名空間擴充，使用 Visual Studio 範本。</span><span class="sxs-lookup"><span data-stu-id="578db-103">Visual Basic provides an easy way for you to deploy your custom `My` namespace extensions by using Visual Studio templates.</span></span> <span data-ttu-id="578db-104">如果您要建立專案範本，您`My`延伸模組是新的專案類型中不可或缺的一部分，您可以包含自訂`My`延伸模組程式碼專案中，當您匯出的範本。</span><span class="sxs-lookup"><span data-stu-id="578db-104">If you are creating a project template for which your `My` extensions are an integral part of the new project type, you can just include your custom `My` extension code with the project when you export the template.</span></span> <span data-ttu-id="578db-105">如需匯出專案範本的詳細資訊，請參閱[How to︰ 建立專案範本](http://msdn.microsoft.com/library/a1a6999d-a34c-48a8-b1cf-027eb5c76398)。</span><span class="sxs-lookup"><span data-stu-id="578db-105">For more information about exporting project templates, see [How to: Create Project Templates](http://msdn.microsoft.com/library/a1a6999d-a34c-48a8-b1cf-027eb5c76398).</span></span>  
  
 <span data-ttu-id="578db-106">如果您的自訂`My`延伸模組是在單一程式碼檔案中，您可以將檔案匯出成項目範本讓使用者可以加入至任何類型的 Visual Basic 專案。</span><span class="sxs-lookup"><span data-stu-id="578db-106">If your custom `My` extension is in a single code file, you can export the file as an item template that users can add to any type of Visual Basic project.</span></span> <span data-ttu-id="578db-107">您可以自訂項目範本，若要啟用其他功能與您的自訂行為`My`Visual Basic 專案中的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="578db-107">You can then customize the item template to enable additional capabilities and behavior for your custom `My` extension in a Visual Basic project.</span></span> <span data-ttu-id="578db-108">這些功能包括︰</span><span class="sxs-lookup"><span data-stu-id="578db-108">Those capabilities include the following:</span></span>  
  
-   <span data-ttu-id="578db-109">允許使用者管理您的自訂`My`副檔名， **My 擴充**Visual Basic 專案設計工具頁面。</span><span class="sxs-lookup"><span data-stu-id="578db-109">Allowing users to manage your custom `My` extension from the **My Extensions** page of the Visual Basic Project Designer.</span></span>  
  
-   <span data-ttu-id="578db-110">自動新增您的自訂`My`延伸模組時指定的組件的參考加入至專案。</span><span class="sxs-lookup"><span data-stu-id="578db-110">Automatically adding your custom `My` extension when a reference to a specified assembly is added to a project.</span></span>  
  
-   <span data-ttu-id="578db-111">隱藏`My`延伸模組中的項目範本**加入項目**對話方塊，讓它不會納入專案項目的清單。</span><span class="sxs-lookup"><span data-stu-id="578db-111">Hiding the `My` extension item template in the **Add Item** dialog box so that it is not included in the list of project items.</span></span>  
  
 <span data-ttu-id="578db-112">本主題討論如何將封裝自訂`My`副檔名為隱藏的項目範本，可從**My 擴充**Visual Basic 專案設計工具頁面。</span><span class="sxs-lookup"><span data-stu-id="578db-112">This topic discusses how to package a custom `My` extension as a hidden item template that can be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="578db-113">自訂`My`延伸模組也會自動加入當指定的組件的參考加入至專案。</span><span class="sxs-lookup"><span data-stu-id="578db-113">The custom `My` extension can also be added automatically when a reference to a specified assembly is added to a project.</span></span>  
  
## <a name="create-a-my-namespace-extension"></a><span data-ttu-id="578db-114">建立 My 命名空間擴充</span><span class="sxs-lookup"><span data-stu-id="578db-114">Create a My namespace extension</span></span>  
 <span data-ttu-id="578db-115">建立自訂的部署封裝的第一個步驟`My`擴充功能是建立一個程式碼檔案的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="578db-115">The first step in creating a deployment package for a custom `My` extension is to create the extension as a single code file.</span></span> <span data-ttu-id="578db-116">如需詳細資訊和有關如何建立自訂的指引`My`延伸模組，請參閱[擴充 My 命名空間，在 Visual Basic 中](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="578db-116">For details and guidance about how to create a custom `My` extension, see [Extending the My Namespace in Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).</span></span>  
  
## <a name="export-a-my-namespace-extension-as-an-item-template"></a><span data-ttu-id="578db-117">匯出為項目範本的 My 命名空間擴充</span><span class="sxs-lookup"><span data-stu-id="578db-117">Export a My namespace extension as an item template</span></span>  
 <span data-ttu-id="578db-118">包含的程式碼檔案之後您`My`命名空間擴充，您可以將程式碼檔匯出為 Visual Studio 項目範本。</span><span class="sxs-lookup"><span data-stu-id="578db-118">After you have a code file that includes your `My` namespace extension, you can export the code file as a Visual Studio item template.</span></span> <span data-ttu-id="578db-119">如需如何將檔案匯出成 Visual Studio 項目範本的指示，請參閱[How to︰ 建立項目範本](http://msdn.microsoft.com/library/77bc53d4-d607-4820-a032-7e3b365891b5)。</span><span class="sxs-lookup"><span data-stu-id="578db-119">For instructions on how to export a file as a Visual Studio item template, see [How to: Create Item Templates](http://msdn.microsoft.com/library/77bc53d4-d607-4820-a032-7e3b365891b5).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="578db-120">如果您`My`命名空間擴充具有特定的組件相依性，您可以自訂項目範本，以自動安裝您`My`命名空間擴充功能時在加入該組件的參考。</span><span class="sxs-lookup"><span data-stu-id="578db-120">If your `My` namespace extension has a dependency on a particular assembly, you can customize your item template to automatically install your `My` namespace extension when a reference to that assembly is added.</span></span> <span data-ttu-id="578db-121">如此一來，您會想要排除的組件參考，當您匯出的程式碼檔案做為 Visual Studio 項目範本。</span><span class="sxs-lookup"><span data-stu-id="578db-121">As a result, you will want to exclude that assembly reference when you export the code file as a Visual Studio item template.</span></span>  
  
## <a name="customize-the-item-template"></a><span data-ttu-id="578db-122">自訂項目範本</span><span class="sxs-lookup"><span data-stu-id="578db-122">Customize the item template</span></span>  
 <span data-ttu-id="578db-123">您可以啟用項目範本，從管理**My 擴充**Visual Basic 專案設計工具頁面。</span><span class="sxs-lookup"><span data-stu-id="578db-123">You can enable your item template to be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="578db-124">您也可以啟用指定的組件的參考加入至專案時，自動新增項目範本。</span><span class="sxs-lookup"><span data-stu-id="578db-124">You can also enable the item template to be added automatically when a reference to a specified assembly is added to a project.</span></span> <span data-ttu-id="578db-125">若要啟用這些自訂項目，您將會新增一個新的檔案，稱為 CustomData 檔案，您的範本，並新增新的項目 xml.vstemplate 檔案中。</span><span class="sxs-lookup"><span data-stu-id="578db-125">To enable these customizations, you will add a new file, called the CustomData file, to your template, and then add a new element to the XML in your .vstemplate file.</span></span>  
  
### <a name="add-the-customdata-file"></a><span data-ttu-id="578db-126">加入 CustomData 檔案</span><span class="sxs-lookup"><span data-stu-id="578db-126">Add the CustomData file</span></span>  
 <span data-ttu-id="578db-127">CustomData 檔案是副檔名的文字檔。CustomData （檔案名稱可以設定為任何值有意義的範本），其中包含 XML。</span><span class="sxs-lookup"><span data-stu-id="578db-127">The CustomData file is a text file that has a file name extension of .CustomData (the file name can be set to any value meaningful to your template) and that contains XML.</span></span> <span data-ttu-id="578db-128">CustomData 檔案中的 XML 會指示 Visual Basic，以包含您`My`延伸模組，當使用者使用**My 擴充**Visual Basic 專案設計工具頁面。</span><span class="sxs-lookup"><span data-stu-id="578db-128">The XML in the CustomData file instructs Visual Basic to include your `My` extension when users use the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="578db-129">您可以選擇性地加入`AssemblyFullName>`CustomData 檔的 XML 屬性。</span><span class="sxs-lookup"><span data-stu-id="578db-129">You can optionally add the <`AssemblyFullName>` attribute to your CustomData file XML.</span></span> <span data-ttu-id="578db-130">這會指示 Visual Basic，以自動安裝您的自訂`My`延伸模組，當特定的組件的參考加入至專案。</span><span class="sxs-lookup"><span data-stu-id="578db-130">This instructs Visual Basic to automatically install your custom `My` extension when a reference to a particular assembly is added to the project.</span></span> <span data-ttu-id="578db-131">您可以使用任何文字編輯器或 XML 編輯器建立 CustomData 檔案，並將其加入項目範本的壓縮資料夾 （.zip 檔案）。</span><span class="sxs-lookup"><span data-stu-id="578db-131">You can use any text editor or XML editor to create the CustomData file, and then add it to your item template's compressed folder (.zip file).</span></span>  
  
 <span data-ttu-id="578db-132">例如，下列 XML 顯示 CustomData 檔案會將範本項目加入至 Microsoft.VisualBasic.PowerPacks.Vs.dll 組件的參考時，Visual Basic 專案的 My 擴充資料夾的內容加入至專案。</span><span class="sxs-lookup"><span data-stu-id="578db-132">For example, the following XML shows the contents of a CustomData file that will add the template item to the My Extensions folder of a Visual Basic project when a reference to the Microsoft.VisualBasic.PowerPacks.Vs.dll assembly is added to the project.</span></span>  
  
```  
<VBMyExtensionTemplate   
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"   
    Version="1.0.0.0"  
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"  
/>  
```  
  
 <span data-ttu-id="578db-133">CustomData 檔案包含`VBMyExtensionTemplate>`具有屬性，如下列表格所列的項目。</span><span class="sxs-lookup"><span data-stu-id="578db-133">The CustomData file contains a <`VBMyExtensionTemplate>` element that has attributes as listed in the following table.</span></span>  
  
|<span data-ttu-id="578db-134">屬性</span><span class="sxs-lookup"><span data-stu-id="578db-134">Attribute</span></span>|<span data-ttu-id="578db-135">描述</span><span class="sxs-lookup"><span data-stu-id="578db-135">Description</span></span>|  
|---|---|  
|`ID`|<span data-ttu-id="578db-136">必要項。</span><span class="sxs-lookup"><span data-stu-id="578db-136">Required.</span></span> <span data-ttu-id="578db-137">延伸模組的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="578db-137">A unique identifier for the extension.</span></span> <span data-ttu-id="578db-138">如果具有此識別碼的延伸模組已加入至專案，再加入不會提示使用者。</span><span class="sxs-lookup"><span data-stu-id="578db-138">If the extension that has this ID has already been added to the project, the user will not be prompted to add it again.</span></span>|  
|`Version`|<span data-ttu-id="578db-139">必要項。</span><span class="sxs-lookup"><span data-stu-id="578db-139">Required.</span></span> <span data-ttu-id="578db-140">項目範本的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="578db-140">A version number for the item template.</span></span>|  
|`AssemblyFullName`|<span data-ttu-id="578db-141">選擇項。</span><span class="sxs-lookup"><span data-stu-id="578db-141">Optional.</span></span> <span data-ttu-id="578db-142">組件名稱。</span><span class="sxs-lookup"><span data-stu-id="578db-142">An assembly name.</span></span> <span data-ttu-id="578db-143">當此組件的參考加入至專案時，會提示使用者加入`My`副檔名，這個項目範本。</span><span class="sxs-lookup"><span data-stu-id="578db-143">When a reference to this assembly is added to the project, the user will be prompted to add the `My` extension from this item template.</span></span>|  
  
### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a><span data-ttu-id="578db-144">新增\<CustomDataSignature > 的.vstemplate 檔的項目</span><span class="sxs-lookup"><span data-stu-id="578db-144">Add the \<CustomDataSignature> element to the .vstemplate file</span></span>  
 <span data-ttu-id="578db-145">若要識別您的 Visual Studio 項目範本，作為`My`命名空間擴充，您也必須修改項目範本的.vstemplate 檔。</span><span class="sxs-lookup"><span data-stu-id="578db-145">To identify your Visual Studio item template as a `My` namespace extension, you must also modify the .vstemplate file for your item template.</span></span> <span data-ttu-id="578db-146">您必須新增`<CustomDataSignature>`項目`<TemplateData>`項目。</span><span class="sxs-lookup"><span data-stu-id="578db-146">You must add a `<CustomDataSignature>` element to the `<TemplateData>` element.</span></span> <span data-ttu-id="578db-147">`<CustomDataSignature>`元素必須包含文字`Microsoft.VisualBasic.MyExtension`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="578db-147">The `<CustomDataSignature>` element must contain the text `Microsoft.VisualBasic.MyExtension`, as shown in the following example.</span></span>  
  
```  
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>  
```  
  
 <span data-ttu-id="578db-148">您無法直接修改壓縮的資料夾 （.zip 檔案） 中的檔案。</span><span class="sxs-lookup"><span data-stu-id="578db-148">You cannot modify files in a compressed folder (.zip file) directly.</span></span> <span data-ttu-id="578db-149">您必須從壓縮資料夾中複製.vstemplate 檔案，進行修改，然後將壓縮資料夾中的.vstemplate 檔取代更新的複製。</span><span class="sxs-lookup"><span data-stu-id="578db-149">You must copy the .vstemplate file from the compressed folder, modify it, and then replace the .vstemplate file in the compressed folder with your updated copy.</span></span>  
  
 <span data-ttu-id="578db-150">下列範例顯示具有.vstemplate 檔案的內容`<CustomDataSignature>`加入項目。</span><span class="sxs-lookup"><span data-stu-id="578db-150">The following example shows the contents of a .vstemplate file that has the `<CustomDataSignature>` element added.</span></span>  
  
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
  
## <a name="install-the-template"></a><span data-ttu-id="578db-151">安裝的範本</span><span class="sxs-lookup"><span data-stu-id="578db-151">Install the template</span></span>  
 <span data-ttu-id="578db-152">若要安裝的範本，您可以將壓縮的資料夾 （.zip 檔案） 複製到 Visual Basic 項目範本資料夾 （例如 My Documents\Visual Studio 2008\Templates\Item templates\item Templates\Visual 基本）。</span><span class="sxs-lookup"><span data-stu-id="578db-152">To install the template, you can copy the compressed folder (.zip file) to the Visual Basic item templates folder (for example, My Documents\Visual Studio 2008\Templates\Item Templates\Visual Basic).</span></span> <span data-ttu-id="578db-153">或者，您可以發行範本，為 Visual Studio 安裝程式 (.vsi) 檔案。</span><span class="sxs-lookup"><span data-stu-id="578db-153">Alternatively, you can publish the template as a Visual Studio Installer (.vsi) file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="578db-154">請參閱</span><span class="sxs-lookup"><span data-stu-id="578db-154">See also</span></span>  
 <span data-ttu-id="578db-155">[擴充 Visual Basic 中的 My 命名空間](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md) </span><span class="sxs-lookup"><span data-stu-id="578db-155">[Extending the My Namespace in Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md) </span></span>  
<span data-ttu-id="578db-156"> [擴充 Visual Basic 應用程式模型](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md) </span><span class="sxs-lookup"><span data-stu-id="578db-156"> [Extending the Visual Basic Application Model](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md) </span></span>  
<span data-ttu-id="578db-157"> [自訂可用的物件在我](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md) </span><span class="sxs-lookup"><span data-stu-id="578db-157"> [Customizing Which Objects are Available in My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md) </span></span>  
<span data-ttu-id="578db-158"> [專案設計工具 my 擴充頁](https://docs.microsoft.com/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)</span><span class="sxs-lookup"><span data-stu-id="578db-158"> [My Extensions Page, Project Designer](https://docs.microsoft.com/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)</span></span>

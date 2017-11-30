---
title: "My.Resources 物件"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- My.Resources
- My.Resources.MyResources.ResourceManager
- My.Resources.MyResources.Culture
helpviewer_keywords: My.Resources object
ms.assetid: 34c3f2dc-7b87-432c-9d5f-17ea666bb266
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b2a2de7229f59e7deea29fe4186a5e466459d9fa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="myresources-object"></a><span data-ttu-id="83bf1-102">My.Resources 物件</span><span class="sxs-lookup"><span data-stu-id="83bf1-102">My.Resources Object</span></span>
<span data-ttu-id="83bf1-103">提供屬性和類別來存取應用程式的資源。</span><span class="sxs-lookup"><span data-stu-id="83bf1-103">Provides properties and classes for accessing the application's resources.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83bf1-104">備註</span><span class="sxs-lookup"><span data-stu-id="83bf1-104">Remarks</span></span>  
 <span data-ttu-id="83bf1-105">`My.Resources`物件提供存取應用程式的資源，並可讓您以動態方式擷取資源應用程式。</span><span class="sxs-lookup"><span data-stu-id="83bf1-105">The `My.Resources` object provides access to the application's resources and lets you dynamically retrieve resources for your application.</span></span> <span data-ttu-id="83bf1-106">如需詳細資訊，請參閱[管理應用程式資源 (.NET)](/visualstudio/ide/managing-application-resources-dotnet)。</span><span class="sxs-lookup"><span data-stu-id="83bf1-106">For more information, see [Managing Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
 <span data-ttu-id="83bf1-107">`My.Resources`物件會公開只有全域資源。</span><span class="sxs-lookup"><span data-stu-id="83bf1-107">The `My.Resources` object exposes only global resources.</span></span> <span data-ttu-id="83bf1-108">它不提供與表單相關聯的資源檔案的存取權。</span><span class="sxs-lookup"><span data-stu-id="83bf1-108">It does not provide access to resource files associated with forms.</span></span> <span data-ttu-id="83bf1-109">您必須在表單中存取的表單資源。</span><span class="sxs-lookup"><span data-stu-id="83bf1-109">You must access the form resources from the form.</span></span> <span data-ttu-id="83bf1-110">如需詳細資訊，請參閱[逐步解說：將 Windows Forms 當地語系化](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5)。</span><span class="sxs-lookup"><span data-stu-id="83bf1-110">For more information, see [Walkthrough: Localizing Windows Forms](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5).</span></span>  
  
 <span data-ttu-id="83bf1-111">您可以存取應用程式的特定文化特性資源檔從`My.Resources`物件。</span><span class="sxs-lookup"><span data-stu-id="83bf1-111">You can access the application's culture-specific resource files from the `My.Resources` object.</span></span> <span data-ttu-id="83bf1-112">根據預設，`My.Resources`物件查閱比對中的文化特性資源檔中的資源<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="83bf1-112">By default, the `My.Resources` object looks up resources from the resource file that matches the culture in the <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A> property.</span></span> <span data-ttu-id="83bf1-113">不過，您可以覆寫這個行為，並指定要用於資源的特定文化特性。</span><span class="sxs-lookup"><span data-stu-id="83bf1-113">However, you can override this behavior and specify a particular culture to use for the resources.</span></span> <span data-ttu-id="83bf1-114">如需詳細資訊，請參閱[桌面應用程式中的資源](../../../framework/resources/index.md)。</span><span class="sxs-lookup"><span data-stu-id="83bf1-114">For more information, see [Resources in Desktop Apps](../../../framework/resources/index.md).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="83bf1-115">屬性</span><span class="sxs-lookup"><span data-stu-id="83bf1-115">Properties</span></span>  
 <span data-ttu-id="83bf1-116">內容`My.Resources`物件提供唯讀存取您的應用程式資源。</span><span class="sxs-lookup"><span data-stu-id="83bf1-116">The properties of the `My.Resources` object provide read-only access to your application's resources.</span></span> <span data-ttu-id="83bf1-117">若要新增或移除資源，使用**專案設計工具**。</span><span class="sxs-lookup"><span data-stu-id="83bf1-117">To add or remove resources, use the **Project Designer**.</span></span> <span data-ttu-id="83bf1-118">如需詳細資訊，請參閱[如何： 加入或移除資源](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d)。</span><span class="sxs-lookup"><span data-stu-id="83bf1-118">For more information, see [How to: Add or Remove Resources](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d).</span></span> <span data-ttu-id="83bf1-119">您可以存取資源，透過新增**專案設計工具**使用`My.Resources.``resourceName`。</span><span class="sxs-lookup"><span data-stu-id="83bf1-119">You can access resources added through the **Project Designer** by using `My.Resources.``resourceName`.</span></span>  
  
 <span data-ttu-id="83bf1-120">您也可以新增或移除選取的專案中的資源檔**方案總管 中**按一下**加入新項目**或**加入現有項目**從**專案**功能表。</span><span class="sxs-lookup"><span data-stu-id="83bf1-120">You can also add or remove resource files by selecting your project in **Solution Explorer** and clicking **Add New Item** or **Add Existing Item** from the **Project** menu.</span></span> <span data-ttu-id="83bf1-121">您可以存取資源利用這個方式加入`My.Resources.``resourceFileName`.`resourceName`。</span><span class="sxs-lookup"><span data-stu-id="83bf1-121">You can access resources added in this manner by using `My.Resources.``resourceFileName`.`resourceName`.</span></span>  
  
 <span data-ttu-id="83bf1-122">每個資源都有名稱、 類別目錄和值，以及這些資源的設定會決定要存取資源的屬性會出現在`My.Resources`物件。</span><span class="sxs-lookup"><span data-stu-id="83bf1-122">Each resource has a name, category, and value, and these resource settings determine how the property to access the resource appears in the `My.Resources` object.</span></span> <span data-ttu-id="83bf1-123">資源中加入**專案設計工具**:</span><span class="sxs-lookup"><span data-stu-id="83bf1-123">For resources added in the **Project Designer**:</span></span>  
  
-   <span data-ttu-id="83bf1-124">名稱會決定屬性的名稱</span><span class="sxs-lookup"><span data-stu-id="83bf1-124">The name determines the name of the property,</span></span>  
  
-   <span data-ttu-id="83bf1-125">資源資料是屬性的值</span><span class="sxs-lookup"><span data-stu-id="83bf1-125">The resource data is the value of the property,</span></span>  
  
-   <span data-ttu-id="83bf1-126">分類會決定屬性的型別：</span><span class="sxs-lookup"><span data-stu-id="83bf1-126">The category determines the type of the property:</span></span>  
  
|<span data-ttu-id="83bf1-127">分類</span><span class="sxs-lookup"><span data-stu-id="83bf1-127">Category</span></span>|<span data-ttu-id="83bf1-128">屬性資料型別</span><span class="sxs-lookup"><span data-stu-id="83bf1-128">Property data type</span></span>|  
|---|---|  
|<span data-ttu-id="83bf1-129">**字串**</span><span class="sxs-lookup"><span data-stu-id="83bf1-129">**Strings**</span></span>|[<span data-ttu-id="83bf1-130">String</span><span class="sxs-lookup"><span data-stu-id="83bf1-130">String</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)|  
|<span data-ttu-id="83bf1-131">**影像**</span><span class="sxs-lookup"><span data-stu-id="83bf1-131">**Images**</span></span>|<xref:System.Drawing.Bitmap>|  
|<span data-ttu-id="83bf1-132">**圖示**</span><span class="sxs-lookup"><span data-stu-id="83bf1-132">**Icons**</span></span>|<xref:System.Drawing.Icon>|  
|<span data-ttu-id="83bf1-133">**音訊**</span><span class="sxs-lookup"><span data-stu-id="83bf1-133">**Audio**</span></span>|<xref:System.IO.UnmanagedMemoryStream><br /><br /> <span data-ttu-id="83bf1-134"><xref:System.IO.UnmanagedMemoryStream>類別衍生自<xref:System.IO.Stream>類別中，因此它可以搭配這些方法會採用資料流，例如<xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="83bf1-134">The <xref:System.IO.UnmanagedMemoryStream> class derives from the <xref:System.IO.Stream> class, so it can be used with methods that take streams, such as the <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A> method.</span></span>|  
|<span data-ttu-id="83bf1-135">**檔案**</span><span class="sxs-lookup"><span data-stu-id="83bf1-135">**Files**</span></span>|<span data-ttu-id="83bf1-136">-   [字串](../../../visual-basic/language-reference/data-types/string-data-type.md)文字檔案。</span><span class="sxs-lookup"><span data-stu-id="83bf1-136">-   [String](../../../visual-basic/language-reference/data-types/string-data-type.md) for text files.</span></span><br /><span data-ttu-id="83bf1-137">-   <xref:System.Drawing.Bitmap>映像檔案。</span><span class="sxs-lookup"><span data-stu-id="83bf1-137">-   <xref:System.Drawing.Bitmap> for image files.</span></span><br /><span data-ttu-id="83bf1-138">-   <xref:System.Drawing.Icon>圖示檔案。</span><span class="sxs-lookup"><span data-stu-id="83bf1-138">-   <xref:System.Drawing.Icon> for icon files.</span></span><br /><span data-ttu-id="83bf1-139">-   <xref:System.IO.UnmanagedMemoryStream>音效檔。</span><span class="sxs-lookup"><span data-stu-id="83bf1-139">-   <xref:System.IO.UnmanagedMemoryStream> for sound files.</span></span>|  
|<span data-ttu-id="83bf1-140">**其他**</span><span class="sxs-lookup"><span data-stu-id="83bf1-140">**Other**</span></span>|<span data-ttu-id="83bf1-141">在設計工具中的資訊來決定**類型**資料行。</span><span class="sxs-lookup"><span data-stu-id="83bf1-141">Determined by the information in the designer's **Type** column.</span></span>|  
  
## <a name="classes"></a><span data-ttu-id="83bf1-142">類別</span><span class="sxs-lookup"><span data-stu-id="83bf1-142">Classes</span></span>  
 <span data-ttu-id="83bf1-143">`My.Resources`物件會公開為具有共用的屬性類別的每個資源檔。</span><span class="sxs-lookup"><span data-stu-id="83bf1-143">The `My.Resources` object exposes each resource file as a class with shared properties.</span></span> <span data-ttu-id="83bf1-144">類別名稱是資源檔的名稱相同。</span><span class="sxs-lookup"><span data-stu-id="83bf1-144">The class name is the same as the name of the resource file.</span></span> <span data-ttu-id="83bf1-145">上一節所述，在資源檔中的資源會公開為類別中的屬性。</span><span class="sxs-lookup"><span data-stu-id="83bf1-145">As described in the previous section, the resources in a resource file are exposed as properties in the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83bf1-146">範例</span><span class="sxs-lookup"><span data-stu-id="83bf1-146">Example</span></span>  
 <span data-ttu-id="83bf1-147">此範例會設定表單的標題為指定的字串資源`Form1Title`應用程式資源檔中。</span><span class="sxs-lookup"><span data-stu-id="83bf1-147">This example sets the title of a form to the string resource named `Form1Title` in the application resource file.</span></span> <span data-ttu-id="83bf1-148">如範例能夠運作，應用程式必須具有名為字串`Form1Title`其資源檔中。</span><span class="sxs-lookup"><span data-stu-id="83bf1-148">For the example to work, the application must have a string named `Form1Title` in its resource file.</span></span> <span data-ttu-id="83bf1-149">如需詳細資訊，請參閱[如何： 加入或移除資源](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d)。</span><span class="sxs-lookup"><span data-stu-id="83bf1-149">For more information, see [How to: Add or Remove Resources](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d).</span></span>  
  
 [!code-vb[VbVbalrMyResources#1](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="83bf1-150">範例</span><span class="sxs-lookup"><span data-stu-id="83bf1-150">Example</span></span>  
 <span data-ttu-id="83bf1-151">這個範例會將名為圖示表單的圖示`Form1Icon`儲存應用程式的資源檔。</span><span class="sxs-lookup"><span data-stu-id="83bf1-151">This example sets the icon of the form to the icon named `Form1Icon` that is stored in the application's resource file.</span></span> <span data-ttu-id="83bf1-152">如範例能夠運作，應用程式必須具有名為圖示`Form1Icon`其資源檔中。</span><span class="sxs-lookup"><span data-stu-id="83bf1-152">For the example to work, the application must have an icon named `Form1Icon` in its resource file.</span></span>  
  
 [!code-vb[VbVbalrMyResources#2](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="83bf1-153">範例</span><span class="sxs-lookup"><span data-stu-id="83bf1-153">Example</span></span>  
 <span data-ttu-id="83bf1-154">此範例會設定表單的背景影像的影像資源，名為`Form1Background`，這是應用程式資源檔中。</span><span class="sxs-lookup"><span data-stu-id="83bf1-154">This example sets the background image of a form to the image resource named `Form1Background`, which is in the application resource file.</span></span> <span data-ttu-id="83bf1-155">要讓範例能夠運作，應用程式必須具有名為的映像資源`Form1Background`其資源檔中。</span><span class="sxs-lookup"><span data-stu-id="83bf1-155">For this example to work, the application must have an image resource named `Form1Background` in its resource file.</span></span>  
  
 [!code-vb[VbVbalrMyResources#3](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="83bf1-156">範例</span><span class="sxs-lookup"><span data-stu-id="83bf1-156">Example</span></span>  
 <span data-ttu-id="83bf1-157">此範例會播放聲音儲存為具名的音效資源`Form1Greeting`應用程式的資源檔。</span><span class="sxs-lookup"><span data-stu-id="83bf1-157">This example plays the sound that is stored as an audio resource named `Form1Greeting` in the application's resource file.</span></span> <span data-ttu-id="83bf1-158">如範例能夠運作，應用程式必須具有名為的音訊資源`Form1Greeting`其資源檔中。</span><span class="sxs-lookup"><span data-stu-id="83bf1-158">For the example to work, the application must have an audio resource named `Form1Greeting` in its resource file.</span></span> <span data-ttu-id="83bf1-159">`My.Computer.Audio.Play`方法，僅適用於 Windows Forms 應用程式。</span><span class="sxs-lookup"><span data-stu-id="83bf1-159">The `My.Computer.Audio.Play` method is available only for Windows Forms applications.</span></span>  
  
 [!code-vb[VbVbalrMyResources#4](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="83bf1-160">範例</span><span class="sxs-lookup"><span data-stu-id="83bf1-160">Example</span></span>  
 <span data-ttu-id="83bf1-161">這個範例會擷取字串資源的應用程式的法文文化特性版本。</span><span class="sxs-lookup"><span data-stu-id="83bf1-161">This example retrieves the French-culture version of a  string resource of the application.</span></span> <span data-ttu-id="83bf1-162">資源名稱為`Message`。</span><span class="sxs-lookup"><span data-stu-id="83bf1-162">The resource is named `Message`.</span></span> <span data-ttu-id="83bf1-163">若要變更文化特性的`My.Resources`物件使用，此範例會使用<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>。</span><span class="sxs-lookup"><span data-stu-id="83bf1-163">To change the culture that the `My.Resources` object uses, the example uses <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>.</span></span>  
  
 <span data-ttu-id="83bf1-164">要讓範例能夠運作，應用程式必須具有名為字串`Message`中其資源檔和應用程式不能有該資源的檔案，Resources.fr FR.resx 法文文化特性版本。</span><span class="sxs-lookup"><span data-stu-id="83bf1-164">For this example to work, the application must have a string named `Message` in its resource file, and the application should have the French-culture version of that resource file, Resources.fr-FR.resx.</span></span> <span data-ttu-id="83bf1-165">如需詳細資訊，請參閱[如何： 加入或移除資源](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d)。</span><span class="sxs-lookup"><span data-stu-id="83bf1-165">For more information, see [How to: Add or Remove Resources](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d).</span></span> <span data-ttu-id="83bf1-166">如果應用程式並沒有法文文化特性的資源檔案版本，`My.Resource`物件會從預設文化特性資源檔擷取資源。</span><span class="sxs-lookup"><span data-stu-id="83bf1-166">If the application does not have the French-culture version of the resource file, the `My.Resource` object retrieves the resource from the default-culture resource file.</span></span>  
  
 [!code-vb[VbVbalrMyResources#10](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_5.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="83bf1-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83bf1-167">See Also</span></span>  
 [<span data-ttu-id="83bf1-168">如何：新增或移除資源</span><span class="sxs-lookup"><span data-stu-id="83bf1-168">How to: Add or Remove Resources</span></span>](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d)  
 [<span data-ttu-id="83bf1-169">管理應用程式資源 (.NET)</span><span class="sxs-lookup"><span data-stu-id="83bf1-169">Managing Application Resources (.NET)</span></span>](/visualstudio/ide/managing-application-resources-dotnet)  
 [<span data-ttu-id="83bf1-170">桌面應用程式中的資源</span><span class="sxs-lookup"><span data-stu-id="83bf1-170">Resources in Desktop Apps</span></span>](../../../framework/resources/index.md)  
 [<span data-ttu-id="83bf1-171">逐步解說： 當地語系化 Windows Form</span><span class="sxs-lookup"><span data-stu-id="83bf1-171">Walkthrough: Localizing Windows Forms</span></span>](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5)

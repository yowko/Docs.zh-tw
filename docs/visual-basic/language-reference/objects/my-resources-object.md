---
title: "My.Resources 物件 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- My.Resources
- My.Resources.MyResources.ResourceManager
- My.Resources.MyResources.Culture
dev_langs:
- VB
helpviewer_keywords:
- My.Resources object
ms.assetid: 34c3f2dc-7b87-432c-9d5f-17ea666bb266
caps.latest.revision: 22
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
ms.openlocfilehash: 68d0ce69441f18f7a59cb84b0cf363eab9f98669
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="myresources-object"></a><span data-ttu-id="02f2f-102">My.Resources 物件</span><span class="sxs-lookup"><span data-stu-id="02f2f-102">My.Resources Object</span></span>
<span data-ttu-id="02f2f-103">提供屬性和類別來存取應用程式的資源。</span><span class="sxs-lookup"><span data-stu-id="02f2f-103">Provides properties and classes for accessing the application's resources.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02f2f-104">備註</span><span class="sxs-lookup"><span data-stu-id="02f2f-104">Remarks</span></span>  
 <span data-ttu-id="02f2f-105">`My.Resources`物件提供的應用程式資源的存取權，並讓您動態擷取您的應用程式的資源。</span><span class="sxs-lookup"><span data-stu-id="02f2f-105">The `My.Resources` object provides access to the application's resources and lets you dynamically retrieve resources for your application.</span></span> <span data-ttu-id="02f2f-106">如需詳細資訊，請參閱[管理應用程式資源 (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-resources-dotnet)。</span><span class="sxs-lookup"><span data-stu-id="02f2f-106">For more information, see [Managing Application Resources (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
 <span data-ttu-id="02f2f-107">`My.Resources`物件會公開只有全域資源。</span><span class="sxs-lookup"><span data-stu-id="02f2f-107">The `My.Resources` object exposes only global resources.</span></span> <span data-ttu-id="02f2f-108">它不提供與表單相關聯的資源檔案的存取權。</span><span class="sxs-lookup"><span data-stu-id="02f2f-108">It does not provide access to resource files associated with forms.</span></span> <span data-ttu-id="02f2f-109">您必須從表單存取表單資源。</span><span class="sxs-lookup"><span data-stu-id="02f2f-109">You must access the form resources from the form.</span></span> <span data-ttu-id="02f2f-110">如需詳細資訊，請參閱[逐步解說：將 Windows Forms 當地語系化](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5)。</span><span class="sxs-lookup"><span data-stu-id="02f2f-110">For more information, see [Walkthrough: Localizing Windows Forms](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5).</span></span>  
  
 <span data-ttu-id="02f2f-111">您可以存取應用程式的特定文化特性資源檔從`My.Resources`物件。</span><span class="sxs-lookup"><span data-stu-id="02f2f-111">You can access the application's culture-specific resource files from the `My.Resources` object.</span></span> <span data-ttu-id="02f2f-112">根據預設，`My.Resources`物件中查閱比對中的文化特性資源檔中的資源<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A>屬性。</xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A></span><span class="sxs-lookup"><span data-stu-id="02f2f-112">By default, the `My.Resources` object looks up resources from the resource file that matches the culture in the <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A> property.</span></span> <span data-ttu-id="02f2f-113">不過，您可以覆寫這個行為，並指定特定文化特性使用的資源。</span><span class="sxs-lookup"><span data-stu-id="02f2f-113">However, you can override this behavior and specify a particular culture to use for the resources.</span></span> <span data-ttu-id="02f2f-114">如需詳細資訊，請參閱[桌面應用程式中的資源](http://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)。</span><span class="sxs-lookup"><span data-stu-id="02f2f-114">For more information, see [Resources in Desktop Apps](http://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="02f2f-115">屬性</span><span class="sxs-lookup"><span data-stu-id="02f2f-115">Properties</span></span>  
 <span data-ttu-id="02f2f-116">屬性的`My.Resources`物件提供唯讀存取您的應用程式資源。</span><span class="sxs-lookup"><span data-stu-id="02f2f-116">The properties of the `My.Resources` object provide read-only access to your application's resources.</span></span> <span data-ttu-id="02f2f-117">若要新增或移除資源，使用**專案設計工具**。</span><span class="sxs-lookup"><span data-stu-id="02f2f-117">To add or remove resources, use the **Project Designer**.</span></span> <span data-ttu-id="02f2f-118">如需詳細資訊，請參閱[How to︰ 加入或移除資源](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d)。</span><span class="sxs-lookup"><span data-stu-id="02f2f-118">For more information, see [How to: Add or Remove Resources](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d).</span></span> <span data-ttu-id="02f2f-119">您可以存取資源，透過新增**專案設計工具**使用`My.Resources.``resourceName`。</span><span class="sxs-lookup"><span data-stu-id="02f2f-119">You can access resources added through the **Project Designer** by using `My.Resources.``resourceName`.</span></span>  
  
 <span data-ttu-id="02f2f-120">您也可以新增或移除選取的專案中的資源檔**方案總管 中**，然後按一下**加入新項目**或**加入現有項目**從**專案**功能表。</span><span class="sxs-lookup"><span data-stu-id="02f2f-120">You can also add or remove resource files by selecting your project in **Solution Explorer** and clicking **Add New Item** or **Add Existing Item** from the **Project** menu.</span></span> <span data-ttu-id="02f2f-121">您可以存取資源利用這種方式加入`My.Resources.``resourceFileName`。`resourceName`。</span><span class="sxs-lookup"><span data-stu-id="02f2f-121">You can access resources added in this manner by using `My.Resources.``resourceFileName`.`resourceName`.</span></span>  
  
 <span data-ttu-id="02f2f-122">每個資源都有名稱、 類別目錄和值，以及這些資源設定會決定要存取資源的屬性會出現在`My.Resources`物件。</span><span class="sxs-lookup"><span data-stu-id="02f2f-122">Each resource has a name, category, and value, and these resource settings determine how the property to access the resource appears in the `My.Resources` object.</span></span> <span data-ttu-id="02f2f-123">加入資源**專案設計工具**:</span><span class="sxs-lookup"><span data-stu-id="02f2f-123">For resources added in the **Project Designer**:</span></span>  
  
-   <span data-ttu-id="02f2f-124">名稱會決定屬性的名稱</span><span class="sxs-lookup"><span data-stu-id="02f2f-124">The name determines the name of the property,</span></span>  
  
-   <span data-ttu-id="02f2f-125">資源資料是屬性的值</span><span class="sxs-lookup"><span data-stu-id="02f2f-125">The resource data is the value of the property,</span></span>  
  
-   <span data-ttu-id="02f2f-126">分類會決定屬性的型別︰</span><span class="sxs-lookup"><span data-stu-id="02f2f-126">The category determines the type of the property:</span></span>  
  
|<span data-ttu-id="02f2f-127">分類</span><span class="sxs-lookup"><span data-stu-id="02f2f-127">Category</span></span>|<span data-ttu-id="02f2f-128">屬性資料型別</span><span class="sxs-lookup"><span data-stu-id="02f2f-128">Property data type</span></span>|  
|---|---|  
|<span data-ttu-id="02f2f-129">**字串**</span><span class="sxs-lookup"><span data-stu-id="02f2f-129">**Strings**</span></span>|[<span data-ttu-id="02f2f-130">String</span><span class="sxs-lookup"><span data-stu-id="02f2f-130">String</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)|  
|<span data-ttu-id="02f2f-131">**映像**</span><span class="sxs-lookup"><span data-stu-id="02f2f-131">**Images**</span></span>|<span data-ttu-id="02f2f-132"><xref:System.Drawing.Bitmap></xref:System.Drawing.Bitmap></span><span class="sxs-lookup"><span data-stu-id="02f2f-132"><xref:System.Drawing.Bitmap></span></span>|  
|<span data-ttu-id="02f2f-133">**圖示**</span><span class="sxs-lookup"><span data-stu-id="02f2f-133">**Icons**</span></span>|<span data-ttu-id="02f2f-134"><xref:System.Drawing.Icon></xref:System.Drawing.Icon></span><span class="sxs-lookup"><span data-stu-id="02f2f-134"><xref:System.Drawing.Icon></span></span>|  
|<span data-ttu-id="02f2f-135">**音訊**</span><span class="sxs-lookup"><span data-stu-id="02f2f-135">**Audio**</span></span>|<span data-ttu-id="02f2f-136"><xref:System.IO.UnmanagedMemoryStream></xref:System.IO.UnmanagedMemoryStream></span><span class="sxs-lookup"><span data-stu-id="02f2f-136"><xref:System.IO.UnmanagedMemoryStream></span></span><br /><br /> <span data-ttu-id="02f2f-137"><xref:System.IO.UnmanagedMemoryStream>類別衍生自<xref:System.IO.Stream>類別，因此採用資料流，例如方法搭配<xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>方法。</xref:Microsoft.VisualBasic.Devices.Audio.Play%2A> </xref:System.IO.Stream> </xref:System.IO.UnmanagedMemoryStream></span><span class="sxs-lookup"><span data-stu-id="02f2f-137">The <xref:System.IO.UnmanagedMemoryStream> class derives from the <xref:System.IO.Stream> class, so it can be used with methods that take streams, such as the <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A> method.</span></span>|  
|<span data-ttu-id="02f2f-138">**檔案**</span><span class="sxs-lookup"><span data-stu-id="02f2f-138">**Files**</span></span>|<span data-ttu-id="02f2f-139">-   [字串](../../../visual-basic/language-reference/data-types/string-data-type.md)的文字檔案。</span><span class="sxs-lookup"><span data-stu-id="02f2f-139">-   [String](../../../visual-basic/language-reference/data-types/string-data-type.md) for text files.</span></span><br /><span data-ttu-id="02f2f-140">-<xref:System.Drawing.Bitmap>映像檔案。</xref:System.Drawing.Bitmap></span><span class="sxs-lookup"><span data-stu-id="02f2f-140">-   <xref:System.Drawing.Bitmap> for image files.</span></span><br /><span data-ttu-id="02f2f-141">-<xref:System.Drawing.Icon>的圖示檔案。</xref:System.Drawing.Icon></span><span class="sxs-lookup"><span data-stu-id="02f2f-141">-   <xref:System.Drawing.Icon> for icon files.</span></span><br /><span data-ttu-id="02f2f-142">-<xref:System.IO.UnmanagedMemoryStream>音效檔。</xref:System.IO.UnmanagedMemoryStream></span><span class="sxs-lookup"><span data-stu-id="02f2f-142">-   <xref:System.IO.UnmanagedMemoryStream> for sound files.</span></span>|  
|<span data-ttu-id="02f2f-143">**其他**</span><span class="sxs-lookup"><span data-stu-id="02f2f-143">**Other**</span></span>|<span data-ttu-id="02f2f-144">在設計工具中的資訊來決定**類型**資料行。</span><span class="sxs-lookup"><span data-stu-id="02f2f-144">Determined by the information in the designer's **Type** column.</span></span>|  
  
## <a name="classes"></a><span data-ttu-id="02f2f-145">類別</span><span class="sxs-lookup"><span data-stu-id="02f2f-145">Classes</span></span>  
 <span data-ttu-id="02f2f-146">`My.Resources`物件會公開為具有共用屬性的類別的每個資源檔。</span><span class="sxs-lookup"><span data-stu-id="02f2f-146">The `My.Resources` object exposes each resource file as a class with shared properties.</span></span> <span data-ttu-id="02f2f-147">類別名稱是資源檔的名稱相同。</span><span class="sxs-lookup"><span data-stu-id="02f2f-147">The class name is the same as the name of the resource file.</span></span> <span data-ttu-id="02f2f-148">上一節所述，在資源檔中的資源會公開為類別中的屬性。</span><span class="sxs-lookup"><span data-stu-id="02f2f-148">As described in the previous section, the resources in a resource file are exposed as properties in the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02f2f-149">範例</span><span class="sxs-lookup"><span data-stu-id="02f2f-149">Example</span></span>  
 <span data-ttu-id="02f2f-150">本範例將表單的標題設定為指定的字串資源`Form1Title`應用程式資源檔中。</span><span class="sxs-lookup"><span data-stu-id="02f2f-150">This example sets the title of a form to the string resource named `Form1Title` in the application resource file.</span></span> <span data-ttu-id="02f2f-151">若要使用的範例，請應用程式必須具有名為的字串`Form1Title`其資源檔中。</span><span class="sxs-lookup"><span data-stu-id="02f2f-151">For the example to work, the application must have a string named `Form1Title` in its resource file.</span></span> <span data-ttu-id="02f2f-152">如需詳細資訊，請參閱[How to︰ 加入或移除資源](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d)。</span><span class="sxs-lookup"><span data-stu-id="02f2f-152">For more information, see [How to: Add or Remove Resources](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d).</span></span>  
  
 <span data-ttu-id="02f2f-153">[!code-vb[VbVbalrMyResources #&1;](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="02f2f-153">[!code-vb[VbVbalrMyResources#1](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_1.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="02f2f-154">範例</span><span class="sxs-lookup"><span data-stu-id="02f2f-154">Example</span></span>  
 <span data-ttu-id="02f2f-155">這個範例會將名為圖示表單的圖示`Form1Icon`均會儲存在應用程式的資源檔中。</span><span class="sxs-lookup"><span data-stu-id="02f2f-155">This example sets the icon of the form to the icon named `Form1Icon` that is stored in the application's resource file.</span></span> <span data-ttu-id="02f2f-156">範例能夠運作，如應用程式必須具有名為圖示`Form1Icon`其資源檔中。</span><span class="sxs-lookup"><span data-stu-id="02f2f-156">For the example to work, the application must have an icon named `Form1Icon` in its resource file.</span></span>  
  
 <span data-ttu-id="02f2f-157">[!code-vb[VbVbalrMyResources #&2;](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="02f2f-157">[!code-vb[VbVbalrMyResources#2](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_2.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="02f2f-158">範例</span><span class="sxs-lookup"><span data-stu-id="02f2f-158">Example</span></span>  
 <span data-ttu-id="02f2f-159">本範例將表單的背景影像為指定的影像資源`Form1Background`，這是應用程式資源檔中。</span><span class="sxs-lookup"><span data-stu-id="02f2f-159">This example sets the background image of a form to the image resource named `Form1Background`, which is in the application resource file.</span></span> <span data-ttu-id="02f2f-160">讓範例能夠運作，應用程式必須有具名的影像資源`Form1Background`其資源檔中。</span><span class="sxs-lookup"><span data-stu-id="02f2f-160">For this example to work, the application must have an image resource named `Form1Background` in its resource file.</span></span>  
  
 <span data-ttu-id="02f2f-161">[!code-vb[VbVbalrMyResources #&3;](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="02f2f-161">[!code-vb[VbVbalrMyResources#3](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_3.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="02f2f-162">範例</span><span class="sxs-lookup"><span data-stu-id="02f2f-162">Example</span></span>  
 <span data-ttu-id="02f2f-163">此範例會播放的音效，儲存為音訊資源名為`Form1Greeting`應用程式的資源檔中。</span><span class="sxs-lookup"><span data-stu-id="02f2f-163">This example plays the sound that is stored as an audio resource named `Form1Greeting` in the application's resource file.</span></span> <span data-ttu-id="02f2f-164">範例能夠運作，如應用程式必須具有名為的音效資源`Form1Greeting`其資源檔中。</span><span class="sxs-lookup"><span data-stu-id="02f2f-164">For the example to work, the application must have an audio resource named `Form1Greeting` in its resource file.</span></span> <span data-ttu-id="02f2f-165">`My.Computer.Audio.Play`方法，僅適用於 Windows Form 應用程式。</span><span class="sxs-lookup"><span data-stu-id="02f2f-165">The `My.Computer.Audio.Play` method is available only for Windows Forms applications.</span></span>  
  
 <span data-ttu-id="02f2f-166">[!code-vb[VbVbalrMyResources #&4;](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="02f2f-166">[!code-vb[VbVbalrMyResources#4](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_4.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="02f2f-167">範例</span><span class="sxs-lookup"><span data-stu-id="02f2f-167">Example</span></span>  
 <span data-ttu-id="02f2f-168">此範例會擷取字串資源的應用程式的法文文化特性版本。</span><span class="sxs-lookup"><span data-stu-id="02f2f-168">This example retrieves the French-culture version of a  string resource of the application.</span></span> <span data-ttu-id="02f2f-169">資源名稱為`Message`。</span><span class="sxs-lookup"><span data-stu-id="02f2f-169">The resource is named `Message`.</span></span> <span data-ttu-id="02f2f-170">若要變更文化特性的`My.Resources`物件使用，此範例會使用<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>。</xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A></span><span class="sxs-lookup"><span data-stu-id="02f2f-170">To change the culture that the `My.Resources` object uses, the example uses <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>.</span></span>  
  
 <span data-ttu-id="02f2f-171">這個範例能夠運作，如應用程式必須具有名為的字串`Message`其資源中檔案和應用程式應該具有該資源檔 Resources.fr FR.resx 法文文化特性版本。</span><span class="sxs-lookup"><span data-stu-id="02f2f-171">For this example to work, the application must have a string named `Message` in its resource file, and the application should have the French-culture version of that resource file, Resources.fr-FR.resx.</span></span> <span data-ttu-id="02f2f-172">如需詳細資訊，請參閱[How to︰ 加入或移除資源](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d)。</span><span class="sxs-lookup"><span data-stu-id="02f2f-172">For more information, see [How to: Add or Remove Resources](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d).</span></span> <span data-ttu-id="02f2f-173">如果應用程式並沒有資源檔的法文文化特性版本`My.Resource`物件會從預設文化特性資源檔擷取資源。</span><span class="sxs-lookup"><span data-stu-id="02f2f-173">If the application does not have the French-culture version of the resource file, the `My.Resource` object retrieves the resource from the default-culture resource file.</span></span>  
  
 <span data-ttu-id="02f2f-174">[!code-vb[VbVbalrMyResources #&10;](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="02f2f-174">[!code-vb[VbVbalrMyResources#10](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_5.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02f2f-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02f2f-175">See Also</span></span>  
 <span data-ttu-id="02f2f-176">[如何︰ 加入或移除資源](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d) </span><span class="sxs-lookup"><span data-stu-id="02f2f-176">[How to: Add or Remove Resources](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d) </span></span>  
<span data-ttu-id="02f2f-177"> [管理應用程式資源 (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-resources-dotnet) </span><span class="sxs-lookup"><span data-stu-id="02f2f-177"> [Managing Application Resources (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-resources-dotnet) </span></span>  
<span data-ttu-id="02f2f-178"> [桌面應用程式中的資源](http://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890) </span><span class="sxs-lookup"><span data-stu-id="02f2f-178"> [Resources in Desktop Apps](http://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890) </span></span>  
<span data-ttu-id="02f2f-179"> [逐步解說︰ 將 Windows Form 當地語系化](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5)</span><span class="sxs-lookup"><span data-stu-id="02f2f-179"> [Walkthrough: Localizing Windows Forms](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5)</span></span>

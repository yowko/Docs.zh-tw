---
title: My.Resources 物件
ms.date: 07/20/2015
f1_keywords:
- My.Resources
- My.Resources.MyResources.ResourceManager
- My.Resources.MyResources.Culture
helpviewer_keywords:
- My.Resources object
ms.assetid: 34c3f2dc-7b87-432c-9d5f-17ea666bb266
ms.openlocfilehash: 9fd23cb119ff9148a45d32ec70ccc4dad08ab876
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="myresources-object"></a><span data-ttu-id="dc347-102">My.Resources 物件</span><span class="sxs-lookup"><span data-stu-id="dc347-102">My.Resources Object</span></span>
<span data-ttu-id="dc347-103">提供屬性和類別來存取應用程式的資源。</span><span class="sxs-lookup"><span data-stu-id="dc347-103">Provides properties and classes for accessing the application's resources.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc347-104">備註</span><span class="sxs-lookup"><span data-stu-id="dc347-104">Remarks</span></span>  
 <span data-ttu-id="dc347-105">`My.Resources`物件提供存取應用程式的資源，並可讓您以動態方式擷取資源應用程式。</span><span class="sxs-lookup"><span data-stu-id="dc347-105">The `My.Resources` object provides access to the application's resources and lets you dynamically retrieve resources for your application.</span></span> <span data-ttu-id="dc347-106">如需詳細資訊，請參閱[管理應用程式資源 (.NET)](/visualstudio/ide/managing-application-resources-dotnet)。</span><span class="sxs-lookup"><span data-stu-id="dc347-106">For more information, see [Managing Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
 <span data-ttu-id="dc347-107">`My.Resources`物件會公開只有全域資源。</span><span class="sxs-lookup"><span data-stu-id="dc347-107">The `My.Resources` object exposes only global resources.</span></span> <span data-ttu-id="dc347-108">它不提供與表單相關聯的資源檔案的存取權。</span><span class="sxs-lookup"><span data-stu-id="dc347-108">It does not provide access to resource files associated with forms.</span></span> <span data-ttu-id="dc347-109">您必須在表單中存取的表單資源。</span><span class="sxs-lookup"><span data-stu-id="dc347-109">You must access the form resources from the form.</span></span>  
  
 <span data-ttu-id="dc347-110">您可以存取應用程式的特定文化特性資源檔從`My.Resources`物件。</span><span class="sxs-lookup"><span data-stu-id="dc347-110">You can access the application's culture-specific resource files from the `My.Resources` object.</span></span> <span data-ttu-id="dc347-111">根據預設，`My.Resources`物件查閱比對中的文化特性資源檔中的資源<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="dc347-111">By default, the `My.Resources` object looks up resources from the resource file that matches the culture in the <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A> property.</span></span> <span data-ttu-id="dc347-112">不過，您可以覆寫這個行為，並指定要用於資源的特定文化特性。</span><span class="sxs-lookup"><span data-stu-id="dc347-112">However, you can override this behavior and specify a particular culture to use for the resources.</span></span> <span data-ttu-id="dc347-113">如需詳細資訊，請參閱[桌面應用程式中的資源](../../../framework/resources/index.md)。</span><span class="sxs-lookup"><span data-stu-id="dc347-113">For more information, see [Resources in Desktop Apps](../../../framework/resources/index.md).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="dc347-114">屬性</span><span class="sxs-lookup"><span data-stu-id="dc347-114">Properties</span></span>  
 <span data-ttu-id="dc347-115">內容`My.Resources`物件提供唯讀存取您的應用程式資源。</span><span class="sxs-lookup"><span data-stu-id="dc347-115">The properties of the `My.Resources` object provide read-only access to your application's resources.</span></span> <span data-ttu-id="dc347-116">若要新增或移除資源，使用**專案設計工具**。</span><span class="sxs-lookup"><span data-stu-id="dc347-116">To add or remove resources, use the **Project Designer**.</span></span> <span data-ttu-id="dc347-117">您可以存取資源，透過新增**專案設計工具**使用`My.Resources.``resourceName`。</span><span class="sxs-lookup"><span data-stu-id="dc347-117">You can access resources added through the **Project Designer** by using `My.Resources.``resourceName`.</span></span>  
  
 <span data-ttu-id="dc347-118">您也可以新增或移除選取的專案中的資源檔**方案總管 中**按一下**加入新項目**或**加入現有項目**從**專案**功能表。</span><span class="sxs-lookup"><span data-stu-id="dc347-118">You can also add or remove resource files by selecting your project in **Solution Explorer** and clicking **Add New Item** or **Add Existing Item** from the **Project** menu.</span></span> <span data-ttu-id="dc347-119">您可以存取資源利用這個方式加入`My.Resources.``resourceFileName`、`resourceName`。</span><span class="sxs-lookup"><span data-stu-id="dc347-119">You can access resources added in this manner by using `My.Resources.``resourceFileName`.`resourceName`.</span></span>  
  
 <span data-ttu-id="dc347-120">每個資源都有名稱、 類別目錄和值，以及這些資源的設定會決定要存取資源的屬性會出現在`My.Resources`物件。</span><span class="sxs-lookup"><span data-stu-id="dc347-120">Each resource has a name, category, and value, and these resource settings determine how the property to access the resource appears in the `My.Resources` object.</span></span> <span data-ttu-id="dc347-121">資源中加入**專案設計工具**:</span><span class="sxs-lookup"><span data-stu-id="dc347-121">For resources added in the **Project Designer**:</span></span>  
  
-   <span data-ttu-id="dc347-122">名稱會決定屬性的名稱</span><span class="sxs-lookup"><span data-stu-id="dc347-122">The name determines the name of the property,</span></span>  
  
-   <span data-ttu-id="dc347-123">資源資料是屬性的值</span><span class="sxs-lookup"><span data-stu-id="dc347-123">The resource data is the value of the property,</span></span>  
  
-   <span data-ttu-id="dc347-124">分類會決定屬性的型別：</span><span class="sxs-lookup"><span data-stu-id="dc347-124">The category determines the type of the property:</span></span>  
  
|<span data-ttu-id="dc347-125">分類</span><span class="sxs-lookup"><span data-stu-id="dc347-125">Category</span></span>|<span data-ttu-id="dc347-126">屬性資料型別</span><span class="sxs-lookup"><span data-stu-id="dc347-126">Property data type</span></span>|  
|---|---|  
|<span data-ttu-id="dc347-127">**字串**</span><span class="sxs-lookup"><span data-stu-id="dc347-127">**Strings**</span></span>|[<span data-ttu-id="dc347-128">String</span><span class="sxs-lookup"><span data-stu-id="dc347-128">String</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)|  
|<span data-ttu-id="dc347-129">**影像**</span><span class="sxs-lookup"><span data-stu-id="dc347-129">**Images**</span></span>|<xref:System.Drawing.Bitmap>|  
|<span data-ttu-id="dc347-130">**圖示**</span><span class="sxs-lookup"><span data-stu-id="dc347-130">**Icons**</span></span>|<xref:System.Drawing.Icon>|  
|<span data-ttu-id="dc347-131">**音效**</span><span class="sxs-lookup"><span data-stu-id="dc347-131">**Audio**</span></span>|<xref:System.IO.UnmanagedMemoryStream><br /><br /> <span data-ttu-id="dc347-132"><xref:System.IO.UnmanagedMemoryStream>類別衍生自<xref:System.IO.Stream>類別中，因此它可以搭配這些方法會採用資料流，例如<xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="dc347-132">The <xref:System.IO.UnmanagedMemoryStream> class derives from the <xref:System.IO.Stream> class, so it can be used with methods that take streams, such as the <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A> method.</span></span>|  
|<span data-ttu-id="dc347-133">**檔案**</span><span class="sxs-lookup"><span data-stu-id="dc347-133">**Files**</span></span>|<span data-ttu-id="dc347-134">-   [字串](../../../visual-basic/language-reference/data-types/string-data-type.md)文字檔案。</span><span class="sxs-lookup"><span data-stu-id="dc347-134">-   [String](../../../visual-basic/language-reference/data-types/string-data-type.md) for text files.</span></span><br /><span data-ttu-id="dc347-135">-   <xref:System.Drawing.Bitmap> 映像檔案。</span><span class="sxs-lookup"><span data-stu-id="dc347-135">-   <xref:System.Drawing.Bitmap> for image files.</span></span><br /><span data-ttu-id="dc347-136">-   <xref:System.Drawing.Icon> 圖示檔案。</span><span class="sxs-lookup"><span data-stu-id="dc347-136">-   <xref:System.Drawing.Icon> for icon files.</span></span><br /><span data-ttu-id="dc347-137">-   <xref:System.IO.UnmanagedMemoryStream> 音效檔。</span><span class="sxs-lookup"><span data-stu-id="dc347-137">-   <xref:System.IO.UnmanagedMemoryStream> for sound files.</span></span>|  
|<span data-ttu-id="dc347-138">**其他**</span><span class="sxs-lookup"><span data-stu-id="dc347-138">**Other**</span></span>|<span data-ttu-id="dc347-139">在設計工具中的資訊來決定**類型**資料行。</span><span class="sxs-lookup"><span data-stu-id="dc347-139">Determined by the information in the designer's **Type** column.</span></span>|  
  
## <a name="classes"></a><span data-ttu-id="dc347-140">類別</span><span class="sxs-lookup"><span data-stu-id="dc347-140">Classes</span></span>  
 <span data-ttu-id="dc347-141">`My.Resources`物件會公開為具有共用的屬性類別的每個資源檔。</span><span class="sxs-lookup"><span data-stu-id="dc347-141">The `My.Resources` object exposes each resource file as a class with shared properties.</span></span> <span data-ttu-id="dc347-142">類別名稱是資源檔的名稱相同。</span><span class="sxs-lookup"><span data-stu-id="dc347-142">The class name is the same as the name of the resource file.</span></span> <span data-ttu-id="dc347-143">上一節所述，在資源檔中的資源會公開為類別中的屬性。</span><span class="sxs-lookup"><span data-stu-id="dc347-143">As described in the previous section, the resources in a resource file are exposed as properties in the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc347-144">範例</span><span class="sxs-lookup"><span data-stu-id="dc347-144">Example</span></span>  
 <span data-ttu-id="dc347-145">此範例會設定表單的標題為指定的字串資源`Form1Title`應用程式資源檔中。</span><span class="sxs-lookup"><span data-stu-id="dc347-145">This example sets the title of a form to the string resource named `Form1Title` in the application resource file.</span></span> <span data-ttu-id="dc347-146">如範例能夠運作，應用程式必須具有名為字串`Form1Title`其資源檔中。</span><span class="sxs-lookup"><span data-stu-id="dc347-146">For the example to work, the application must have a string named `Form1Title` in its resource file.</span></span>  
  
 [!code-vb[VbVbalrMyResources#1](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="dc347-147">範例</span><span class="sxs-lookup"><span data-stu-id="dc347-147">Example</span></span>  
 <span data-ttu-id="dc347-148">這個範例會將名為圖示表單的圖示`Form1Icon`儲存應用程式的資源檔。</span><span class="sxs-lookup"><span data-stu-id="dc347-148">This example sets the icon of the form to the icon named `Form1Icon` that is stored in the application's resource file.</span></span> <span data-ttu-id="dc347-149">如範例能夠運作，應用程式必須具有名為圖示`Form1Icon`其資源檔中。</span><span class="sxs-lookup"><span data-stu-id="dc347-149">For the example to work, the application must have an icon named `Form1Icon` in its resource file.</span></span>  
  
 [!code-vb[VbVbalrMyResources#2](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="dc347-150">範例</span><span class="sxs-lookup"><span data-stu-id="dc347-150">Example</span></span>  
 <span data-ttu-id="dc347-151">此範例會設定表單的背景影像的影像資源，名為`Form1Background`，這是應用程式資源檔中。</span><span class="sxs-lookup"><span data-stu-id="dc347-151">This example sets the background image of a form to the image resource named `Form1Background`, which is in the application resource file.</span></span> <span data-ttu-id="dc347-152">要讓範例能夠運作，應用程式必須具有名為的映像資源`Form1Background`其資源檔中。</span><span class="sxs-lookup"><span data-stu-id="dc347-152">For this example to work, the application must have an image resource named `Form1Background` in its resource file.</span></span>  
  
 [!code-vb[VbVbalrMyResources#3](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="dc347-153">範例</span><span class="sxs-lookup"><span data-stu-id="dc347-153">Example</span></span>  
 <span data-ttu-id="dc347-154">此範例會播放聲音儲存為具名的音效資源`Form1Greeting`應用程式的資源檔。</span><span class="sxs-lookup"><span data-stu-id="dc347-154">This example plays the sound that is stored as an audio resource named `Form1Greeting` in the application's resource file.</span></span> <span data-ttu-id="dc347-155">如範例能夠運作，應用程式必須具有名為的音訊資源`Form1Greeting`其資源檔中。</span><span class="sxs-lookup"><span data-stu-id="dc347-155">For the example to work, the application must have an audio resource named `Form1Greeting` in its resource file.</span></span> <span data-ttu-id="dc347-156">`My.Computer.Audio.Play`方法，僅適用於 Windows Forms 應用程式。</span><span class="sxs-lookup"><span data-stu-id="dc347-156">The `My.Computer.Audio.Play` method is available only for Windows Forms applications.</span></span>  
  
 [!code-vb[VbVbalrMyResources#4](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="dc347-157">範例</span><span class="sxs-lookup"><span data-stu-id="dc347-157">Example</span></span>  
 <span data-ttu-id="dc347-158">這個範例會擷取字串資源的應用程式的法文文化特性版本。</span><span class="sxs-lookup"><span data-stu-id="dc347-158">This example retrieves the French-culture version of a  string resource of the application.</span></span> <span data-ttu-id="dc347-159">資源名稱為`Message`。</span><span class="sxs-lookup"><span data-stu-id="dc347-159">The resource is named `Message`.</span></span> <span data-ttu-id="dc347-160">若要變更文化特性的`My.Resources`物件使用，此範例會使用<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>。</span><span class="sxs-lookup"><span data-stu-id="dc347-160">To change the culture that the `My.Resources` object uses, the example uses <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>.</span></span>  
  
 <span data-ttu-id="dc347-161">要讓範例能夠運作，應用程式必須具有名為字串`Message`中其資源檔和應用程式不能有該資源的檔案，Resources.fr FR.resx 法文文化特性版本。</span><span class="sxs-lookup"><span data-stu-id="dc347-161">For this example to work, the application must have a string named `Message` in its resource file, and the application should have the French-culture version of that resource file, Resources.fr-FR.resx.</span></span> <span data-ttu-id="dc347-162">如果應用程式並沒有法文文化特性的資源檔案版本，`My.Resource`物件會從預設文化特性資源檔擷取資源。</span><span class="sxs-lookup"><span data-stu-id="dc347-162">If the application does not have the French-culture version of the resource file, the `My.Resource` object retrieves the resource from the default-culture resource file.</span></span>  
  
 [!code-vb[VbVbalrMyResources#10](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_5.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="dc347-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc347-163">See Also</span></span>  
 [<span data-ttu-id="dc347-164">管理應用程式資源 (.NET)</span><span class="sxs-lookup"><span data-stu-id="dc347-164">Managing Application Resources (.NET)</span></span>](/visualstudio/ide/managing-application-resources-dotnet)  
 [<span data-ttu-id="dc347-165">桌面應用程式中的資源</span><span class="sxs-lookup"><span data-stu-id="dc347-165">Resources in Desktop Apps</span></span>](../../../framework/resources/index.md)  


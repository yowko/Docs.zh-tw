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
ms.openlocfilehash: 3d12524706f680434d5b6d8da39c89042bea3281
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867335"
---
# <a name="myresources-object"></a><span data-ttu-id="a199b-102">My.Resources 物件</span><span class="sxs-lookup"><span data-stu-id="a199b-102">My.Resources Object</span></span>

<span data-ttu-id="a199b-103">提供用來存取應用程式資源的屬性和類別。</span><span class="sxs-lookup"><span data-stu-id="a199b-103">Provides properties and classes for accessing the application's resources.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a199b-104">備註</span><span class="sxs-lookup"><span data-stu-id="a199b-104">Remarks</span></span>  

 <span data-ttu-id="a199b-105">`My.Resources`物件提供應用程式資源的存取權，並可讓您動態取出應用程式的資源。</span><span class="sxs-lookup"><span data-stu-id="a199b-105">The `My.Resources` object provides access to the application's resources and lets you dynamically retrieve resources for your application.</span></span> <span data-ttu-id="a199b-106">如需詳細資訊，請參閱 [ ( .net) 管理應用程式資源 ](/visualstudio/ide/managing-application-resources-dotnet)。</span><span class="sxs-lookup"><span data-stu-id="a199b-106">For more information, see [Managing Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
 <span data-ttu-id="a199b-107">`My.Resources`物件只會公開全域資源。</span><span class="sxs-lookup"><span data-stu-id="a199b-107">The `My.Resources` object exposes only global resources.</span></span> <span data-ttu-id="a199b-108">它不會提供與表單相關聯的資源檔存取權。</span><span class="sxs-lookup"><span data-stu-id="a199b-108">It does not provide access to resource files associated with forms.</span></span> <span data-ttu-id="a199b-109">您必須從表單存取表單資源。</span><span class="sxs-lookup"><span data-stu-id="a199b-109">You must access the form resources from the form.</span></span>  
  
 <span data-ttu-id="a199b-110">您可以從物件存取應用程式的特定文化特性資源檔 `My.Resources` 。</span><span class="sxs-lookup"><span data-stu-id="a199b-110">You can access the application's culture-specific resource files from the `My.Resources` object.</span></span> <span data-ttu-id="a199b-111">根據預設， `My.Resources` 物件會從符合屬性中文化特性的資源檔中查閱資源 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A> 。</span><span class="sxs-lookup"><span data-stu-id="a199b-111">By default, the `My.Resources` object looks up resources from the resource file that matches the culture in the <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A> property.</span></span> <span data-ttu-id="a199b-112">不過，您可以覆寫此行為，並指定要用於資源的特定文化特性。</span><span class="sxs-lookup"><span data-stu-id="a199b-112">However, you can override this behavior and specify a particular culture to use for the resources.</span></span> <span data-ttu-id="a199b-113">如需詳細資訊，請參閱[桌面應用程式中的資源](../../../framework/resources/index.md)。</span><span class="sxs-lookup"><span data-stu-id="a199b-113">For more information, see [Resources in Desktop Apps](../../../framework/resources/index.md).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a199b-114">屬性</span><span class="sxs-lookup"><span data-stu-id="a199b-114">Properties</span></span>  

 <span data-ttu-id="a199b-115">物件的屬性會 `My.Resources` 提供應用程式資源的唯讀存取權。</span><span class="sxs-lookup"><span data-stu-id="a199b-115">The properties of the `My.Resources` object provide read-only access to your application's resources.</span></span> <span data-ttu-id="a199b-116">若要加入或移除資源，請使用 [ **專案設計**工具]。</span><span class="sxs-lookup"><span data-stu-id="a199b-116">To add or remove resources, use the **Project Designer**.</span></span> <span data-ttu-id="a199b-117">您可以使用 [資源設計工具] 來存取透過 [**專案設計**工具] 加入的資源 `My.Resources.` \* \*。</span><span class="sxs-lookup"><span data-stu-id="a199b-117">You can access resources added through the **Project Designer** by using `My.Resources.`*resourceName*.</span></span>  
  
 <span data-ttu-id="a199b-118">您也可以在**方案總管**中選取專案，然後按一下 [**專案**] 功能表中的 [**加入新專案**] 或 [**加入現有專案**]，以加入或移除資源檔。</span><span class="sxs-lookup"><span data-stu-id="a199b-118">You can also add or remove resource files by selecting your project in **Solution Explorer** and clicking **Add New Item** or **Add Existing Item** from the **Project** menu.</span></span> <span data-ttu-id="a199b-119">您可以使用 resourceFileName 的資源資源來存取以這種方式新增的資源 `My.Resources.` *resourceFileName* `.` \* \*。</span><span class="sxs-lookup"><span data-stu-id="a199b-119">You can access resources added in this manner by using `My.Resources.`*resourceFileName*`.`*resourceName*.</span></span>  
  
 <span data-ttu-id="a199b-120">每個資源都有名稱、類別和值，而這些資源設定會決定存取資源的屬性如何顯示在物件中 `My.Resources` 。</span><span class="sxs-lookup"><span data-stu-id="a199b-120">Each resource has a name, category, and value, and these resource settings determine how the property to access the resource appears in the `My.Resources` object.</span></span> <span data-ttu-id="a199b-121">針對 [ **專案設計**工具] 中新增的資源：</span><span class="sxs-lookup"><span data-stu-id="a199b-121">For resources added in the **Project Designer**:</span></span>  
  
- <span data-ttu-id="a199b-122">名稱會決定屬性的名稱，</span><span class="sxs-lookup"><span data-stu-id="a199b-122">The name determines the name of the property,</span></span>  
  
- <span data-ttu-id="a199b-123">資源資料是屬性的值，</span><span class="sxs-lookup"><span data-stu-id="a199b-123">The resource data is the value of the property,</span></span>  
  
- <span data-ttu-id="a199b-124">類別會決定屬性的類型：</span><span class="sxs-lookup"><span data-stu-id="a199b-124">The category determines the type of the property:</span></span>  
  
|<span data-ttu-id="a199b-125">類別</span><span class="sxs-lookup"><span data-stu-id="a199b-125">Category</span></span>|<span data-ttu-id="a199b-126">屬性資料類型</span><span class="sxs-lookup"><span data-stu-id="a199b-126">Property data type</span></span>|  
|---|---|  
|<span data-ttu-id="a199b-127">**字串**</span><span class="sxs-lookup"><span data-stu-id="a199b-127">**Strings**</span></span>|[<span data-ttu-id="a199b-128">String</span><span class="sxs-lookup"><span data-stu-id="a199b-128">String</span></span>](../data-types/string-data-type.md)|  
|<span data-ttu-id="a199b-129">**影像**</span><span class="sxs-lookup"><span data-stu-id="a199b-129">**Images**</span></span>|<xref:System.Drawing.Bitmap>|  
|<span data-ttu-id="a199b-130">**圖示**</span><span class="sxs-lookup"><span data-stu-id="a199b-130">**Icons**</span></span>|<xref:System.Drawing.Icon>|  
|<span data-ttu-id="a199b-131">**音訊**</span><span class="sxs-lookup"><span data-stu-id="a199b-131">**Audio**</span></span>|<xref:System.IO.UnmanagedMemoryStream><br /><br /> <span data-ttu-id="a199b-132"><xref:System.IO.UnmanagedMemoryStream>類別衍生自 <xref:System.IO.Stream> 類別，因此可搭配採用資料流程的方法（例如方法）使用 <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A> 。</span><span class="sxs-lookup"><span data-stu-id="a199b-132">The <xref:System.IO.UnmanagedMemoryStream> class derives from the <xref:System.IO.Stream> class, so it can be used with methods that take streams, such as the <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A> method.</span></span>|  
|<span data-ttu-id="a199b-133">**檔案**</span><span class="sxs-lookup"><span data-stu-id="a199b-133">**Files**</span></span>|<span data-ttu-id="a199b-134">-   文字檔的[字串](../data-types/string-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="a199b-134">-   [String](../data-types/string-data-type.md) for text files.</span></span><br /><span data-ttu-id="a199b-135">-   <xref:System.Drawing.Bitmap> 適用于影像檔案。</span><span class="sxs-lookup"><span data-stu-id="a199b-135">-   <xref:System.Drawing.Bitmap> for image files.</span></span><br /><span data-ttu-id="a199b-136">-   <xref:System.Drawing.Icon> 適用于圖示檔。</span><span class="sxs-lookup"><span data-stu-id="a199b-136">-   <xref:System.Drawing.Icon> for icon files.</span></span><br /><span data-ttu-id="a199b-137">-   <xref:System.IO.UnmanagedMemoryStream> 適用于音效檔。</span><span class="sxs-lookup"><span data-stu-id="a199b-137">-   <xref:System.IO.UnmanagedMemoryStream> for sound files.</span></span>|  
|<span data-ttu-id="a199b-138">**其他**</span><span class="sxs-lookup"><span data-stu-id="a199b-138">**Other**</span></span>|<span data-ttu-id="a199b-139">由設計工具 **類型** 資料行中的資訊所決定。</span><span class="sxs-lookup"><span data-stu-id="a199b-139">Determined by the information in the designer's **Type** column.</span></span>|  
  
## <a name="classes"></a><span data-ttu-id="a199b-140">類別</span><span class="sxs-lookup"><span data-stu-id="a199b-140">Classes</span></span>  

 <span data-ttu-id="a199b-141">物件會將 `My.Resources` 每個資源檔公開為具有共用屬性的類別。</span><span class="sxs-lookup"><span data-stu-id="a199b-141">The `My.Resources` object exposes each resource file as a class with shared properties.</span></span> <span data-ttu-id="a199b-142">類別名稱與資源檔的名稱相同。</span><span class="sxs-lookup"><span data-stu-id="a199b-142">The class name is the same as the name of the resource file.</span></span> <span data-ttu-id="a199b-143">如上一節所述，資源檔中的資源會公開為類別中的屬性。</span><span class="sxs-lookup"><span data-stu-id="a199b-143">As described in the previous section, the resources in a resource file are exposed as properties in the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a199b-144">範例</span><span class="sxs-lookup"><span data-stu-id="a199b-144">Example</span></span>  

 <span data-ttu-id="a199b-145">此範例會將表單的標題設定為 `Form1Title` 應用程式資源檔中所命名的字串資源。</span><span class="sxs-lookup"><span data-stu-id="a199b-145">This example sets the title of a form to the string resource named `Form1Title` in the application resource file.</span></span> <span data-ttu-id="a199b-146">若要讓範例能夠運作，應用程式的資源檔中必須有一個名為的字串 `Form1Title` 。</span><span class="sxs-lookup"><span data-stu-id="a199b-146">For the example to work, the application must have a string named `Form1Title` in its resource file.</span></span>  
  
 [!code-vb[VbVbalrMyResources#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="a199b-147">範例</span><span class="sxs-lookup"><span data-stu-id="a199b-147">Example</span></span>  

 <span data-ttu-id="a199b-148">此範例會將表單的圖示設定為 `Form1Icon` 儲存在應用程式資源檔中名為的圖示。</span><span class="sxs-lookup"><span data-stu-id="a199b-148">This example sets the icon of the form to the icon named `Form1Icon` that is stored in the application's resource file.</span></span> <span data-ttu-id="a199b-149">若要讓範例能夠運作，應用程式的資源檔中必須有一個名為的圖示 `Form1Icon` 。</span><span class="sxs-lookup"><span data-stu-id="a199b-149">For the example to work, the application must have an icon named `Form1Icon` in its resource file.</span></span>  
  
 [!code-vb[VbVbalrMyResources#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="a199b-150">範例</span><span class="sxs-lookup"><span data-stu-id="a199b-150">Example</span></span>  

 <span data-ttu-id="a199b-151">此範例會將表單的背景影像設定為影像資源，該資源 `Form1Background` 位於應用程式資源檔中。</span><span class="sxs-lookup"><span data-stu-id="a199b-151">This example sets the background image of a form to the image resource named `Form1Background`, which is in the application resource file.</span></span> <span data-ttu-id="a199b-152">若要讓此範例能夠運作，應用程式必須 `Form1Background` 在其資源檔中有一個名為的影像資源。</span><span class="sxs-lookup"><span data-stu-id="a199b-152">For this example to work, the application must have an image resource named `Form1Background` in its resource file.</span></span>  
  
 [!code-vb[VbVbalrMyResources#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="a199b-153">範例</span><span class="sxs-lookup"><span data-stu-id="a199b-153">Example</span></span>  

 <span data-ttu-id="a199b-154">此範例會在 `Form1Greeting` 應用程式的資源檔中，播放儲存為音訊資源的音效。</span><span class="sxs-lookup"><span data-stu-id="a199b-154">This example plays the sound that is stored as an audio resource named `Form1Greeting` in the application's resource file.</span></span> <span data-ttu-id="a199b-155">若要讓範例能夠運作，應用程式的資源檔中必須有一個名為的音訊資源 `Form1Greeting` 。</span><span class="sxs-lookup"><span data-stu-id="a199b-155">For the example to work, the application must have an audio resource named `Form1Greeting` in its resource file.</span></span> <span data-ttu-id="a199b-156">此 `My.Computer.Audio.Play` 方法僅適用于 Windows Forms 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a199b-156">The `My.Computer.Audio.Play` method is available only for Windows Forms applications.</span></span>  
  
 [!code-vb[VbVbalrMyResources#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="a199b-157">範例</span><span class="sxs-lookup"><span data-stu-id="a199b-157">Example</span></span>  

 <span data-ttu-id="a199b-158">此範例會抓取應用程式之字串資源的法文文化特性版本。</span><span class="sxs-lookup"><span data-stu-id="a199b-158">This example retrieves the French-culture version of a  string resource of the application.</span></span> <span data-ttu-id="a199b-159">資源的名稱為 `Message` 。</span><span class="sxs-lookup"><span data-stu-id="a199b-159">The resource is named `Message`.</span></span> <span data-ttu-id="a199b-160">為了變更物件使用的文化特性 `My.Resources` ，此範例會使用 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A> 。</span><span class="sxs-lookup"><span data-stu-id="a199b-160">To change the culture that the `My.Resources` object uses, the example uses <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>.</span></span>  
  
 <span data-ttu-id="a199b-161">若要讓此範例能夠運作，應用程式的資源檔中必須要有一個名為的字串 `Message` ，而應用程式應該要有該資源檔（Resources.fr）的法文文化特性版本。</span><span class="sxs-lookup"><span data-stu-id="a199b-161">For this example to work, the application must have a string named `Message` in its resource file, and the application should have the French-culture version of that resource file, Resources.fr-FR.resx.</span></span> <span data-ttu-id="a199b-162">如果應用程式沒有法文文化特性版本的資源檔，則 `My.Resource` 物件會從預設文化特性資源檔抓取資源。</span><span class="sxs-lookup"><span data-stu-id="a199b-162">If the application does not have the French-culture version of the resource file, the `My.Resource` object retrieves the resource from the default-culture resource file.</span></span>  
  
 [!code-vb[VbVbalrMyResources#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="a199b-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a199b-163">See also</span></span>

- [<span data-ttu-id="a199b-164">管理應用程式資源 (.NET)</span><span class="sxs-lookup"><span data-stu-id="a199b-164">Managing Application Resources (.NET)</span></span>](/visualstudio/ide/managing-application-resources-dotnet)
- [<span data-ttu-id="a199b-165">桌面應用程式中的資源</span><span class="sxs-lookup"><span data-stu-id="a199b-165">Resources in Desktop Apps</span></span>](../../../framework/resources/index.md)

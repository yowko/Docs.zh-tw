---
title: 如何：讀取影像中繼資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- metadata [Windows Forms], property item
- metadata [Windows Forms], reading image
ms.assetid: 72ec0b31-0be7-444a-9575-1dbcb864e0be
ms.openlocfilehash: 92ce4eb8d51fbd25f9a129a629dc47bfb9941f34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526574"
---
# <a name="how-to-read-image-metadata"></a><span data-ttu-id="4fe33-102">如何：讀取影像中繼資料</span><span class="sxs-lookup"><span data-stu-id="4fe33-102">How to: Read Image Metadata</span></span>
<span data-ttu-id="4fe33-103">部分映像檔案包含以判斷影像的功能，您可以讀取的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="4fe33-103">Some image files contain metadata that you can read to determine features of the image.</span></span> <span data-ttu-id="4fe33-104">例如，數位相片可能包含您可以讀取，判斷製造商和型號的相機，用來擷取映像的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="4fe33-104">For example, a digital photograph might contain metadata that you can read to determine the make and model of the camera used to capture the image.</span></span> <span data-ttu-id="4fe33-105">與[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]，您可以讀取現有的中繼資料，您也可以撰寫新的中繼資料映像檔案。</span><span class="sxs-lookup"><span data-stu-id="4fe33-105">With [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you can read existing metadata, and you can also write new metadata to image files.</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="4fe33-106"> 儲存中繼資料中的一份<xref:System.Drawing.Imaging.PropertyItem>物件。</span><span class="sxs-lookup"><span data-stu-id="4fe33-106"> stores an individual piece of metadata in a <xref:System.Drawing.Imaging.PropertyItem> object.</span></span> <span data-ttu-id="4fe33-107">您可以閱讀<xref:System.Drawing.Image.PropertyItems%2A>屬性<xref:System.Drawing.Image>要從檔案擷取的所有中繼資料物件。</span><span class="sxs-lookup"><span data-stu-id="4fe33-107">You can read the <xref:System.Drawing.Image.PropertyItems%2A> property of an <xref:System.Drawing.Image> object to retrieve all the metadata from a file.</span></span> <span data-ttu-id="4fe33-108"><xref:System.Drawing.Image.PropertyItems%2A>屬性傳回的陣列<xref:System.Drawing.Imaging.PropertyItem>物件。</span><span class="sxs-lookup"><span data-stu-id="4fe33-108">The <xref:System.Drawing.Image.PropertyItems%2A> property returns an array of <xref:System.Drawing.Imaging.PropertyItem> objects.</span></span>  
  
 <span data-ttu-id="4fe33-109">A<xref:System.Drawing.Imaging.PropertyItem>物件具有下列四個屬性： `Id`， `Value`， `Len`，和`Type`。</span><span class="sxs-lookup"><span data-stu-id="4fe33-109">A <xref:System.Drawing.Imaging.PropertyItem> object has the following four properties: `Id`, `Value`, `Len`, and `Type`.</span></span>  
  
## <a name="id"></a><span data-ttu-id="4fe33-110">ID</span><span class="sxs-lookup"><span data-stu-id="4fe33-110">Id</span></span>  
 <span data-ttu-id="4fe33-111">標記識別項目的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="4fe33-111">A tag that identifies the metadata item.</span></span> <span data-ttu-id="4fe33-112">可以指派給某些值<xref:System.Drawing.Imaging.PropertyItem.Id%2A>下表所示。</span><span class="sxs-lookup"><span data-stu-id="4fe33-112">Some values that can be assigned to <xref:System.Drawing.Imaging.PropertyItem.Id%2A> are shown in the following table.</span></span>  
  
|<span data-ttu-id="4fe33-113">十六進位值</span><span class="sxs-lookup"><span data-stu-id="4fe33-113">Hexadecimal value</span></span>|<span data-ttu-id="4fe33-114">描述</span><span class="sxs-lookup"><span data-stu-id="4fe33-114">Description</span></span>|  
|-----------------------|-----------------|  
|<span data-ttu-id="4fe33-115">0x0320</span><span class="sxs-lookup"><span data-stu-id="4fe33-115">0x0320</span></span><br /><br /> <span data-ttu-id="4fe33-116">0x010F</span><span class="sxs-lookup"><span data-stu-id="4fe33-116">0x010F</span></span><br /><br /> <span data-ttu-id="4fe33-117">0x0110</span><span class="sxs-lookup"><span data-stu-id="4fe33-117">0x0110</span></span><br /><br /> <span data-ttu-id="4fe33-118">0x9003</span><span class="sxs-lookup"><span data-stu-id="4fe33-118">0x9003</span></span><br /><br /> <span data-ttu-id="4fe33-119">0x829A</span><span class="sxs-lookup"><span data-stu-id="4fe33-119">0x829A</span></span><br /><br /> <span data-ttu-id="4fe33-120">0x5090</span><span class="sxs-lookup"><span data-stu-id="4fe33-120">0x5090</span></span><br /><br /> <span data-ttu-id="4fe33-121">0x5091</span><span class="sxs-lookup"><span data-stu-id="4fe33-121">0x5091</span></span>|<span data-ttu-id="4fe33-122">映像標題</span><span class="sxs-lookup"><span data-stu-id="4fe33-122">Image title</span></span><br /><br /> <span data-ttu-id="4fe33-123">設備製造商</span><span class="sxs-lookup"><span data-stu-id="4fe33-123">Equipment manufacturer</span></span><br /><br /> <span data-ttu-id="4fe33-124">設備模型</span><span class="sxs-lookup"><span data-stu-id="4fe33-124">Equipment model</span></span><br /><br /> <span data-ttu-id="4fe33-125">ExifDTOriginal</span><span class="sxs-lookup"><span data-stu-id="4fe33-125">ExifDTOriginal</span></span><br /><br /> <span data-ttu-id="4fe33-126">Exif 曝光時間</span><span class="sxs-lookup"><span data-stu-id="4fe33-126">Exif exposure time</span></span><br /><br /> <span data-ttu-id="4fe33-127">亮度表</span><span class="sxs-lookup"><span data-stu-id="4fe33-127">Luminance table</span></span><br /><br /> <span data-ttu-id="4fe33-128">色度表</span><span class="sxs-lookup"><span data-stu-id="4fe33-128">Chrominance table</span></span>|  
  
## <a name="value"></a><span data-ttu-id="4fe33-129">值</span><span class="sxs-lookup"><span data-stu-id="4fe33-129">Value</span></span>  
 <span data-ttu-id="4fe33-130">值的陣列。</span><span class="sxs-lookup"><span data-stu-id="4fe33-130">An array of values.</span></span> <span data-ttu-id="4fe33-131">值的格式取決於<xref:System.Drawing.Imaging.PropertyItem.Type%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="4fe33-131">The format of the values is determined by the <xref:System.Drawing.Imaging.PropertyItem.Type%2A> property.</span></span>  
  
## <a name="len"></a><span data-ttu-id="4fe33-132">長度</span><span class="sxs-lookup"><span data-stu-id="4fe33-132">Len</span></span>  
 <span data-ttu-id="4fe33-133">所指向的值陣列的長度 （以位元組為單位）<xref:System.Drawing.Imaging.PropertyItem.Value%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="4fe33-133">The length (in bytes) of the array of values pointed to by the <xref:System.Drawing.Imaging.PropertyItem.Value%2A> property.</span></span>  
  
## <a name="type"></a><span data-ttu-id="4fe33-134">類型</span><span class="sxs-lookup"><span data-stu-id="4fe33-134">Type</span></span>  
 <span data-ttu-id="4fe33-135">所指陣列中值的資料型別`Value`屬性。</span><span class="sxs-lookup"><span data-stu-id="4fe33-135">The data type of the values in the array pointed to by the `Value` property.</span></span> <span data-ttu-id="4fe33-136">所指定的格式`Type`屬性值會顯示下表中</span><span class="sxs-lookup"><span data-stu-id="4fe33-136">The formats indicated by the `Type` property values are shown in the following table</span></span>  
  
|<span data-ttu-id="4fe33-137">數值</span><span class="sxs-lookup"><span data-stu-id="4fe33-137">Numeric value</span></span>|<span data-ttu-id="4fe33-138">描述</span><span class="sxs-lookup"><span data-stu-id="4fe33-138">Description</span></span>|  
|-------------------|-----------------|  
|<span data-ttu-id="4fe33-139">1</span><span class="sxs-lookup"><span data-stu-id="4fe33-139">1</span></span>|<span data-ttu-id="4fe33-140">`Byte`</span><span class="sxs-lookup"><span data-stu-id="4fe33-140">A `Byte`</span></span>|  
|<span data-ttu-id="4fe33-141">2</span><span class="sxs-lookup"><span data-stu-id="4fe33-141">2</span></span>|<span data-ttu-id="4fe33-142">陣列`Byte`為 ASCII 編碼的物件</span><span class="sxs-lookup"><span data-stu-id="4fe33-142">An array of `Byte` objects encoded as ASCII</span></span>|  
|<span data-ttu-id="4fe33-143">3</span><span class="sxs-lookup"><span data-stu-id="4fe33-143">3</span></span>|<span data-ttu-id="4fe33-144">16 位元整數</span><span class="sxs-lookup"><span data-stu-id="4fe33-144">A 16-bit integer</span></span>|  
|<span data-ttu-id="4fe33-145">4</span><span class="sxs-lookup"><span data-stu-id="4fe33-145">4</span></span>|<span data-ttu-id="4fe33-146">32 位元整數</span><span class="sxs-lookup"><span data-stu-id="4fe33-146">A 32-bit integer</span></span>|  
|<span data-ttu-id="4fe33-147">5</span><span class="sxs-lookup"><span data-stu-id="4fe33-147">5</span></span>|<span data-ttu-id="4fe33-148">兩個陣列`Byte`合理數表示的物件</span><span class="sxs-lookup"><span data-stu-id="4fe33-148">An array of two `Byte` objects that represent a rational number</span></span>|  
|<span data-ttu-id="4fe33-149">6</span><span class="sxs-lookup"><span data-stu-id="4fe33-149">6</span></span>|<span data-ttu-id="4fe33-150">未使用</span><span class="sxs-lookup"><span data-stu-id="4fe33-150">Not used</span></span>|  
|<span data-ttu-id="4fe33-151">7</span><span class="sxs-lookup"><span data-stu-id="4fe33-151">7</span></span>|<span data-ttu-id="4fe33-152">未定義</span><span class="sxs-lookup"><span data-stu-id="4fe33-152">Undefined</span></span>|  
|<span data-ttu-id="4fe33-153">8</span><span class="sxs-lookup"><span data-stu-id="4fe33-153">8</span></span>|<span data-ttu-id="4fe33-154">未使用</span><span class="sxs-lookup"><span data-stu-id="4fe33-154">Not used</span></span>|  
|<span data-ttu-id="4fe33-155">9</span><span class="sxs-lookup"><span data-stu-id="4fe33-155">9</span></span>|`SLong`|  
|<span data-ttu-id="4fe33-156">10</span><span class="sxs-lookup"><span data-stu-id="4fe33-156">10</span></span>|`SRational`|  
  
## <a name="example"></a><span data-ttu-id="4fe33-157">範例</span><span class="sxs-lookup"><span data-stu-id="4fe33-157">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="4fe33-158">描述</span><span class="sxs-lookup"><span data-stu-id="4fe33-158">Description</span></span>  
 <span data-ttu-id="4fe33-159">下列程式碼範例讀取，並顯示檔案中的中繼資料的七個部分， `FakePhoto.jpg`。</span><span class="sxs-lookup"><span data-stu-id="4fe33-159">The following code example reads and displays the seven pieces of metadata in the file `FakePhoto.jpg`.</span></span> <span data-ttu-id="4fe33-160">第二個 （索引 1） 屬性項目在清單中的有<xref:System.Drawing.Imaging.PropertyItem.Id%2A>0x010F （設備製造商） 和<xref:System.Drawing.Imaging.PropertyItem.Type%2A>2 （ASCII 編碼位元組陣列）。</span><span class="sxs-lookup"><span data-stu-id="4fe33-160">The second (index 1) property item in the list has <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (equipment manufacturer) and <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (ASCII-encoded byte array).</span></span> <span data-ttu-id="4fe33-161">程式碼範例會顯示該屬性之項目的值。</span><span class="sxs-lookup"><span data-stu-id="4fe33-161">The code example displays the value of that property item.</span></span>  
  
 <span data-ttu-id="4fe33-162">程式碼會產生類似下面的輸出：</span><span class="sxs-lookup"><span data-stu-id="4fe33-162">The code produces output similar to the following:</span></span>  
  
 `Property Item 0`  
  
 `id: 0x320`  
  
 `type: 2`  
  
 `length: 16 bytes`  
  
 `Property Item 1`  
  
 `id: 0x10f`  
  
 `type: 2`  
  
 `length: 17 bytes`  
  
 `Property Item 2`  
  
 `id: 0x110`  
  
 `type: 2`  
  
 `length: 7 bytes`  
  
 `Property Item 3`  
  
 `id: 0x9003`  
  
 `type: 2`  
  
 `length: 20 bytes`  
  
 `Property Item 4`  
  
 `id: 0x829a`  
  
 `type: 5`  
  
 `length: 8 bytes`  
  
 `Property Item 5`  
  
 `id: 0x5090`  
  
 `type: 3`  
  
 `length: 128 bytes`  
  
 `Property Item 6`  
  
 `id: 0x5091`  
  
 `type: 3`  
  
 `length: 128 bytes`  
  
 `The equipment make is Northwind Camera.`  
  
### <a name="code"></a><span data-ttu-id="4fe33-163">程式碼</span><span class="sxs-lookup"><span data-stu-id="4fe33-163">Code</span></span>  
 [!code-csharp[System.Drawing.WorkingWithImages#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.WorkingWithImages#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4fe33-164">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="4fe33-164">Compiling the Code</span></span>  
 <span data-ttu-id="4fe33-165">上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。</span><span class="sxs-lookup"><span data-stu-id="4fe33-165">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="4fe33-166">處理表單的<xref:System.Windows.Forms.Control.Paint>事件並將此程式碼貼到 [小畫家] 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="4fe33-166">Handle the form's <xref:System.Windows.Forms.Control.Paint> event and paste this code into the paint event handler.</span></span> <span data-ttu-id="4fe33-167">您必須取代`FakePhoto.jpg`映像名稱與路徑上您的系統並匯入有效`System.Drawing.Imaging`命名空間。</span><span class="sxs-lookup"><span data-stu-id="4fe33-167">You must replace `FakePhoto.jpg` with an image name and path valid on your system and import the `System.Drawing.Imaging` namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fe33-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4fe33-168">See Also</span></span>  
 [<span data-ttu-id="4fe33-169">影像、點陣圖和中繼檔</span><span class="sxs-lookup"><span data-stu-id="4fe33-169">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="4fe33-170">使用影像、點陣圖、圖示和中繼檔</span><span class="sxs-lookup"><span data-stu-id="4fe33-170">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)

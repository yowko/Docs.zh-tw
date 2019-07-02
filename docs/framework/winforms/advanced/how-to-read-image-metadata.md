---
title: HOW TO：讀取影像中繼資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- metadata [Windows Forms], property item
- metadata [Windows Forms], reading image
ms.assetid: 72ec0b31-0be7-444a-9575-1dbcb864e0be
ms.openlocfilehash: 6c02f7e5744828fd8eddc88be8d7da28f3bc2a2a
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505784"
---
# <a name="how-to-read-image-metadata"></a><span data-ttu-id="dd9d4-102">HOW TO：讀取影像中繼資料</span><span class="sxs-lookup"><span data-stu-id="dd9d4-102">How to: Read Image Metadata</span></span>
<span data-ttu-id="dd9d4-103">某些影像檔包含中繼資料，您可以讀取來判斷映像的功能。</span><span class="sxs-lookup"><span data-stu-id="dd9d4-103">Some image files contain metadata that you can read to determine features of the image.</span></span> <span data-ttu-id="dd9d4-104">比方說，數位相片可能包含您可以讀取來判斷的廠牌與型號，用來擷取影像之相機的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="dd9d4-104">For example, a digital photograph might contain metadata that you can read to determine the make and model of the camera used to capture the image.</span></span> <span data-ttu-id="dd9d4-105">使用 GDI + 中，您可以讀取現有的中繼資料，而且您也可以撰寫新的中繼資料映像檔案。</span><span class="sxs-lookup"><span data-stu-id="dd9d4-105">With GDI+, you can read existing metadata, and you can also write new metadata to image files.</span></span>  
  
 <span data-ttu-id="dd9d4-106">GDI + 會儲存一段個別中繼資料中<xref:System.Drawing.Imaging.PropertyItem>物件。</span><span class="sxs-lookup"><span data-stu-id="dd9d4-106">GDI+ stores an individual piece of metadata in a <xref:System.Drawing.Imaging.PropertyItem> object.</span></span> <span data-ttu-id="dd9d4-107">您可以閱讀<xref:System.Drawing.Image.PropertyItems%2A>屬性<xref:System.Drawing.Image>要從檔案擷取所有中繼資料物件。</span><span class="sxs-lookup"><span data-stu-id="dd9d4-107">You can read the <xref:System.Drawing.Image.PropertyItems%2A> property of an <xref:System.Drawing.Image> object to retrieve all the metadata from a file.</span></span> <span data-ttu-id="dd9d4-108"><xref:System.Drawing.Image.PropertyItems%2A>屬性傳回的陣列<xref:System.Drawing.Imaging.PropertyItem>物件。</span><span class="sxs-lookup"><span data-stu-id="dd9d4-108">The <xref:System.Drawing.Image.PropertyItems%2A> property returns an array of <xref:System.Drawing.Imaging.PropertyItem> objects.</span></span>  
  
 <span data-ttu-id="dd9d4-109">A<xref:System.Drawing.Imaging.PropertyItem>物件具有下列四個屬性： `Id`， `Value`， `Len`，和`Type`。</span><span class="sxs-lookup"><span data-stu-id="dd9d4-109">A <xref:System.Drawing.Imaging.PropertyItem> object has the following four properties: `Id`, `Value`, `Len`, and `Type`.</span></span>  
  
## <a name="id"></a><span data-ttu-id="dd9d4-110">ID</span><span class="sxs-lookup"><span data-stu-id="dd9d4-110">Id</span></span>  
 <span data-ttu-id="dd9d4-111">標記可識別中繼資料項目。</span><span class="sxs-lookup"><span data-stu-id="dd9d4-111">A tag that identifies the metadata item.</span></span> <span data-ttu-id="dd9d4-112">某些值，可以指派給<xref:System.Drawing.Imaging.PropertyItem.Id%2A>下表所示。</span><span class="sxs-lookup"><span data-stu-id="dd9d4-112">Some values that can be assigned to <xref:System.Drawing.Imaging.PropertyItem.Id%2A> are shown in the following table.</span></span>  
  
|<span data-ttu-id="dd9d4-113">十六進位值</span><span class="sxs-lookup"><span data-stu-id="dd9d4-113">Hexadecimal value</span></span>|<span data-ttu-id="dd9d4-114">描述</span><span class="sxs-lookup"><span data-stu-id="dd9d4-114">Description</span></span>|  
|-----------------------|-----------------|  
|<span data-ttu-id="dd9d4-115">0x0320</span><span class="sxs-lookup"><span data-stu-id="dd9d4-115">0x0320</span></span><br /><br /> <span data-ttu-id="dd9d4-116">0x010F</span><span class="sxs-lookup"><span data-stu-id="dd9d4-116">0x010F</span></span><br /><br /> <span data-ttu-id="dd9d4-117">0x0110</span><span class="sxs-lookup"><span data-stu-id="dd9d4-117">0x0110</span></span><br /><br /> <span data-ttu-id="dd9d4-118">0x9003</span><span class="sxs-lookup"><span data-stu-id="dd9d4-118">0x9003</span></span><br /><br /> <span data-ttu-id="dd9d4-119">0x829A</span><span class="sxs-lookup"><span data-stu-id="dd9d4-119">0x829A</span></span><br /><br /> <span data-ttu-id="dd9d4-120">0x5090</span><span class="sxs-lookup"><span data-stu-id="dd9d4-120">0x5090</span></span><br /><br /> <span data-ttu-id="dd9d4-121">0x5091</span><span class="sxs-lookup"><span data-stu-id="dd9d4-121">0x5091</span></span>|<span data-ttu-id="dd9d4-122">映像標題</span><span class="sxs-lookup"><span data-stu-id="dd9d4-122">Image title</span></span><br /><br /> <span data-ttu-id="dd9d4-123">設備製造商</span><span class="sxs-lookup"><span data-stu-id="dd9d4-123">Equipment manufacturer</span></span><br /><br /> <span data-ttu-id="dd9d4-124">設備型號</span><span class="sxs-lookup"><span data-stu-id="dd9d4-124">Equipment model</span></span><br /><br /> <span data-ttu-id="dd9d4-125">ExifDTOriginal</span><span class="sxs-lookup"><span data-stu-id="dd9d4-125">ExifDTOriginal</span></span><br /><br /> <span data-ttu-id="dd9d4-126">Exif 曝光時間</span><span class="sxs-lookup"><span data-stu-id="dd9d4-126">Exif exposure time</span></span><br /><br /> <span data-ttu-id="dd9d4-127">亮度表</span><span class="sxs-lookup"><span data-stu-id="dd9d4-127">Luminance table</span></span><br /><br /> <span data-ttu-id="dd9d4-128">色差表</span><span class="sxs-lookup"><span data-stu-id="dd9d4-128">Chrominance table</span></span>|  
  
## <a name="value"></a><span data-ttu-id="dd9d4-129">值</span><span class="sxs-lookup"><span data-stu-id="dd9d4-129">Value</span></span>  
 <span data-ttu-id="dd9d4-130">值的陣列。</span><span class="sxs-lookup"><span data-stu-id="dd9d4-130">An array of values.</span></span> <span data-ttu-id="dd9d4-131">值的格式取決於<xref:System.Drawing.Imaging.PropertyItem.Type%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="dd9d4-131">The format of the values is determined by the <xref:System.Drawing.Imaging.PropertyItem.Type%2A> property.</span></span>  
  
## <a name="len"></a><span data-ttu-id="dd9d4-132">長度</span><span class="sxs-lookup"><span data-stu-id="dd9d4-132">Len</span></span>  
 <span data-ttu-id="dd9d4-133">一維陣列的值的長度 （以位元組為單位） 所指的<xref:System.Drawing.Imaging.PropertyItem.Value%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="dd9d4-133">The length (in bytes) of the array of values pointed to by the <xref:System.Drawing.Imaging.PropertyItem.Value%2A> property.</span></span>  
  
## <a name="type"></a><span data-ttu-id="dd9d4-134">類型</span><span class="sxs-lookup"><span data-stu-id="dd9d4-134">Type</span></span>  
 <span data-ttu-id="dd9d4-135">陣列中值的資料類型所指的`Value`屬性。</span><span class="sxs-lookup"><span data-stu-id="dd9d4-135">The data type of the values in the array pointed to by the `Value` property.</span></span> <span data-ttu-id="dd9d4-136">所表示之格式`Type`下表顯示屬性值</span><span class="sxs-lookup"><span data-stu-id="dd9d4-136">The formats indicated by the `Type` property values are shown in the following table</span></span>  
  
|<span data-ttu-id="dd9d4-137">數字值</span><span class="sxs-lookup"><span data-stu-id="dd9d4-137">Numeric value</span></span>|<span data-ttu-id="dd9d4-138">描述</span><span class="sxs-lookup"><span data-stu-id="dd9d4-138">Description</span></span>|  
|-------------------|-----------------|  
|<span data-ttu-id="dd9d4-139">1</span><span class="sxs-lookup"><span data-stu-id="dd9d4-139">1</span></span>|<span data-ttu-id="dd9d4-140">`Byte`</span><span class="sxs-lookup"><span data-stu-id="dd9d4-140">A `Byte`</span></span>|  
|<span data-ttu-id="dd9d4-141">2</span><span class="sxs-lookup"><span data-stu-id="dd9d4-141">2</span></span>|<span data-ttu-id="dd9d4-142">陣列`Byte`為 ASCII 編碼的物件</span><span class="sxs-lookup"><span data-stu-id="dd9d4-142">An array of `Byte` objects encoded as ASCII</span></span>|  
|<span data-ttu-id="dd9d4-143">3</span><span class="sxs-lookup"><span data-stu-id="dd9d4-143">3</span></span>|<span data-ttu-id="dd9d4-144">16 位元整數</span><span class="sxs-lookup"><span data-stu-id="dd9d4-144">A 16-bit integer</span></span>|  
|<span data-ttu-id="dd9d4-145">4</span><span class="sxs-lookup"><span data-stu-id="dd9d4-145">4</span></span>|<span data-ttu-id="dd9d4-146">32 位元整數</span><span class="sxs-lookup"><span data-stu-id="dd9d4-146">A 32-bit integer</span></span>|  
|<span data-ttu-id="dd9d4-147">5</span><span class="sxs-lookup"><span data-stu-id="dd9d4-147">5</span></span>|<span data-ttu-id="dd9d4-148">兩個陣列`Byte`表示有理數的物件</span><span class="sxs-lookup"><span data-stu-id="dd9d4-148">An array of two `Byte` objects that represent a rational number</span></span>|  
|<span data-ttu-id="dd9d4-149">6</span><span class="sxs-lookup"><span data-stu-id="dd9d4-149">6</span></span>|<span data-ttu-id="dd9d4-150">未使用</span><span class="sxs-lookup"><span data-stu-id="dd9d4-150">Not used</span></span>|  
|<span data-ttu-id="dd9d4-151">7</span><span class="sxs-lookup"><span data-stu-id="dd9d4-151">7</span></span>|<span data-ttu-id="dd9d4-152">未定義</span><span class="sxs-lookup"><span data-stu-id="dd9d4-152">Undefined</span></span>|  
|<span data-ttu-id="dd9d4-153">8</span><span class="sxs-lookup"><span data-stu-id="dd9d4-153">8</span></span>|<span data-ttu-id="dd9d4-154">未使用</span><span class="sxs-lookup"><span data-stu-id="dd9d4-154">Not used</span></span>|  
|<span data-ttu-id="dd9d4-155">9</span><span class="sxs-lookup"><span data-stu-id="dd9d4-155">9</span></span>|`SLong`|  
|<span data-ttu-id="dd9d4-156">10</span><span class="sxs-lookup"><span data-stu-id="dd9d4-156">10</span></span>|`SRational`|  
  
## <a name="example"></a><span data-ttu-id="dd9d4-157">範例</span><span class="sxs-lookup"><span data-stu-id="dd9d4-157">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="dd9d4-158">描述</span><span class="sxs-lookup"><span data-stu-id="dd9d4-158">Description</span></span>  
 <span data-ttu-id="dd9d4-159">下列程式碼範例會讀取並顯示檔案中的中繼資料的七個片段`FakePhoto.jpg`。</span><span class="sxs-lookup"><span data-stu-id="dd9d4-159">The following code example reads and displays the seven pieces of metadata in the file `FakePhoto.jpg`.</span></span> <span data-ttu-id="dd9d4-160">在清單中的第二個 （索引 1） 屬性項目具有<xref:System.Drawing.Imaging.PropertyItem.Id%2A>0x010F （設備製造商） 和<xref:System.Drawing.Imaging.PropertyItem.Type%2A>2 （ASCII 編碼的位元組陣列）。</span><span class="sxs-lookup"><span data-stu-id="dd9d4-160">The second (index 1) property item in the list has <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (equipment manufacturer) and <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (ASCII-encoded byte array).</span></span> <span data-ttu-id="dd9d4-161">在程式碼範例會顯示該屬性項目的值。</span><span class="sxs-lookup"><span data-stu-id="dd9d4-161">The code example displays the value of that property item.</span></span>  
  
 <span data-ttu-id="dd9d4-162">程式碼會產生類似下面的輸出：</span><span class="sxs-lookup"><span data-stu-id="dd9d4-162">The code produces output similar to the following:</span></span>  
 
```
 Property Item 0
  
 id: 0x320
  
 type: 2
 
 length: 16 bytes 
  
 Property Item 1
  
 id: 0x10f
  
 type: 2 
  
 length: 17 bytes
  
 Property Item 2
  
 id: 0x110
  
 type: 2
  
 length: 7 bytes
  
 Property Item 3
  
 id: 0x9003
  
 type: 2
  
 length: 20 bytes
  
 Property Item 4
  
 id: 0x829a
  
 type: 5
  
 length: 8 bytes
  
 Property Item 5
  
 id: 0x5090
  
 type: 3
  
 length: 128 bytes
  
 Property Item 6
  
 id: 0x5091
  
 type: 3
  
 length: 128 bytes
  
 The equipment make is Northwind Camera.
 ```
  
### <a name="code"></a><span data-ttu-id="dd9d4-163">程式碼</span><span class="sxs-lookup"><span data-stu-id="dd9d4-163">Code</span></span>  
 [!code-csharp[System.Drawing.WorkingWithImages#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.WorkingWithImages#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="dd9d4-164">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="dd9d4-164">Compiling the Code</span></span>  
 <span data-ttu-id="dd9d4-165">上述範例中專為搭配 Windows Form 使用，而且需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="dd9d4-165">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="dd9d4-166">處理表單的<xref:System.Windows.Forms.Control.Paint>事件並將此程式碼貼到 [小畫家] 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="dd9d4-166">Handle the form's <xref:System.Windows.Forms.Control.Paint> event and paste this code into the paint event handler.</span></span> <span data-ttu-id="dd9d4-167">您必須取代`FakePhoto.jpg`映像名稱和您的系統和匯入有效的路徑與`System.Drawing.Imaging`命名空間。</span><span class="sxs-lookup"><span data-stu-id="dd9d4-167">You must replace `FakePhoto.jpg` with an image name and path valid on your system and import the `System.Drawing.Imaging` namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd9d4-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd9d4-168">See also</span></span>

- [<span data-ttu-id="dd9d4-169">影像、點陣圖和中繼檔</span><span class="sxs-lookup"><span data-stu-id="dd9d4-169">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="dd9d4-170">使用影像、點陣圖、圖示和中繼檔</span><span class="sxs-lookup"><span data-stu-id="dd9d4-170">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)

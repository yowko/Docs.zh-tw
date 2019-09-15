---
title: 作法：讀取影像中繼資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- metadata [Windows Forms], property item
- metadata [Windows Forms], reading image
ms.assetid: 72ec0b31-0be7-444a-9575-1dbcb864e0be
ms.openlocfilehash: 8294bc6596c408160a50d9d7d5e6154f66025c73
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988562"
---
# <a name="how-to-read-image-metadata"></a><span data-ttu-id="3e404-102">作法：讀取影像中繼資料</span><span class="sxs-lookup"><span data-stu-id="3e404-102">How to: Read Image Metadata</span></span>
<span data-ttu-id="3e404-103">有些影像檔案包含的中繼資料可讓您讀取以判斷影像的功能。</span><span class="sxs-lookup"><span data-stu-id="3e404-103">Some image files contain metadata that you can read to determine features of the image.</span></span> <span data-ttu-id="3e404-104">例如，數位相片可能包含您可以閱讀的中繼資料，以判斷用來捕獲影像之相機的品牌和型號。</span><span class="sxs-lookup"><span data-stu-id="3e404-104">For example, a digital photograph might contain metadata that you can read to determine the make and model of the camera used to capture the image.</span></span> <span data-ttu-id="3e404-105">使用 GDI +，您可以讀取現有的中繼資料，也可以將新的中繼資料寫入影像檔案。</span><span class="sxs-lookup"><span data-stu-id="3e404-105">With GDI+, you can read existing metadata, and you can also write new metadata to image files.</span></span>  
  
 <span data-ttu-id="3e404-106">Gdi + 會在<xref:System.Drawing.Imaging.PropertyItem>物件中儲存個別的中繼資料片段。</span><span class="sxs-lookup"><span data-stu-id="3e404-106">GDI+ stores an individual piece of metadata in a <xref:System.Drawing.Imaging.PropertyItem> object.</span></span> <span data-ttu-id="3e404-107">您可以讀取<xref:System.Drawing.Image>物件<xref:System.Drawing.Image.PropertyItems%2A>的屬性，以從檔案抓取所有中繼資料。</span><span class="sxs-lookup"><span data-stu-id="3e404-107">You can read the <xref:System.Drawing.Image.PropertyItems%2A> property of an <xref:System.Drawing.Image> object to retrieve all the metadata from a file.</span></span> <span data-ttu-id="3e404-108">屬性會傳回物件的<xref:System.Drawing.Imaging.PropertyItem>陣列。 <xref:System.Drawing.Image.PropertyItems%2A></span><span class="sxs-lookup"><span data-stu-id="3e404-108">The <xref:System.Drawing.Image.PropertyItems%2A> property returns an array of <xref:System.Drawing.Imaging.PropertyItem> objects.</span></span>  
  
 <span data-ttu-id="3e404-109">`Value` `Id` `Type` `Len`物件具有下列四個屬性：、、和。 <xref:System.Drawing.Imaging.PropertyItem></span><span class="sxs-lookup"><span data-stu-id="3e404-109">A <xref:System.Drawing.Imaging.PropertyItem> object has the following four properties: `Id`, `Value`, `Len`, and `Type`.</span></span>  
  
## <a name="id"></a><span data-ttu-id="3e404-110">ID</span><span class="sxs-lookup"><span data-stu-id="3e404-110">Id</span></span>  
 <span data-ttu-id="3e404-111">識別中繼資料專案的標記。</span><span class="sxs-lookup"><span data-stu-id="3e404-111">A tag that identifies the metadata item.</span></span> <span data-ttu-id="3e404-112">下表顯示一些可指派<xref:System.Drawing.Imaging.PropertyItem.Id%2A>給的值。</span><span class="sxs-lookup"><span data-stu-id="3e404-112">Some values that can be assigned to <xref:System.Drawing.Imaging.PropertyItem.Id%2A> are shown in the following table.</span></span>  
  
|<span data-ttu-id="3e404-113">十六進位值</span><span class="sxs-lookup"><span data-stu-id="3e404-113">Hexadecimal value</span></span>|<span data-ttu-id="3e404-114">說明</span><span class="sxs-lookup"><span data-stu-id="3e404-114">Description</span></span>|  
|-----------------------|-----------------|  
|<span data-ttu-id="3e404-115">0x0320</span><span class="sxs-lookup"><span data-stu-id="3e404-115">0x0320</span></span><br /><br /> <span data-ttu-id="3e404-116">0x010F</span><span class="sxs-lookup"><span data-stu-id="3e404-116">0x010F</span></span><br /><br /> <span data-ttu-id="3e404-117">0x0110</span><span class="sxs-lookup"><span data-stu-id="3e404-117">0x0110</span></span><br /><br /> <span data-ttu-id="3e404-118">0x9003</span><span class="sxs-lookup"><span data-stu-id="3e404-118">0x9003</span></span><br /><br /> <span data-ttu-id="3e404-119">0x829A</span><span class="sxs-lookup"><span data-stu-id="3e404-119">0x829A</span></span><br /><br /> <span data-ttu-id="3e404-120">0x5090</span><span class="sxs-lookup"><span data-stu-id="3e404-120">0x5090</span></span><br /><br /> <span data-ttu-id="3e404-121">0x5091</span><span class="sxs-lookup"><span data-stu-id="3e404-121">0x5091</span></span>|<span data-ttu-id="3e404-122">影像標題</span><span class="sxs-lookup"><span data-stu-id="3e404-122">Image title</span></span><br /><br /> <span data-ttu-id="3e404-123">設備製造商</span><span class="sxs-lookup"><span data-stu-id="3e404-123">Equipment manufacturer</span></span><br /><br /> <span data-ttu-id="3e404-124">設備型號</span><span class="sxs-lookup"><span data-stu-id="3e404-124">Equipment model</span></span><br /><br /> <span data-ttu-id="3e404-125">ExifDTOriginal</span><span class="sxs-lookup"><span data-stu-id="3e404-125">ExifDTOriginal</span></span><br /><br /> <span data-ttu-id="3e404-126">Exif 曝光時間</span><span class="sxs-lookup"><span data-stu-id="3e404-126">Exif exposure time</span></span><br /><br /> <span data-ttu-id="3e404-127">亮度資料表</span><span class="sxs-lookup"><span data-stu-id="3e404-127">Luminance table</span></span><br /><br /> <span data-ttu-id="3e404-128">色度資料表</span><span class="sxs-lookup"><span data-stu-id="3e404-128">Chrominance table</span></span>|  
  
## <a name="value"></a><span data-ttu-id="3e404-129">值</span><span class="sxs-lookup"><span data-stu-id="3e404-129">Value</span></span>  
 <span data-ttu-id="3e404-130">值的陣列。</span><span class="sxs-lookup"><span data-stu-id="3e404-130">An array of values.</span></span> <span data-ttu-id="3e404-131">值的格式取決<xref:System.Drawing.Imaging.PropertyItem.Type%2A>于屬性。</span><span class="sxs-lookup"><span data-stu-id="3e404-131">The format of the values is determined by the <xref:System.Drawing.Imaging.PropertyItem.Type%2A> property.</span></span>  
  
## <a name="len"></a><span data-ttu-id="3e404-132">長度</span><span class="sxs-lookup"><span data-stu-id="3e404-132">Len</span></span>  
 <span data-ttu-id="3e404-133"><xref:System.Drawing.Imaging.PropertyItem.Value%2A>屬性所指向之值陣列的長度（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="3e404-133">The length (in bytes) of the array of values pointed to by the <xref:System.Drawing.Imaging.PropertyItem.Value%2A> property.</span></span>  
  
## <a name="type"></a><span data-ttu-id="3e404-134">類型</span><span class="sxs-lookup"><span data-stu-id="3e404-134">Type</span></span>  
 <span data-ttu-id="3e404-135">`Value`屬性中所指向之陣列值的資料類型。</span><span class="sxs-lookup"><span data-stu-id="3e404-135">The data type of the values in the array pointed to by the `Value` property.</span></span> <span data-ttu-id="3e404-136">下表顯示`Type`屬性值所指出的格式</span><span class="sxs-lookup"><span data-stu-id="3e404-136">The formats indicated by the `Type` property values are shown in the following table</span></span>  
  
|<span data-ttu-id="3e404-137">數值</span><span class="sxs-lookup"><span data-stu-id="3e404-137">Numeric value</span></span>|<span data-ttu-id="3e404-138">描述</span><span class="sxs-lookup"><span data-stu-id="3e404-138">Description</span></span>|  
|-------------------|-----------------|  
|<span data-ttu-id="3e404-139">1</span><span class="sxs-lookup"><span data-stu-id="3e404-139">1</span></span>|<span data-ttu-id="3e404-140">`Byte`</span><span class="sxs-lookup"><span data-stu-id="3e404-140">A `Byte`</span></span>|  
|<span data-ttu-id="3e404-141">2</span><span class="sxs-lookup"><span data-stu-id="3e404-141">2</span></span>|<span data-ttu-id="3e404-142">編碼為 ASCII `Byte`的物件陣列</span><span class="sxs-lookup"><span data-stu-id="3e404-142">An array of `Byte` objects encoded as ASCII</span></span>|  
|<span data-ttu-id="3e404-143">3</span><span class="sxs-lookup"><span data-stu-id="3e404-143">3</span></span>|<span data-ttu-id="3e404-144">16位整數</span><span class="sxs-lookup"><span data-stu-id="3e404-144">A 16-bit integer</span></span>|  
|<span data-ttu-id="3e404-145">4</span><span class="sxs-lookup"><span data-stu-id="3e404-145">4</span></span>|<span data-ttu-id="3e404-146">32位整數</span><span class="sxs-lookup"><span data-stu-id="3e404-146">A 32-bit integer</span></span>|  
|<span data-ttu-id="3e404-147">5</span><span class="sxs-lookup"><span data-stu-id="3e404-147">5</span></span>|<span data-ttu-id="3e404-148">代表有理數的兩`Byte`個物件的陣列</span><span class="sxs-lookup"><span data-stu-id="3e404-148">An array of two `Byte` objects that represent a rational number</span></span>|  
|<span data-ttu-id="3e404-149">6</span><span class="sxs-lookup"><span data-stu-id="3e404-149">6</span></span>|<span data-ttu-id="3e404-150">未使用</span><span class="sxs-lookup"><span data-stu-id="3e404-150">Not used</span></span>|  
|<span data-ttu-id="3e404-151">7</span><span class="sxs-lookup"><span data-stu-id="3e404-151">7</span></span>|<span data-ttu-id="3e404-152">未定義</span><span class="sxs-lookup"><span data-stu-id="3e404-152">Undefined</span></span>|  
|<span data-ttu-id="3e404-153">8</span><span class="sxs-lookup"><span data-stu-id="3e404-153">8</span></span>|<span data-ttu-id="3e404-154">未使用</span><span class="sxs-lookup"><span data-stu-id="3e404-154">Not used</span></span>|  
|<span data-ttu-id="3e404-155">9</span><span class="sxs-lookup"><span data-stu-id="3e404-155">9</span></span>|`SLong`|  
|<span data-ttu-id="3e404-156">10</span><span class="sxs-lookup"><span data-stu-id="3e404-156">10</span></span>|`SRational`|  
  
## <a name="example"></a><span data-ttu-id="3e404-157">範例</span><span class="sxs-lookup"><span data-stu-id="3e404-157">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="3e404-158">描述</span><span class="sxs-lookup"><span data-stu-id="3e404-158">Description</span></span>  
 <span data-ttu-id="3e404-159">下列程式碼範例會讀取並顯示檔案中`FakePhoto.jpg`的七段中繼資料。</span><span class="sxs-lookup"><span data-stu-id="3e404-159">The following code example reads and displays the seven pieces of metadata in the file `FakePhoto.jpg`.</span></span> <span data-ttu-id="3e404-160">清單中的第二個（索引1）屬性專案<xref:System.Drawing.Imaging.PropertyItem.Id%2A>具有0x010F （設備製造商） <xref:System.Drawing.Imaging.PropertyItem.Type%2A>和2（ASCII 編碼的位元組陣列）。</span><span class="sxs-lookup"><span data-stu-id="3e404-160">The second (index 1) property item in the list has <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (equipment manufacturer) and <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (ASCII-encoded byte array).</span></span> <span data-ttu-id="3e404-161">此程式碼範例會顯示該屬性專案的值。</span><span class="sxs-lookup"><span data-stu-id="3e404-161">The code example displays the value of that property item.</span></span>  
  
 <span data-ttu-id="3e404-162">程式碼會產生類似下列的輸出：</span><span class="sxs-lookup"><span data-stu-id="3e404-162">The code produces output similar to the following:</span></span>  
 
```output
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
  
### <a name="code"></a><span data-ttu-id="3e404-163">程式碼</span><span class="sxs-lookup"><span data-stu-id="3e404-163">Code</span></span>  
 [!code-csharp[System.Drawing.WorkingWithImages#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.WorkingWithImages#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3e404-164">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="3e404-164">Compiling the Code</span></span>  
 <span data-ttu-id="3e404-165">上述範例是針對與 Windows Forms 搭配使用所設計，而且它<xref:System.Windows.Forms.PaintEventArgs>需要`e`，這<xref:System.Windows.Forms.Control.Paint>是事件處理常式的參數。</span><span class="sxs-lookup"><span data-stu-id="3e404-165">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="3e404-166">處理表單的<xref:System.Windows.Forms.Control.Paint>事件，並將此程式碼貼入繪製事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="3e404-166">Handle the form's <xref:System.Windows.Forms.Control.Paint> event and paste this code into the paint event handler.</span></span> <span data-ttu-id="3e404-167">您必須將`FakePhoto.jpg`取代為您的系統上有效的映射名稱和路徑， `System.Drawing.Imaging`並匯入命名空間。</span><span class="sxs-lookup"><span data-stu-id="3e404-167">You must replace `FakePhoto.jpg` with an image name and path valid on your system and import the `System.Drawing.Imaging` namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e404-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e404-168">See also</span></span>

- [<span data-ttu-id="3e404-169">影像、點陣圖和中繼檔</span><span class="sxs-lookup"><span data-stu-id="3e404-169">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="3e404-170">使用影像、點陣圖、圖示和中繼檔</span><span class="sxs-lookup"><span data-stu-id="3e404-170">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)

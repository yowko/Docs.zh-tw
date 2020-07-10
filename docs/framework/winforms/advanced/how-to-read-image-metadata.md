---
title: 如何：讀取影像中繼資料
desription: Learn how to read the Windows Forms PropertyItems property of an Image object to retrieve all the metadata from a file.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- metadata [Windows Forms], property item
- metadata [Windows Forms], reading image
ms.assetid: 72ec0b31-0be7-444a-9575-1dbcb864e0be
ms.openlocfilehash: 814cb17feba1e1e3a42b2bc403b0b4c828caf90e
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174662"
---
# <a name="how-to-read-image-metadata"></a>如何：讀取影像中繼資料

有些影像檔案包含的中繼資料可讓您讀取以判斷影像的功能。 例如，數位相片可能包含您可以閱讀的中繼資料，以判斷用來捕獲影像之相機的品牌和型號。 使用 GDI +，您可以讀取現有的中繼資料，也可以將新的中繼資料寫入影像檔案。

GDI + 會在物件中儲存個別的中繼資料片段 <xref:System.Drawing.Imaging.PropertyItem> 。 您可以讀取 <xref:System.Drawing.Image.PropertyItems%2A> 物件的屬性 <xref:System.Drawing.Image> ，以從檔案抓取所有中繼資料。 屬性會傳回 <xref:System.Drawing.Image.PropertyItems%2A> 物件的陣列 <xref:System.Drawing.Imaging.PropertyItem> 。

<xref:System.Drawing.Imaging.PropertyItem>物件具有下列四個屬性： `Id` 、 `Value` 、 `Len` 和 `Type` 。

## <a name="id"></a>識別碼

識別中繼資料專案的標記。 下表顯示一些可指派給的值 <xref:System.Drawing.Imaging.PropertyItem.Id%2A> ：

|十六進位值|描述|
|-----------------------|-----------------|
|0x0320<br /><br /> 0x010F<br /><br /> 0x0110<br /><br /> 0x9003<br /><br /> 0x829A<br /><br /> 0x5090<br /><br /> 0x5091|影像標題<br /><br /> 設備製造商<br /><br /> 設備型號<br /><br /> ExifDTOriginal<br /><br /> Exif 曝光時間<br /><br /> 亮度資料表<br /><br /> 色度資料表|

## <a name="value"></a>值

值的陣列。 值的格式取決於 <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 屬性。

## <a name="len"></a>Len

屬性所指向之值陣列的 (長度，以位元組為單位) <xref:System.Drawing.Imaging.PropertyItem.Value%2A> 。

## <a name="type"></a>類型

屬性中所指向之陣列值的資料類型 `Value` 。 `Type`下表顯示內容值所指出的格式：

|數值|描述|
|-------------------|-----------------|
|1|進行 `Byte`|
|2|`Byte`編碼為 ASCII 的物件陣列|
|3|16位整數|
|4|32位整數|
|5|代表有理數的兩個物件的陣列 `Byte`|
|6|未使用|
|7|未定義|
|8|未使用|
|9|`SLong`|
|10|`SRational`|

## <a name="example"></a>範例
  
下列程式碼範例會讀取並顯示檔案中的七段中繼資料 `FakePhoto.jpg` 。 清單中的第二個 (index 1) 屬性專案具有 <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (設備製造商) 和 <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (ASCII 編碼的位元組陣列) 。 此程式碼範例會顯示該屬性專案的值。

[!code-csharp[System.Drawing.WorkingWithImages#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
[!code-vb[System.Drawing.WorkingWithImages#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]

程式碼會產生類似下列的輸出：

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

## <a name="compiling-the-code"></a>編譯程式碼

上述範例是針對與 Windows Forms 搭配使用所設計，而且它需要 <xref:System.Windows.Forms.PaintEventArgs> `e` ，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。 處理表單的 <xref:System.Windows.Forms.Control.Paint> 事件，並將此程式碼貼入繪製事件處理常式。 您必須將取代 `FakePhoto.jpg` 為您的系統上有效的映射名稱和路徑，並匯入 `System.Drawing.Imaging` 命名空間。

## <a name="see-also"></a>另請參閱

- [影像、點陣圖和中繼檔](images-bitmaps-and-metafiles.md)
- [使用影像、點陣圖、圖示和中繼檔](working-with-images-bitmaps-icons-and-metafiles.md)

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
ms.openlocfilehash: cd3b636f8f0058d4a8eacc656f95d5f46b8967e2
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040746"
---
# <a name="how-to-read-image-metadata"></a>如何：讀取影像中繼資料

有些影像檔案包含的中繼資料可讓您讀取以判斷影像的功能。 例如，數位相片可能包含您可以閱讀的中繼資料，以判斷用來捕獲影像之相機的品牌和型號。 使用 GDI +，您可以讀取現有的中繼資料，也可以將新的中繼資料寫入影像檔案。

GDI + 會將個別的中繼資料儲存在 <xref:System.Drawing.Imaging.PropertyItem> 物件中。 您可以讀取 <xref:System.Drawing.Image> 物件的 <xref:System.Drawing.Image.PropertyItems%2A> 屬性，以從檔案中取出所有中繼資料。 <xref:System.Drawing.Image.PropertyItems%2A> 屬性會傳回 <xref:System.Drawing.Imaging.PropertyItem> 物件的陣列。

<xref:System.Drawing.Imaging.PropertyItem> 物件具有下列四個屬性： `Id`、`Value`、`Len`和 `Type`。

## <a name="id"></a>ID

識別中繼資料專案的標記。 下表顯示一些可指派給 <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 的值：

|十六進位值|描述|
|-----------------------|-----------------|
|0x0320<br /><br /> 0x010F<br /><br /> 0x0110<br /><br /> 0x9003<br /><br /> 0x829A<br /><br /> 0x5090<br /><br /> 0x5091|影像標題<br /><br /> 設備製造商<br /><br /> 設備型號<br /><br /> ExifDTOriginal<br /><br /> Exif 曝光時間<br /><br /> 亮度資料表<br /><br /> 色度資料表|

## <a name="value"></a>值

值的陣列。 值的格式取決於 <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 屬性。

## <a name="len"></a>長度

<xref:System.Drawing.Imaging.PropertyItem.Value%2A> 屬性所指向之值陣列的長度（以位元組為單位）。

## <a name="type"></a>輸入

`Value` 屬性所指向陣列中值的資料類型。 下表顯示 `Type` 屬性值所指出的格式：

|數值|描述|
|-------------------|-----------------|
|1|`Byte`|
|2|編碼為 ASCII 的 `Byte` 物件陣列|
|3|16位整數|
|4|32位整數|
|5|代表有理數之兩個 `Byte` 物件的陣列|
|6|未使用|
|7|未定義|
|8|未使用|
|9|`SLong`|
|10|`SRational`|

## <a name="example"></a>範例
  
下列程式碼範例會在檔案 `FakePhoto.jpg`中讀取和顯示七段中繼資料。 清單中的第二個（索引1）屬性專案具有 <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F （設備製造商）和 <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 （ASCII 編碼的位元組陣列）。 此程式碼範例會顯示該屬性專案的值。

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

上述範例是針對與 Windows Forms 搭配使用所設計，而且需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。 處理表單的 <xref:System.Windows.Forms.Control.Paint> 事件，並將這段程式碼貼入繪製事件處理常式中。 您必須以您系統上的有效映射名稱和路徑來取代 `FakePhoto.jpg`，並匯入 `System.Drawing.Imaging` 命名空間。

## <a name="see-also"></a>請參閱

- [影像、點陣圖和中繼檔](images-bitmaps-and-metafiles.md)
- [使用影像、點陣圖、圖示和中繼檔](working-with-images-bitmaps-icons-and-metafiles.md)

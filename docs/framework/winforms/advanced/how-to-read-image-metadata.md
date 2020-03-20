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
ms.openlocfilehash: e2b56175e625281a920c390e5feb4238e3cb7f44
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182513"
---
# <a name="how-to-read-image-metadata"></a>如何：讀取影像中繼資料

某些影像檔包含中繼資料，您可以讀取中繼資料以確定圖像的功能。 例如，數位照片可能包含中繼資料，您可以讀取中繼資料來確定用於捕獲圖像的相機的製作和型號。 使用 GDI+，您可以讀取現有中繼資料，還可以將新的中繼資料寫入影像檔。

GDI+ 將單個中繼資料段存儲在<xref:System.Drawing.Imaging.PropertyItem>物件中。 可以讀取<xref:System.Drawing.Image.PropertyItems%2A><xref:System.Drawing.Image>物件的屬性以從檔檢索所有中繼資料。 屬性<xref:System.Drawing.Image.PropertyItems%2A>返回物件陣列<xref:System.Drawing.Imaging.PropertyItem>。

物件<xref:System.Drawing.Imaging.PropertyItem>`Id`具有以下四個屬性： 、 `Value` `Len`和`Type`。

## <a name="id"></a>Id

標識中繼資料項的標記。 下表中顯示了可以分配給<xref:System.Drawing.Imaging.PropertyItem.Id%2A>的一些值：

|十六進位值|描述|
|-----------------------|-----------------|
|0 x0320<br /><br /> 0x010F<br /><br /> 0x0110<br /><br /> 0 x9003<br /><br /> 0 x829A<br /><br /> 0 x5090<br /><br /> 0 x5091|圖像標題<br /><br /> 設備製造商<br /><br /> 設備型號<br /><br /> ExifDT 原始<br /><br /> Exif 曝光時間<br /><br /> 亮度表<br /><br /> 色度表|

## <a name="value"></a>值

值的陣列。 值的格式由<xref:System.Drawing.Imaging.PropertyItem.Type%2A>屬性確定。

## <a name="len"></a>Len

<xref:System.Drawing.Imaging.PropertyItem.Value%2A>屬性指向的值陣列的長度（以位元組為單位）。

## <a name="type"></a>類型

屬性指向的陣列中值的`Value`資料類型。 屬性值指示的`Type`格式顯示在下表中：

|數值|描述|
|-------------------|-----------------|
|1|`Byte`。|
|2|編碼為`Byte`ASCII 的物件陣列|
|3|16 位整數|
|4|32 位整數|
|5|表示合理數位的`Byte`兩個物件的陣列|
|6|未使用|
|7|未定義|
|8|未使用|
|9|`SLong`|
|10|`SRational`|

## <a name="example"></a>範例
  
以下代碼示例讀取並顯示檔中`FakePhoto.jpg`的七個中繼資料片段。 清單中的第二個（索引 1）屬性項具有<xref:System.Drawing.Imaging.PropertyItem.Id%2A>0x010F（設備製造商）和<xref:System.Drawing.Imaging.PropertyItem.Type%2A>2（ASCII 編碼位元組陣列）。 代碼示例顯示該屬性項的值。

[!code-csharp[System.Drawing.WorkingWithImages#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
[!code-vb[System.Drawing.WorkingWithImages#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]

該代碼生成類似于以下內容的輸出：

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

前面的示例設計用於 Windows 表單，它需要<xref:System.Windows.Forms.PaintEventArgs>`e`，這是事件處理常式的<xref:System.Windows.Forms.Control.Paint>參數。 處理表單<xref:System.Windows.Forms.Control.Paint>的事件並將此代碼粘貼到繪製事件處理常式中。 您必須替換為`FakePhoto.jpg`系統上有效的圖像名稱和路徑，`System.Drawing.Imaging`並導入命名空間。

## <a name="see-also"></a>另請參閱

- [影像、點陣圖和中繼檔](images-bitmaps-and-metafiles.md)
- [使用影像、點陣圖、圖示和中繼檔](working-with-images-bitmaps-icons-and-metafiles.md)

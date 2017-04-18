---
title: "如何：讀取影像中繼資料 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "中繼資料, 屬性項目"
  - "中繼資料, 讀取影像"
ms.assetid: 72ec0b31-0be7-444a-9575-1dbcb864e0be
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：讀取影像中繼資料
有些影像檔案中會包含中繼資料 \(Metadata\)，您可以讀取這項資料來判斷影像的特性。  例如，讀取數位相片中所包含的中繼資料，可以判斷出捕捉影像時所使用的相機品牌和型號。  在 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 中，可以讀取現有的中繼資料，也可以將新的中繼資料寫入影像檔案中。  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 會將各筆中繼資料儲存在 <xref:System.Drawing.Imaging.PropertyItem> 物件中。  您可以讀取 <xref:System.Drawing.Image> 物件的 <xref:System.Drawing.Image.PropertyItems%2A> 屬性來擷取檔案中的所有中繼資料。  <xref:System.Drawing.Image.PropertyItems%2A> 屬性會傳回 <xref:System.Drawing.Imaging.PropertyItem> 物件的陣列。  
  
 <xref:System.Drawing.Imaging.PropertyItem> 物件具有下列四個屬性：`Id`、`Value`、`Len` 和 `Type`。  
  
## Id  
 識別中繼資料項目的標記 \(Tag\)。  部分可指派給 <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 的值列在下表中。  
  
|十六進位值|描述|  
|-----------|--------|  
|0x0320<br /><br /> 0x010F<br /><br /> 0x0110<br /><br /> 0x9003<br /><br /> 0x829A<br /><br /> 0x5090<br /><br /> 0x5091|影像標題<br /><br /> 設備製造商<br /><br /> 設備型號<br /><br /> ExifDTOriginal<br /><br /> Exif 曝光時間<br /><br /> 亮度表<br /><br /> 色度表|  
  
## 值  
 值的陣列。  值的格式是由 <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 屬性判斷。  
  
## Len  
 <xref:System.Drawing.Imaging.PropertyItem.Value%2A> 屬性所指向之值的陣列的長度 \(以位元組為單位\)。  
  
## 型別  
 `Value` 屬性所指向之陣列中值的資料型別。  `Type` 屬性值所表示的格式列在下表中。  
  
|數值|描述|  
|--------|--------|  
|1|`Byte`|  
|2|以 ASCII 編碼之 `Byte` 物件的陣列|  
|3|16 位元整數|  
|4|32 位元整數|  
|5|代表有理數之兩個 `Byte` 物件的陣列|  
|6|未使用|  
|7|未定義|  
|8|未使用|  
|9|`SLong`|  
|10|`SRational`|  
  
## 範例  
  
### 描述  
 下列程式碼範例會讀取並顯示 `FakePhoto.jpg` 檔案中的七筆中繼資料。  清單中第二個 \(索引為 1\) 屬性項目的 <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 為 0x010F \(設備製造商\)，<xref:System.Drawing.Imaging.PropertyItem.Type%2A> 為 2 \(以 ASCII 編碼的位元組陣列\)。  這個程式碼範例將顯示該屬性項目的值。  
  
 這個程式碼所產生的輸出與下列類似：  
  
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
  
### 程式碼  
 [!code-csharp[System.Drawing.WorkingWithImages#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.WorkingWithImages#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]  
  
## 編譯程式碼  
 上述範例是專為與 Windows Form 搭配使用而設計的，而且它需要 <xref:System.Windows.Forms.PaintEventArgs> `e` \(即 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數\)。  處理表單的 <xref:System.Windows.Forms.Control.Paint> 事件，並將此程式碼貼入繪製事件處理常式中。  您必須以系統中有效的影像名稱和路徑來取代 `FakePhoto.jpg`，並匯入 `System.Drawing.Imaging` 命名空間。  
  
## 請參閱  
 [影像、點陣圖和中繼檔](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)   
 [使用影像、點陣圖、圖示和中繼檔](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
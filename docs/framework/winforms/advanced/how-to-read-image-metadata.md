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
ms.openlocfilehash: eba21519e6ea6cf4a2a412750fd305d7af620c1b
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720784"
---
# <a name="how-to-read-image-metadata"></a>HOW TO：讀取影像中繼資料
某些影像檔包含中繼資料，您可以讀取來判斷映像的功能。 比方說，數位相片可能包含您可以讀取來判斷的廠牌與型號，用來擷取影像之相機的中繼資料。 使用[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]，您可以讀取現有的中繼資料，您也可以撰寫新的中繼資料映像檔案。  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 儲存中繼資料中段個別<xref:System.Drawing.Imaging.PropertyItem>物件。 您可以閱讀<xref:System.Drawing.Image.PropertyItems%2A>屬性<xref:System.Drawing.Image>要從檔案擷取所有中繼資料物件。 <xref:System.Drawing.Image.PropertyItems%2A>屬性傳回的陣列<xref:System.Drawing.Imaging.PropertyItem>物件。  
  
 A<xref:System.Drawing.Imaging.PropertyItem>物件具有下列四個屬性： `Id`， `Value`， `Len`，和`Type`。  
  
## <a name="id"></a>ID  
 標記可識別中繼資料項目。 某些值，可以指派給<xref:System.Drawing.Imaging.PropertyItem.Id%2A>下表所示。  
  
|十六進位值|描述|  
|-----------------------|-----------------|  
|0x0320<br /><br /> 0x010F<br /><br /> 0x0110<br /><br /> 0x9003<br /><br /> 0x829A<br /><br /> 0x5090<br /><br /> 0x5091|映像標題<br /><br /> 設備製造商<br /><br /> 設備型號<br /><br /> ExifDTOriginal<br /><br /> Exif 曝光時間<br /><br /> 亮度表<br /><br /> 色差表|  
  
## <a name="value"></a>值  
 值的陣列。 值的格式取決於<xref:System.Drawing.Imaging.PropertyItem.Type%2A>屬性。  
  
## <a name="len"></a>長度  
 一維陣列的值的長度 （以位元組為單位） 所指的<xref:System.Drawing.Imaging.PropertyItem.Value%2A>屬性。  
  
## <a name="type"></a>類型  
 陣列中值的資料類型所指的`Value`屬性。 所表示之格式`Type`下表顯示屬性值  
  
|數字值|描述|  
|-------------------|-----------------|  
|1|
  `Byte`
|  
|2|陣列`Byte`為 ASCII 編碼的物件|  
|3|16 位元整數|  
|4|32 位元整數|  
|5|兩個陣列`Byte`表示有理數的物件|  
|6|未使用|  
|7|未定義|  
|8|未使用|  
|9|`SLong`|  
|10|`SRational`|  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下列程式碼範例會讀取並顯示檔案中的中繼資料的七個片段`FakePhoto.jpg`。 在清單中的第二個 （索引 1） 屬性項目具有<xref:System.Drawing.Imaging.PropertyItem.Id%2A>0x010F （設備製造商） 和<xref:System.Drawing.Imaging.PropertyItem.Type%2A>2 （ASCII 編碼的位元組陣列）。 在程式碼範例會顯示該屬性項目的值。  
  
 程式碼會產生類似下面的輸出：  
  
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
  
### <a name="code"></a>程式碼  
 [!code-csharp[System.Drawing.WorkingWithImages#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.WorkingWithImages#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。 處理表單的<xref:System.Windows.Forms.Control.Paint>事件並將此程式碼貼到 [小畫家] 事件處理常式。 您必須取代`FakePhoto.jpg`映像名稱和您的系統和匯入有效的路徑與`System.Drawing.Imaging`命名空間。  
  
## <a name="see-also"></a>另請參閱
- [影像、點陣圖和中繼檔](images-bitmaps-and-metafiles.md)
- [使用影像、點陣圖、圖示和中繼檔](working-with-images-bitmaps-icons-and-metafiles.md)

---
title: 點陣圖類型
ms.date: 03/30/2017
helpviewer_keywords:
- jpeg files
- TIFF files
- gif files
- Graphics Interchange Format
- Joint Photographic Experts Group
- .jpeg files
- .gif files
- graphics [Windows Forms], file formats
- images [Windows Forms], file formats
- Portable Network Graphics
- .bmp files
- EXIF file format
- PNG files
- pictures [Windows Forms], file formats
- Tag Image File Format
- bitmaps [Windows Forms], file format
- Exchangeable Image File
ms.assetid: 6be085a2-2c13-47c8-b80a-c18b32777d8d
ms.openlocfilehash: 3083c075bfbbd21a26f7442f9bbccbe800d73cf1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674764"
---
# <a name="types-of-bitmaps"></a>點陣圖類型
點陣圖會指定每個像素色彩的像素矩形陣列中的位元陣列。 組成個別像素的位元數目會決定可以指派給該像素的色彩數目。 比方說，如果每個像素 4 個位元來表示，然後指定像素可以指派其中一個 16 不同的色彩 (2 ^4 = 16 個)。 下表顯示一些範例可以指派給像素，以表示指定之位元數的色彩數目。  
  
|每個像素的位元|可以指派給像素的色彩數目|  
|--------------------|------------------------------------------------------|  
|1|2^1 = 2|  
|2|2^2 = 4|  
|4|2^4 = 16|  
|8|2^8 = 256|  
|16|2^16 = 65,536|  
|24|2^24 = 16,777,216|  
  
 通常儲存點陣圖的磁碟檔案包含一或多個資訊區塊儲存在陣列中的資訊，例如每個像素、 像素的每個資料列，以及資料列數目的位元數。 這類檔案可能也會包含色彩表 （有時稱為調色盤）。 色彩表會將點陣圖中的數字對應到特定的色彩。 下圖顯示放大的影像，以及其點陣圖和色彩的資料表。 每個像素以 4 位元數字，因此會有 2 ^4 = 16 個色彩，色彩表中。 在資料表中的每一種色彩被以 24 位元數字：8 位元用於紅色、 綠色的 8 位元和 8 位元用於藍色。 數字是以十六進位 (基底 16) 格式所示：A = 10，B = 11，C = 12，D = 13，E = 14、 F = 15。  
  
 ![點陣圖範例](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art01.gif "AboutGdip03_Art01")  
  
 看看第 3 欄 5 的映像的資料列中的像素。 點陣圖中對應的數字為 1。 色彩表將告訴我們，1 代表紅色的色彩，因此像素都是紅色。 在頂端列中的所有項目都是點陣圖的 3。 色彩表會告訴我們 3 代表藍色，因此會以藍色顯示之影像的頂端列中的所有像素。  
  
> [!NOTE]
>  某些點陣圖格式儲存在由下往上;點陣圖的第一個資料列中的數字對應到影像的下方資料列中的像素。  
  
 將索引儲存到色彩表的點陣圖稱為調色盤編製索引的點陣圖。 有些點陣圖並不需要色彩表。 比方說，如果點陣圖使用每像素 24 位元，該點陣圖可以儲存自己的色彩，而不是索引色彩表中。 下圖顯示儲存直接 （24 位元 / 像素） 色彩的點陣圖，而不是使用色彩表。 此圖解同時顯示對應的影像的放大的檢視。 在點陣圖，FFFFFF 表示白色、 FF0000 代表紅色、 00FF00 代表綠色，而 0000ff> 中代表藍色。  
  
 ![點陣圖範例](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art02.gif "AboutGdip03_Art02")  
  
## <a name="graphics-file-formats"></a>圖形檔格式  
 有許多標準格式，將點陣圖儲存在磁碟檔案。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 支援的圖形檔案下列段落中所述的格式。  
  
### <a name="bmp"></a>BMP  
 BMP 是使用 Windows 儲存裝置和應用程式無關的映像的標準格式。 檔案標頭中指定的每個像素 （1、 4、 8、 15、 24、 32 或 64） 指定 BMP 檔案的位元數。 每個像素 24 位元的 BMP 檔案很常見。 BMP 檔案通常不會壓縮，因此，不適合用來傳輸在網際網路上。  
  
### <a name="graphics-interchange-format-gif"></a>圖形交換格式 (GIF)  
 GIF 是出現在網頁的映像的一般格式。 Gif 適用於線條繪圖、 使用的純色，區塊的圖片和圖片與銳利色彩之間的界限。 Gif 被壓縮，而且壓縮程序; 不會損失任何資訊解壓縮後的映像正是與原來相同。 Gif 的一種色彩可以指定為透明的如此將會有顯示它的任何網頁上的背景色彩的影像。 一連串的 GIF 影像可以儲存在單一檔案，以形成的動畫的 GIF。 Gif 會儲存最多每像素 8 位元，所以它們被限制為 256 種色彩。  
  
### <a name="joint-photographic-experts-group-jpeg"></a>Joint Photographic Experts Group (JPEG)  
 JPEG 非常適用於自然的場景，例如掃描照片的壓縮配置。 在壓縮過程中，會遺失一些資訊，但通常是無法察覺到人們的眼睛遺失。 Jpeg 會儲存 24 個位元 / 像素，因此它們可以顯示多個 16 萬種色彩。 Jpeg 不支援透明度或動畫。  
  
 JPEG 影像壓縮層級設定，但較高的壓縮層級 （較小的檔案） 會造成多個遺失的資訊。 20:1 的壓縮比率通常會產生肉眼難以區別從原始的映像。 下圖顯示 BMP 影像和兩個從該 BMP 影像已壓縮的 JPEG 影像。 第一個 JPEG 壓縮比率為 4:1，第二個 JPEG 大約 8:1 壓縮率。  
  
 ![檔案類型範例](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art03.gif "AboutGdip03_Art03")  
  
 JPEG 壓縮不會適用於線條繪圖，區塊的單色，並明確的界限。 下圖顯示兩個 Jpeg GIF 及 BMP。 BMP 從壓縮的 Jpeg 和 GIF。 壓縮比率為 4:1 GIF、 4:1，較小的 jpeg，和 8:3 的較大的 JPEG。 請注意 GIF 維護程式碼行，以及明確的界限，但 Jpeg 似乎比較模糊的界限。  
  
 ![Filetypes](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art03a.gif "AboutGdip03_Art03A")  
  
 JPEG 是一種壓縮配置，不是檔案格式。 JPEG 檔案交換格式 (JFIF) 是常用於儲存和轉送已根據 JPEG 配置壓縮的影像檔案格式。 網頁瀏覽器所顯示的 JFIF 檔案使用.jpg 副檔名。  
  
### <a name="exchangeable-image-file-exif"></a>可交換影像檔案 (EXIF)  
 EXIF 是用數位相機所擷取的相片的檔案格式。 EXIF 檔案包含壓縮的 JPEG 規格根據映像。 EXIF 檔案也包含相片的相關資訊 （拍攝日期、 快門速度、 曝光時間等等） 以及相機 （製造商、 型號及等等） 的相關資訊。  
  
### <a name="portable-network-graphics-png"></a>Portable Network Graphics (PNG)  
 PNG 格式會保留眾多的 GIF 格式的優點，但也提供功能的 GIF。 GIF 檔，像是 PNG 檔案會壓縮不會遺失的資訊。 PNG 檔案可以儲存 8、 24 日或每個像素和灰階 1、 2、 4、 8、 48 位元或每像素 16 位元的色彩。 相反地，只有 1、 2、 4 或 8 位元 / 像素，可以使用 GIF 檔案。 PNG 檔案也可以儲存每個像素指定的程度該像素的色彩混合使用的背景色彩的 alpha 值。  
  
 GIF PNG 改進，以漸進方式顯示影像的能力 （也就是要顯示映像的更好和更好的近似值，因為它抵達網路連接）。 PNG 檔案可以包含 gamma 修正和色彩修正的資訊，讓映像可以在各種不同的顯示裝置上正確轉譯。  
  
### <a name="tag-image-file-format-tiff"></a>標記的影像檔案格式 (TIFF)  
 TIFF 是富彈性且可擴充的格式支援的各種不同的平台和映像處理的應用程式。 TIFF 檔案可以儲存任意數目的每個像素的位元映像，而且可以利用各種不同的壓縮演算法。 數個映像可以儲存在單一、 多頁的 TIFF 檔中。 映像 （掃描器製作，主機電腦，類型壓縮、 方向、 每像素，並依此類推樣本） 相關的資訊可以儲存在檔案中，並透過標記使用排列。 可以擴充 TIFF 格式，視需要加入新的標記與核准。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Drawing.Image?displayProperty=nameWithType>
- <xref:System.Drawing.Bitmap?displayProperty=nameWithType>
- <xref:System.Drawing.Imaging.PixelFormat?displayProperty=nameWithType>
- [影像、點陣圖和中繼檔](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
- [使用影像、點陣圖、圖示和中繼檔](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)

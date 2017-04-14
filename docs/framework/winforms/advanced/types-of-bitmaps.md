---
title: "點陣圖類型 | Microsoft Docs"
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
  - ".bmp 檔案"
  - ".gif 檔案"
  - ".jpeg 檔案"
  - "點陣圖 [Windows Form], 檔案格式"
  - "可交換的影像檔"
  - "EXIF 檔案格式"
  - "GIF 檔"
  - "圖形 [Windows Form], 檔案格式"
  - "圖形交換格式 (GIF)"
  - "影像 [Windows Form], 檔案格式"
  - "Joint Photographic Experts Group (JPEG)"
  - "jpeg 檔案"
  - "圖片, 檔案格式"
  - "PNG 檔案"
  - "可攜式網路圖形"
  - "TIF 檔案格式"
  - "TIFF 檔案"
ms.assetid: 6be085a2-2c13-47c8-b80a-c18b32777d8d
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 點陣圖類型
點陣圖是位元陣列，指定矩形陣列 \(Rectangular Array\) 像素中的每個像素色彩。  個別像素的組成位元數將決定指派給該像素的色彩數目。  例如，如果每個像素都是由 4 個位元組成，則可將指定像素指派給 16 個不同的色彩之一 \(2^4 \= 16\)。  下表將顯示一些範例，說明可指派給由指定位元數所表示的像素的色彩數目。  
  
|每像素位元數|可指派給像素的色彩數目|  
|------------|-----------------|  
|1|2^1 \= 2|  
|2|2^2 \= 4|  
|4|2^4 \= 16|  
|8|2^8 \= 256|  
|16|2^16 \= 65,536|  
|24|2^24 \= 16,777,216|  
  
 儲存點陣圖的磁片檔案通常都會包含一或多個資訊區塊，其中存放每像素位元數目、每列的像素數目和陣列的資料列數目等資訊。  此類檔案可能也會包含色彩表 \(又稱為色板\)。  色表會將點陣圖的數目對應為特定色彩。  下列圖示顯示一個放大的影像及其點陣圖和色表。  每個像素都是由 4 位元數字來表示，因此色表中共有 2^4 \= 16 個色彩。  表格中的每一個色彩都是用 24 位元數字來表示：8 位元用來表示紅色、8 位元用來表示綠色，還有 8 位元用來表示藍色。  這些數字是以十六進位 \(以 16 為基底\) 格式顯示：A \= 10、B \= 11、C \= 12、D \= 13、E \= 14、F \= 15。  
  
 ![點陣圖範例](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art01.png "AboutGdip03\_Art01")  
  
 請看影像的第 3 列及第 5 欄的像素。  點陣圖中對應的數字為 1。  我們可由色表得知 1 代表紅色，因此該像素為紅色。  點陣圖頂端列的所有項目都是 3。  我們可由色表得知 3 表示藍色，因此影像頂端列的所有像素都是藍色。  
  
> [!NOTE]
>  有些點陣圖是以由下到上的格式儲存；點陣圖首列的數目會對應到影像底端列的像素。  
  
 將索引儲存至色彩表的點陣圖稱為色板索引點陣圖。  有些點陣圖並不需要色表。  例如，如果點陣圖使用每像素 24 位元，則該點陣圖可儲存色彩本身，而非存入色表的索引。  下圖顯示直接儲存色彩的點陣圖 \(每像素 24 位元\)，而不是使用色表。  該圖同時顯示對應影像的放大檢視畫面。  在點陣圖中，FFFFFF 表示白色、FF0000 代表紅色、00FF00 為綠色，而 0000FF 則為藍色。  
  
 ![點陣圖範例](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art02.png "AboutGdip03\_Art02")  
  
## 圖形檔案格式  
 您可以使用許多標準格式將點陣圖儲存在磁片檔案中。  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 支援以下各節說明的圖形檔案格式。  
  
### BMP  
 BMP 是 Windows 用來儲存與裝置無關 \(Device\-Independent\) 和與應用程式無關的影像的標準格式。  指定 BMP 檔的每像素位元數 \(1、4、8、15、24、32 或 64\) 是由檔案標頭所決定。  常見的 BMP 檔為每像素 24 位元。  通常 BMP 檔不會被壓縮，因此並不適合透過網際網路傳輸。  
  
### Graphics Interchange Format \(GIF\)  
 GIF 是 Web 網頁上常見的影像格式。  GIF 適用於線條圖形、具有實色區塊的圖片和色彩之間具有明顯界線的圖片。  GIF 可被壓縮而且不會在壓縮過程中遺失任何資訊；解壓縮後的影像將和原始影像完全相同。  GIF 的色彩可指定為透明，這樣一來影像則可以顯示該影像的 Web 網頁做為背景色彩。  GIF 影像的序列 \(Sequence\) 可儲存在單一檔案中，做為動畫 GIF。  GIF 大部分都儲存為每像素 8 位元，這樣便可將它們限制在 256 色彩。  
  
### Joint Photographic Experts Group \(JPEG\)  
 JPEG 是一種壓縮結構，適用於自然景觀圖片，例如掃描的照片。  有些資訊可能會在壓縮過程中喪失，但肉眼並無法看出變化。  JPEG 可儲存每像素 24 位元，因此它們可以顯示超過 1 千 6 百萬個色彩。  JPEG 不支援透明效果或動畫。  
  
 您可以設定 JPEG 影像檔的壓縮層次，但壓縮層次越高 \(檔案越小\)，便會喪失較多資訊。  通常肉眼無法辨識以 20:1 的壓縮比率所產生的影像和原始檔案之間的差異。  下圖將顯示 BMP 影像和兩個從該 BMP 影像壓縮而來的 JPEG 影像。  第一個 JPEG 的壓縮比率為 4:1，第二個 JPEG 的壓縮比率約為 8:1。  
  
 ![檔案類型範例](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art03.gif "AboutGdip03\_Art03")  
  
 JPEG 壓縮不適用於線條圖形、實色區塊和明顯的界線。  下圖將顯示一個 BMP 和兩個 JPEG 及一個 GIF。  這兩個 JPEG 和 GIF 都是從 BMP 壓縮而來的。  GIF 的壓縮比率為 4:1、較小的 JPEG 為 4:1，較大的 JPEG 為 8:3。  請注意，GIF 中的線條旁仍然出現明顯界線，但 JPEG 中的界線似乎比較模糊。  
  
 ![檔案類型](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art03a.png "AboutGdip03\_Art03A")  
  
 JPEG 是一種壓縮結構，而非檔案格式。  JPEG 檔案交換格式 \(JFIF\) 是常用來儲存和傳送影像的檔案格式，它們是根據 JPEG 結構進行壓縮。  Web 瀏覽器顯示的 JFIF 檔案將使用 .jpg 副檔名。  
  
### Exchangeable Image File \(EXIF\)  
 EXIF 是用於數位相機所擷取的相片檔案格式。  EXIF 檔含有根據 JPEG 規格來壓縮的影像。  EXIF 檔同時含有照片資訊 \(拍攝日期、快門速度、曝光時間等資訊\) 和相機資訊 \(製造商、型號等資訊\)。  
  
### Portable Network Graphics \(PNG\)  
 PNG 格式保留了許多 GIF 格式的優點，同時提供比 GIF 更強大的功能。  PNG 檔和 GIF 檔同樣都不會在壓縮過程中喪失任何資訊。  PNG 檔可儲存每像素 8、24 或 48 位元的色彩，以及每像素 1、2、4、8 或 16 位元的灰階。  相較之下，GIF 檔只能使用每像素 1、2、4 或 8 位元。  PNG 檔也可儲存每個像素的 Alpha 值，指定該像素與背景色彩混用的程度。  
  
 PNG 改進了 GIF 漸進式顯示影像的功能；當 PNG 收到透過網路連線傳送的影像時，可以顯示較佳的影像效果。  PNG 檔可包含 Gamma 修正和色彩修正資訊，這樣一來可將影像正確地對應到各種不同的顯示裝置。  
  
### Tag Image File Format \(TIFF\)  
 TIFF 是一種具有彈性且可延伸的格式，各種平台和影像處理應用程式都支援這種格式。  TIFF 檔可儲存每像素任意位元數的影像，並可使用各種壓縮演算法。  單一、多頁的 TIFF 檔可儲存數個影像。  影像相關資訊 \(掃描器製作、主機電腦、壓縮類型、方向、每像素範例等等\) 可儲存在檔案中，並可使用標記進行排列。  TIFF 格式可依需要 \(如情況允許而且必須增加新的標記\) 進行延伸。  
  
## 請參閱  
 <xref:System.Drawing.Image?displayProperty=fullName>   
 <xref:System.Drawing.Bitmap?displayProperty=fullName>   
 <xref:System.Drawing.Imaging.PixelFormat?displayProperty=fullName>   
 [影像、點陣圖和中繼檔](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)   
 [使用影像、點陣圖、圖示和中繼檔](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
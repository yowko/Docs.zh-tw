---
title: 作法：設定 Windows Forms 控制項所顯示的影像
ms.date: 08/20/2019
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Button control [Windows Forms], images
- Windows Forms controls, images
- controls [Windows Forms], images
- images [Windows Forms], Windows Forms controls
- examples [Windows Forms], controls
ms.assetid: 9445af8f-4f62-48b0-a3f6-068058964b9f
ms.openlocfilehash: b1b1dbbb50c3b19cf8d8a7d7030d0bc168afb6a7
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666193"
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a>作法：設定 Windows Forms 控制項所顯示的影像

數個 Windows Forms 控制項可以顯示影像。 這些影像可以是用來闡明控制項用途的圖示, 例如代表儲存命令的按鈕上的磁片圖示。 或者, 圖示可以是背景影像, 為控制項提供您想要的外觀和行為。

## <a name="programmatic"></a>化

將控制項的`Image`或`BackgroundImage`屬性設定為類型<xref:System.Drawing.Image>的物件。 一般來說, 您會使用<xref:System.Drawing.Image.FromFile%2A>方法從檔案載入影像。

在下列程式碼範例中, 為影像位置設定的路徑是 [我的**圖片**] 資料夾。 大部分執行 Windows 作業系統的電腦都包含此目錄。 這也可讓具有最低系統存取層級的使用者安全地執行應用程式。 下列程式碼範例要求您已經有已加入<xref:System.Windows.Forms.PictureBox>控制項的表單。

```vb
' Replace the image named below with your own icon.
PictureBox1.Image = Image.FromFile _
   (System.Environment.GetFolderPath _
   (System.Environment.SpecialFolder.MyPictures) _
   & "\Image.gif")
```

```csharp
// Replace the image named below with your own icon.
// Note the escape character used (@) when specifying the path.
pictureBox1.Image = Image.FromFile
   (System.Environment.GetFolderPath
   (System.Environment.SpecialFolder.MyPictures)
   + @"\Image.gif");
```

```cpp
// Replace the image named below with your own icon.
pictureBox1->Image = Image::FromFile(String::Concat
   (System::Environment::GetFolderPath
   (System::Environment::SpecialFolder::MyPictures),
   "\\Image.gif"));
```

## <a name="designer"></a>Designer

1. 在 Visual Studio 的 [**屬性**] 視窗中, 選取控制項的 [**影像**] 或 [ **BackgroundImage** ] 屬性, 然後選取![省略號 (Visual Studio](./media/visual-studio-ellipsis-button.png)中的省略號按鈕) 以顯示 [**選取][資源**] 對話方塊。

2. 選取您想要顯示的影像。

## <a name="see-also"></a>另請參閱

- <xref:System.Drawing.Image.FromFile%2A>
- <xref:System.Drawing.Image>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>

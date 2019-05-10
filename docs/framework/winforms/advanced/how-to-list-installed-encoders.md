---
title: HOW TO：列出已安裝的編碼器
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image codecs [Windows Forms], listing
- image encoders [Windows Forms], listing
ms.assetid: 49e8e4e9-7a67-42d9-86bf-08821cdc282e
ms.openlocfilehash: 2634dd96b3aa5edcecde092919eb328b7f3dadc3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626835"
---
# <a name="how-to-list-installed-encoders"></a>HOW TO：列出已安裝的編碼器
若要列出可用的電腦上，影像編碼器，以判斷是否能省下您的應用程式特定的影像檔案格式。 <xref:System.Drawing.Imaging.ImageCodecInfo>類別提供<xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A>靜態方法，讓您可以判斷哪一個映像編碼器可用。 <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> 傳回的陣列<xref:System.Drawing.Imaging.ImageCodecInfo>物件。  
  
## <a name="example"></a>範例  
 下列程式碼範例會輸出已安裝的編碼器的清單和其屬性值。  
  
 [!code-csharp[UsingImageEncodersDecoders#1](~/samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#1)]
 [!code-vb[UsingImageEncodersDecoders#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- Windows Forms 應用程式。  
  
- A <xref:System.Windows.Forms.PaintEventArgs>，這是參數的<xref:System.Windows.Forms.PaintEventHandler>。  
  
## <a name="see-also"></a>另請參閱

- [如何：列出已安裝的解碼器](how-to-list-installed-decoders.md)
- [使用 Managed GDI+ 中的影像編碼器和解碼器](using-image-encoders-and-decoders-in-managed-gdi.md)

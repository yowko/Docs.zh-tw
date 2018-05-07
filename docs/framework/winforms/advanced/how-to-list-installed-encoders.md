---
title: 如何：列出已安裝的編碼器
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image codecs [Windows Forms], listing
- image encoders [Windows Forms], listing
ms.assetid: 49e8e4e9-7a67-42d9-86bf-08821cdc282e
ms.openlocfilehash: 1882ce9a140fb325c29411173ba7bde717bd3f98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-list-installed-encoders"></a>如何：列出已安裝的編碼器
若要列出影像轉碼器的電腦上，可用來判斷您的應用程式是否可以將儲存至特定的影像檔案格式。 <xref:System.Drawing.Imaging.ImageCodecInfo>類別提供<xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A>靜態方法，如此您就可以判斷哪一個映像編碼器可用。 <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> 傳回的陣列<xref:System.Drawing.Imaging.ImageCodecInfo>物件。  
  
## <a name="example"></a>範例  
 下列程式碼範例會輸出之已安裝的編碼器清單和其屬性值。  
  
 [!code-csharp[UsingImageEncodersDecoders#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#1)]
 [!code-vb[UsingImageEncodersDecoders#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   Windows Forms 應用程式。  
  
-   A <xref:System.Windows.Forms.PaintEventArgs>，這是參數的<xref:System.Windows.Forms.PaintEventHandler>。  
  
## <a name="see-also"></a>另請參閱  
 [操作說明：列出已安裝的解碼器](../../../../docs/framework/winforms/advanced/how-to-list-installed-decoders.md)  
 [使用 Managed GDI+ 中的影像編碼器和解碼器](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)

---
title: 如何：判斷編碼器所支援的參數
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encoder parameters [Windows Forms], determining supported
ms.assetid: f47ae459-e3ce-4d41-a140-2f6c6aea3f44
ms.openlocfilehash: 7f7c270c4ae590c070103d51f116158869b678c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-determine-the-parameters-supported-by-an-encoder"></a>如何：判斷編碼器所支援的參數
您可以調整影像的參數，例如品質和壓縮層級，但您必須知道所指定之影像編碼器支援的參數。 <xref:System.Drawing.Image>類別提供<xref:System.Drawing.Image.GetEncoderParameterList%2A>方法，以便決定映像所支援的參數為特定的編碼器。 您可以指定編碼器使用的 GUID。 <xref:System.Drawing.Image.GetEncoderParameterList%2A>方法傳回的陣列<xref:System.Drawing.Imaging.EncoderParameter>物件。  
  
## <a name="example"></a>範例  
 下列範例程式碼輸出 JPEG 編碼器支援的參數。 使用參數類別目錄清單中相關聯的 Guid<xref:System.Drawing.Imaging.Encoder>類別概觀來決定每個參數類別。  
  
 [!code-csharp[UsingImageEncodersDecoders#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#3)]
 [!code-vb[UsingImageEncodersDecoders#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   Windows Forms 應用程式。  
  
-   A <xref:System.Windows.Forms.PaintEventArgs>，這是參數的<xref:System.Windows.Forms.PaintEventHandler>。  
  
## <a name="see-also"></a>另請參閱  
 [操作說明：列出已安裝的編碼器](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 [點陣圖類型](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)  
 [使用 Managed GDI+ 中的影像編碼器和解碼器](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)

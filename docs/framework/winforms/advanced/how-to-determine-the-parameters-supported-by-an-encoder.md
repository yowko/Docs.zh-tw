---
title: HOW TO：判斷編碼器所支援的參數
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encoder parameters [Windows Forms], determining supported
ms.assetid: f47ae459-e3ce-4d41-a140-2f6c6aea3f44
ms.openlocfilehash: 56b78a0cdfcb9ac8e3a7dbc12527fcc59f0524fd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54723403"
---
# <a name="how-to-determine-the-parameters-supported-by-an-encoder"></a>HOW TO：判斷編碼器所支援的參數
您可以調整影像的參數，例如品質和壓縮層級，但您必須知道所指定之影像編碼器所支援的參數。 <xref:System.Drawing.Image>類別提供<xref:System.Drawing.Image.GetEncoderParameterList%2A>方法，如此您就可以判斷特定編碼器支援哪些映像參數。 您可以指定編碼器使用的 GUID。 <xref:System.Drawing.Image.GetEncoderParameterList%2A>方法傳回的陣列<xref:System.Drawing.Imaging.EncoderParameter>物件。  
  
## <a name="example"></a>範例  
 下列範例程式碼輸出 JPEG 編碼器支援的參數。 使用的參數類別和關聯的 Guid，在清單<xref:System.Drawing.Imaging.Encoder>類別概觀，判斷每個參數的分類。  
  
 [!code-csharp[UsingImageEncodersDecoders#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#3)]
 [!code-vb[UsingImageEncodersDecoders#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   Windows Forms 應用程式。  
  
-   A <xref:System.Windows.Forms.PaintEventArgs>，這是參數的<xref:System.Windows.Forms.PaintEventHandler>。  
  
## <a name="see-also"></a>另請參閱
- [如何：列出已安裝的編碼器](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)
- [點陣圖類型](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)
- [使用 Managed GDI+ 中的影像編碼器和解碼器](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)

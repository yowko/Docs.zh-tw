---
title: 如何：列印 Windows Form
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- printing a form
- printing [Windows Forms], printing a form
ms.assetid: c8dff5f8-f56a-4c07-ae31-64643b31f8fc
ms.openlocfilehash: 42940654a0754ac3616ca7983af07d20607f480f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-print-a-windows-form"></a>如何：列印 Windows Form
在開發程序的一部分，您通常會想要列印一份您的 Windows Form。 下列程式碼範例示範如何使用列印一份目前的表單<xref:System.Drawing.Graphics.CopyFromScreen%2A>方法。  
  
## <a name="example"></a>範例  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這是完整的程式碼範例，其中包含`Main`方法。  
  
## <a name="robust-programming"></a>穩固程式設計  
 以下條件可能會造成例外狀況：  
  
-   您沒有存取印表機的權限。  
  
-   沒有安裝印表機。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 若要執行這個程式碼範例，您必須存取您使用您的電腦與印表機的權限。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Drawing.Printing.PrintDocument>  
 [操作說明：使用 GDI+ 呈現影像](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)  
 [如何：列印 Windows Forms 中的圖形](../../../../docs/framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)

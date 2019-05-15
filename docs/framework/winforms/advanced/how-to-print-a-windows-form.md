---
title: 作法：列印 Windows Form
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
ms.openlocfilehash: cd10e0a43ff37b921dc8e024d7a6a51fafbb0400
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591848"
---
# <a name="how-to-print-a-windows-form"></a>作法：列印 Windows Form
在開發程序的一部分，您通常會想要列印一份 Windows 表單。 下列程式碼範例示範如何使用列印一份目前的表單<xref:System.Drawing.Graphics.CopyFromScreen%2A>方法。  
  
## <a name="example"></a>範例  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 以下條件可能會造成例外狀況：  
  
- 您沒有存取印表機的權限。  
  
- 不沒有安裝任何印表機。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 若要執行此程式碼範例，您必須存取您使用您的電腦與印表機的權限。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Drawing.Printing.PrintDocument>
- [如何：使用 GDI + 呈現影像](how-to-render-images-with-gdi.md)
- [如何：列印 Windows Form 中的圖形](how-to-print-graphics-in-windows-forms.md)

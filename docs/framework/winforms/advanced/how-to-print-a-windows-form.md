---
title: 如何：列印 Windows Form
description: 瞭解如何使用 CopyFromScreen 方法，以程式設計方式列印目前 Windows Form 的複本。
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
ms.openlocfilehash: b59ea4b5347903b36a166c4f8ac0d8d7db18635e
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174688"
---
# <a name="how-to-print-a-windows-form"></a>如何：列印 Windows Form
在開發過程中，您通常會想要列印 Windows Form 的複本。 下列程式碼範例示範如何使用方法來列印目前表單的複本 <xref:System.Drawing.Graphics.CopyFromScreen%2A> 。  
  
## <a name="example"></a>範例  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 以下條件可能會造成例外狀況：  
  
- 您沒有存取印表機的許可權。  
  
- 未安裝印表機。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 若要執行這個程式碼範例，您必須擁有存取電腦所用印表機的許可權。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Drawing.Printing.PrintDocument>
- [如何：使用 GDI+ 呈現影像](how-to-render-images-with-gdi.md)
- [如何：列印 Windows Forms 中的圖形](how-to-print-graphics-in-windows-forms.md)

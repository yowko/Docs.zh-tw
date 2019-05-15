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
# <a name="how-to-print-a-windows-form"></a><span data-ttu-id="68fc9-102">作法：列印 Windows Form</span><span class="sxs-lookup"><span data-stu-id="68fc9-102">How to: Print a Windows Form</span></span>
<span data-ttu-id="68fc9-103">在開發程序的一部分，您通常會想要列印一份 Windows 表單。</span><span class="sxs-lookup"><span data-stu-id="68fc9-103">As part of the development process, you typically will want to print a copy of your Windows Form.</span></span> <span data-ttu-id="68fc9-104">下列程式碼範例示範如何使用列印一份目前的表單<xref:System.Drawing.Graphics.CopyFromScreen%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="68fc9-104">The following code example shows how to print a copy of the current form by using the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68fc9-105">範例</span><span class="sxs-lookup"><span data-stu-id="68fc9-105">Example</span></span>  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="68fc9-106">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="68fc9-106">Robust Programming</span></span>  
 <span data-ttu-id="68fc9-107">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="68fc9-107">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="68fc9-108">您沒有存取印表機的權限。</span><span class="sxs-lookup"><span data-stu-id="68fc9-108">You do not have permission to access the printer.</span></span>  
  
- <span data-ttu-id="68fc9-109">不沒有安裝任何印表機。</span><span class="sxs-lookup"><span data-stu-id="68fc9-109">There is no printer installed.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="68fc9-110">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="68fc9-110">.NET Framework Security</span></span>  
 <span data-ttu-id="68fc9-111">若要執行此程式碼範例，您必須存取您使用您的電腦與印表機的權限。</span><span class="sxs-lookup"><span data-stu-id="68fc9-111">In order to run this code example, you must have permission to access the printer you use with your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68fc9-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68fc9-112">See also</span></span>

- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="68fc9-113">如何：使用 GDI + 呈現影像</span><span class="sxs-lookup"><span data-stu-id="68fc9-113">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)
- [<span data-ttu-id="68fc9-114">如何：列印 Windows Form 中的圖形</span><span class="sxs-lookup"><span data-stu-id="68fc9-114">How to: Print Graphics in Windows Forms</span></span>](how-to-print-graphics-in-windows-forms.md)

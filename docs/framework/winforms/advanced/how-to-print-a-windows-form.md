---
title: HOW TO：列印 Windows Form
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
ms.openlocfilehash: 85fb12028687578b76e0f16061deb9b9a4de70e3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59121962"
---
# <a name="how-to-print-a-windows-form"></a><span data-ttu-id="3558f-102">HOW TO：列印 Windows Form</span><span class="sxs-lookup"><span data-stu-id="3558f-102">How to: Print a Windows Form</span></span>
<span data-ttu-id="3558f-103">在開發程序的一部分，您通常會想要列印一份 Windows 表單。</span><span class="sxs-lookup"><span data-stu-id="3558f-103">As part of the development process, you typically will want to print a copy of your Windows Form.</span></span> <span data-ttu-id="3558f-104">下列程式碼範例示範如何使用列印一份目前的表單<xref:System.Drawing.Graphics.CopyFromScreen%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="3558f-104">The following code example shows how to print a copy of the current form by using the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3558f-105">範例</span><span class="sxs-lookup"><span data-stu-id="3558f-105">Example</span></span>  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3558f-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="3558f-106">Compiling the Code</span></span>  
 <span data-ttu-id="3558f-107">這是完整的程式碼範例，其中包含`Main`方法。</span><span class="sxs-lookup"><span data-stu-id="3558f-107">This is a complete code example that contains a `Main` method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="3558f-108">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="3558f-108">Robust Programming</span></span>  
 <span data-ttu-id="3558f-109">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="3558f-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="3558f-110">您沒有存取印表機的權限。</span><span class="sxs-lookup"><span data-stu-id="3558f-110">You do not have permission to access the printer.</span></span>  
  
-   <span data-ttu-id="3558f-111">不沒有安裝任何印表機。</span><span class="sxs-lookup"><span data-stu-id="3558f-111">There is no printer installed.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="3558f-112">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="3558f-112">.NET Framework Security</span></span>  
 <span data-ttu-id="3558f-113">若要執行此程式碼範例，您必須存取您使用您的電腦與印表機的權限。</span><span class="sxs-lookup"><span data-stu-id="3558f-113">In order to run this code example, you must have permission to access the printer you use with your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3558f-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3558f-114">See also</span></span>

- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="3558f-115">如何：使用 GDI + 呈現影像</span><span class="sxs-lookup"><span data-stu-id="3558f-115">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)
- [<span data-ttu-id="3558f-116">如何：列印 Windows Form 中的圖形</span><span class="sxs-lookup"><span data-stu-id="3558f-116">How to: Print Graphics in Windows Forms</span></span>](how-to-print-graphics-in-windows-forms.md)

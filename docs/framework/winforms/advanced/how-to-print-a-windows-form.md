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
# <a name="how-to-print-a-windows-form"></a><span data-ttu-id="ef003-103">如何：列印 Windows Form</span><span class="sxs-lookup"><span data-stu-id="ef003-103">How to: Print a Windows Form</span></span>
<span data-ttu-id="ef003-104">在開發過程中，您通常會想要列印 Windows Form 的複本。</span><span class="sxs-lookup"><span data-stu-id="ef003-104">As part of the development process, you typically will want to print a copy of your Windows Form.</span></span> <span data-ttu-id="ef003-105">下列程式碼範例示範如何使用方法來列印目前表單的複本 <xref:System.Drawing.Graphics.CopyFromScreen%2A> 。</span><span class="sxs-lookup"><span data-stu-id="ef003-105">The following code example shows how to print a copy of the current form by using the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef003-106">範例</span><span class="sxs-lookup"><span data-stu-id="ef003-106">Example</span></span>  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="ef003-107">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="ef003-107">Robust Programming</span></span>  
 <span data-ttu-id="ef003-108">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="ef003-108">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="ef003-109">您沒有存取印表機的許可權。</span><span class="sxs-lookup"><span data-stu-id="ef003-109">You do not have permission to access the printer.</span></span>  
  
- <span data-ttu-id="ef003-110">未安裝印表機。</span><span class="sxs-lookup"><span data-stu-id="ef003-110">There is no printer installed.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="ef003-111">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="ef003-111">.NET Framework Security</span></span>  
 <span data-ttu-id="ef003-112">若要執行這個程式碼範例，您必須擁有存取電腦所用印表機的許可權。</span><span class="sxs-lookup"><span data-stu-id="ef003-112">In order to run this code example, you must have permission to access the printer you use with your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef003-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef003-113">See also</span></span>

- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="ef003-114">如何：使用 GDI+ 呈現影像</span><span class="sxs-lookup"><span data-stu-id="ef003-114">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)
- [<span data-ttu-id="ef003-115">如何：列印 Windows Forms 中的圖形</span><span class="sxs-lookup"><span data-stu-id="ef003-115">How to: Print Graphics in Windows Forms</span></span>](how-to-print-graphics-in-windows-forms.md)

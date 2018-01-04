---
title: "如何：列印 Windows Form"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- printing a form
- printing [Windows Forms], printing a form
ms.assetid: c8dff5f8-f56a-4c07-ae31-64643b31f8fc
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8c50b1f47d207334160ed12674ee8efb1390fb84
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-print-a-windows-form"></a><span data-ttu-id="ee1a0-102">如何：列印 Windows Form</span><span class="sxs-lookup"><span data-stu-id="ee1a0-102">How to: Print a Windows Form</span></span>
<span data-ttu-id="ee1a0-103">在開發程序的一部分，您通常會想要列印一份您的 Windows Form。</span><span class="sxs-lookup"><span data-stu-id="ee1a0-103">As part of the development process, you typically will want to print a copy of your Windows Form.</span></span> <span data-ttu-id="ee1a0-104">下列程式碼範例示範如何使用列印一份目前的表單<xref:System.Drawing.Graphics.CopyFromScreen%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="ee1a0-104">The following code example shows how to print a copy of the current form by using the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee1a0-105">範例</span><span class="sxs-lookup"><span data-stu-id="ee1a0-105">Example</span></span>  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ee1a0-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="ee1a0-106">Compiling the Code</span></span>  
 <span data-ttu-id="ee1a0-107">這是完整的程式碼範例，其中包含`Main`方法。</span><span class="sxs-lookup"><span data-stu-id="ee1a0-107">This is a complete code example that contains a `Main` method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="ee1a0-108">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="ee1a0-108">Robust Programming</span></span>  
 <span data-ttu-id="ee1a0-109">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="ee1a0-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="ee1a0-110">您沒有存取印表機的權限。</span><span class="sxs-lookup"><span data-stu-id="ee1a0-110">You do not have permission to access the printer.</span></span>  
  
-   <span data-ttu-id="ee1a0-111">沒有安裝印表機。</span><span class="sxs-lookup"><span data-stu-id="ee1a0-111">There is no printer installed.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="ee1a0-112">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="ee1a0-112">.NET Framework Security</span></span>  
 <span data-ttu-id="ee1a0-113">若要執行這個程式碼範例，您必須存取您使用您的電腦與印表機的權限。</span><span class="sxs-lookup"><span data-stu-id="ee1a0-113">In order to run this code example, you must have permission to access the printer you use with your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee1a0-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="ee1a0-114">See Also</span></span>  
 <xref:System.Drawing.Printing.PrintDocument>  
 [<span data-ttu-id="ee1a0-115">操作說明：使用 GDI+ 呈現影像</span><span class="sxs-lookup"><span data-stu-id="ee1a0-115">How to: Render Images with GDI+</span></span>](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)  
 [<span data-ttu-id="ee1a0-116">如何：列印 Windows Forms 中的圖形</span><span class="sxs-lookup"><span data-stu-id="ee1a0-116">How to: Print Graphics in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)

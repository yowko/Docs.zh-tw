---
title: "如何：建立垂直文字"
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
- text [Windows Forms], drawing vertical
- Windows Forms, drawing vertical text
- strings [Windows Forms], drawing vertical
- vertical text [Windows Forms], drawing
ms.assetid: 50c69046-4188-47d9-b949-cc2610ffd337
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8615a90094232381f2c8d51f5593276d0c01f892
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-vertical-text"></a><span data-ttu-id="ec650-102">如何：建立垂直文字</span><span class="sxs-lookup"><span data-stu-id="ec650-102">How to: Create Vertical Text</span></span>
<span data-ttu-id="ec650-103">您可以使用<xref:System.Drawing.StringFormat>物件，以指定垂直而非水平繪製文字。</span><span class="sxs-lookup"><span data-stu-id="ec650-103">You can use a <xref:System.Drawing.StringFormat> object to specify that text be drawn vertically rather than horizontally.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec650-104">範例</span><span class="sxs-lookup"><span data-stu-id="ec650-104">Example</span></span>  
 <span data-ttu-id="ec650-105">下列範例會將值指派<xref:System.Drawing.StringFormatFlags.DirectionVertical>至<xref:System.Drawing.StringFormat.FormatFlags%2A>屬性<xref:System.Drawing.StringFormat>物件。</span><span class="sxs-lookup"><span data-stu-id="ec650-105">The following example assigns the value <xref:System.Drawing.StringFormatFlags.DirectionVertical> to the <xref:System.Drawing.StringFormat.FormatFlags%2A> property of a <xref:System.Drawing.StringFormat> object.</span></span> <span data-ttu-id="ec650-106">確認<xref:System.Drawing.StringFormat>物件傳遞至<xref:System.Drawing.Graphics.DrawString%2A>方法<xref:System.Drawing.Graphics>類別。</span><span class="sxs-lookup"><span data-stu-id="ec650-106">That <xref:System.Drawing.StringFormat> object is passed to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="ec650-107">值<xref:System.Drawing.StringFormatFlags.DirectionVertical>隸屬<xref:System.Drawing.StringFormatFlags>列舉型別。</span><span class="sxs-lookup"><span data-stu-id="ec650-107">The value <xref:System.Drawing.StringFormatFlags.DirectionVertical> is a member of the <xref:System.Drawing.StringFormatFlags> enumeration.</span></span>  
  
 <span data-ttu-id="ec650-108">下圖顯示垂直文字。</span><span class="sxs-lookup"><span data-stu-id="ec650-108">The following illustration shows the vertical text.</span></span>  
  
 <span data-ttu-id="ec650-109">![字型文字](../../../../docs/framework/winforms/advanced/media/csfontstext5.png "csfontstext5")</span><span class="sxs-lookup"><span data-stu-id="ec650-109">![Fonts Text](../../../../docs/framework/winforms/advanced/media/csfontstext5.png "csfontstext5")</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.FontsAndText#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ec650-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="ec650-110">Compiling the Code</span></span>  
  
-   <span data-ttu-id="ec650-111">上述範例設計用於搭配 Windows Form，且其需要<xref:System.Windows.Forms.PaintEventArgs> `e` ，這是參數的<xref:System.Windows.Forms.PaintEventHandler>。</span><span class="sxs-lookup"><span data-stu-id="ec650-111">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e` , which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec650-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="ec650-112">See Also</span></span>  
 [<span data-ttu-id="ec650-113">操作說明：使用 GDI 繪製文字</span><span class="sxs-lookup"><span data-stu-id="ec650-113">How to: Draw Text with GDI</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)

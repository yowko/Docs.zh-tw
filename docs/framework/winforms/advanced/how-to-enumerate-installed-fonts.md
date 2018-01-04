---
title: "如何：列舉已安裝的字型"
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
- fonts [Windows Forms], enumerating installed
- examples [Windows Forms], fonts
ms.assetid: 26d74ef5-0f39-4eeb-8d20-00e66e014abe
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 905b5ecbda58d2f7edb7fc30d5505eec63a64c2b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enumerate-installed-fonts"></a><span data-ttu-id="4fcb1-102">如何：列舉已安裝的字型</span><span class="sxs-lookup"><span data-stu-id="4fcb1-102">How to: Enumerate Installed Fonts</span></span>
<span data-ttu-id="4fcb1-103"><xref:System.Drawing.Text.InstalledFontCollection>類別繼承自<xref:System.Drawing.Text.FontCollection>抽象基底類別。</span><span class="sxs-lookup"><span data-stu-id="4fcb1-103">The <xref:System.Drawing.Text.InstalledFontCollection> class inherits from the <xref:System.Drawing.Text.FontCollection> abstract base class.</span></span> <span data-ttu-id="4fcb1-104">您可以使用<xref:System.Drawing.Text.InstalledFontCollection>物件來列舉電腦上安裝的字型。</span><span class="sxs-lookup"><span data-stu-id="4fcb1-104">You can use an <xref:System.Drawing.Text.InstalledFontCollection> object to enumerate the fonts installed on the computer.</span></span> <span data-ttu-id="4fcb1-105"><xref:System.Drawing.Text.FontCollection.Families%2A>屬性<xref:System.Drawing.Text.InstalledFontCollection>物件是陣列<xref:System.Drawing.FontFamily>物件。</span><span class="sxs-lookup"><span data-stu-id="4fcb1-105">The <xref:System.Drawing.Text.FontCollection.Families%2A> property of an <xref:System.Drawing.Text.InstalledFontCollection> object is an array of <xref:System.Drawing.FontFamily> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4fcb1-106">範例</span><span class="sxs-lookup"><span data-stu-id="4fcb1-106">Example</span></span>  
 <span data-ttu-id="4fcb1-107">下列範例會列出電腦上安裝的所有字型家族的名稱。</span><span class="sxs-lookup"><span data-stu-id="4fcb1-107">The following example lists the names of all the font families installed on the computer.</span></span> <span data-ttu-id="4fcb1-108">程式碼會擷取<xref:System.Drawing.FontFamily.Name%2A>每個屬性<xref:System.Drawing.FontFamily>所傳回陣列中的物件<xref:System.Drawing.Text.FontCollection.Families%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="4fcb1-108">The code retrieves the <xref:System.Drawing.FontFamily.Name%2A> property of each <xref:System.Drawing.FontFamily> object in the array returned by the <xref:System.Drawing.Text.FontCollection.Families%2A> property.</span></span> <span data-ttu-id="4fcb1-109">擷取系列名稱，如串連這些區塊是以逗號分隔的格式清單。</span><span class="sxs-lookup"><span data-stu-id="4fcb1-109">As the family names are retrieved, they are concatenated to form a comma-separated list.</span></span> <span data-ttu-id="4fcb1-110">然後在<xref:System.Drawing.Graphics.DrawString%2A>方法<xref:System.Drawing.Graphics>類別在矩形中繪製的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="4fcb1-110">Then the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> class draws the comma-separated list in a rectangle.</span></span>  
  
 <span data-ttu-id="4fcb1-111">如果您執行範例程式碼時，輸出會類似於下圖所示。</span><span class="sxs-lookup"><span data-stu-id="4fcb1-111">If you run the example code, the output will be similar to that shown in the following illustration.</span></span>  
  
 <span data-ttu-id="4fcb1-112">![安裝字型](../../../../docs/framework/winforms/advanced/media/csfontstext6.png "csfontstext6")</span><span class="sxs-lookup"><span data-stu-id="4fcb1-112">![Installed Fonts](../../../../docs/framework/winforms/advanced/media/csfontstext6.png "csfontstext6")</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.FontsAndText#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4fcb1-113">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="4fcb1-113">Compiling the Code</span></span>  
 <span data-ttu-id="4fcb1-114">上述範例設計是為搭配 Windows Form 使用所設計，而且需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.PaintEventHandler> 的參數。</span><span class="sxs-lookup"><span data-stu-id="4fcb1-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span> <span data-ttu-id="4fcb1-115">此外，您應該匯入<xref:System.Drawing.Text>命名空間。</span><span class="sxs-lookup"><span data-stu-id="4fcb1-115">In addition, you should import the <xref:System.Drawing.Text> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fcb1-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="4fcb1-116">See Also</span></span>  
 [<span data-ttu-id="4fcb1-117">使用字型和文字</span><span class="sxs-lookup"><span data-stu-id="4fcb1-117">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)

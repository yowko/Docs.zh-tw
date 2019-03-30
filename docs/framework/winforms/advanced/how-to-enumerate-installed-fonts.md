---
title: HOW TO：列舉已安裝的字型
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [Windows Forms], enumerating installed
- examples [Windows Forms], fonts
ms.assetid: 26d74ef5-0f39-4eeb-8d20-00e66e014abe
ms.openlocfilehash: e56f06d6f7a762a1ef1ff85fa30751ea64f9f14b
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2019
ms.locfileid: "58653739"
---
# <a name="how-to-enumerate-installed-fonts"></a><span data-ttu-id="f95f4-102">HOW TO：列舉已安裝的字型</span><span class="sxs-lookup"><span data-stu-id="f95f4-102">How to: Enumerate Installed Fonts</span></span>
<span data-ttu-id="f95f4-103"><xref:System.Drawing.Text.InstalledFontCollection>類別繼承自<xref:System.Drawing.Text.FontCollection>抽象基底類別。</span><span class="sxs-lookup"><span data-stu-id="f95f4-103">The <xref:System.Drawing.Text.InstalledFontCollection> class inherits from the <xref:System.Drawing.Text.FontCollection> abstract base class.</span></span> <span data-ttu-id="f95f4-104">您可以使用<xref:System.Drawing.Text.InstalledFontCollection>物件來列舉電腦上安裝的字型。</span><span class="sxs-lookup"><span data-stu-id="f95f4-104">You can use an <xref:System.Drawing.Text.InstalledFontCollection> object to enumerate the fonts installed on the computer.</span></span> <span data-ttu-id="f95f4-105"><xref:System.Drawing.Text.FontCollection.Families%2A>的屬性<xref:System.Drawing.Text.InstalledFontCollection>物件為陣列的<xref:System.Drawing.FontFamily>物件。</span><span class="sxs-lookup"><span data-stu-id="f95f4-105">The <xref:System.Drawing.Text.FontCollection.Families%2A> property of an <xref:System.Drawing.Text.InstalledFontCollection> object is an array of <xref:System.Drawing.FontFamily> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f95f4-106">範例</span><span class="sxs-lookup"><span data-stu-id="f95f4-106">Example</span></span>  
 <span data-ttu-id="f95f4-107">下列範例會列出安裝在電腦上的所有字型家族的名稱。</span><span class="sxs-lookup"><span data-stu-id="f95f4-107">The following example lists the names of all the font families installed on the computer.</span></span> <span data-ttu-id="f95f4-108">程式碼會擷取<xref:System.Drawing.FontFamily.Name%2A>屬性的每個<xref:System.Drawing.FontFamily>中所傳回的陣列物件<xref:System.Drawing.Text.FontCollection.Families%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="f95f4-108">The code retrieves the <xref:System.Drawing.FontFamily.Name%2A> property of each <xref:System.Drawing.FontFamily> object in the array returned by the <xref:System.Drawing.Text.FontCollection.Families%2A> property.</span></span> <span data-ttu-id="f95f4-109">系列名稱是擷取，串連這些區塊是以逗號分隔的格式清單。</span><span class="sxs-lookup"><span data-stu-id="f95f4-109">As the family names are retrieved, they are concatenated to form a comma-separated list.</span></span> <span data-ttu-id="f95f4-110">然後<xref:System.Drawing.Graphics.DrawString%2A>方法的<xref:System.Drawing.Graphics>類別在矩形中繪製的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="f95f4-110">Then the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> class draws the comma-separated list in a rectangle.</span></span>  
  
 <span data-ttu-id="f95f4-111">如果您執行範例程式碼時，輸出會類似下圖所示：</span><span class="sxs-lookup"><span data-stu-id="f95f4-111">If you run the example code, the output will be similar to that shown in the following illustration:</span></span>  
  
 ![如果螢幕擷取畫面會顯示已安裝的字型系列。](./media/how-to-enumerate-installed-fonts/list-installed-font-families.png)  
  
 [!code-csharp[System.Drawing.FontsAndText#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.FontsAndText#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f95f4-113">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="f95f4-113">Compiling the Code</span></span>  
 <span data-ttu-id="f95f4-114">上述範例中專為搭配 Windows Form 使用，而且需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.PaintEventHandler>。</span><span class="sxs-lookup"><span data-stu-id="f95f4-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span> <span data-ttu-id="f95f4-115">此外，您應該匯入<xref:System.Drawing.Text>命名空間。</span><span class="sxs-lookup"><span data-stu-id="f95f4-115">In addition, you should import the <xref:System.Drawing.Text> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f95f4-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f95f4-116">See also</span></span>
- [<span data-ttu-id="f95f4-117">使用字型和文字</span><span class="sxs-lookup"><span data-stu-id="f95f4-117">Using Fonts and Text</span></span>](using-fonts-and-text.md)

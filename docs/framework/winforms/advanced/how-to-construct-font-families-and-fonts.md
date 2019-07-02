---
title: HOW TO：建構字型家族和字型
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- font families [Windows Forms], constructing
- fonts [Windows Forms], constructing
ms.assetid: d3a4a223-9492-4b54-9afd-db1c31c3cefd
ms.openlocfilehash: 2d609525858c7a8ff77c0b86900b4fc7d6b4e39a
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505953"
---
# <a name="how-to-construct-font-families-and-fonts"></a><span data-ttu-id="a9187-102">作法：建構字型家族和字型</span><span class="sxs-lookup"><span data-stu-id="a9187-102">How to: Construct Font Families and Fonts</span></span>
<span data-ttu-id="a9187-103">GDI + 劃分為具有相同的字樣，但不同的字型的字型系列。</span><span class="sxs-lookup"><span data-stu-id="a9187-103">GDI+ groups fonts with the same typeface but different styles into font families.</span></span> <span data-ttu-id="a9187-104">比方說，新細明體字型系列包含下列字型：</span><span class="sxs-lookup"><span data-stu-id="a9187-104">For example, the Arial font family contains the following fonts:</span></span>  
  
- <span data-ttu-id="a9187-105">新細明體的一般</span><span class="sxs-lookup"><span data-stu-id="a9187-105">Arial Regular</span></span>  
  
- <span data-ttu-id="a9187-106">新細明體粗體</span><span class="sxs-lookup"><span data-stu-id="a9187-106">Arial Bold</span></span>  
  
- <span data-ttu-id="a9187-107">新細明體斜體</span><span class="sxs-lookup"><span data-stu-id="a9187-107">Arial Italic</span></span>  
  
- <span data-ttu-id="a9187-108">新細明體</span><span class="sxs-lookup"><span data-stu-id="a9187-108">Arial Bold Italic</span></span>  
  
 <span data-ttu-id="a9187-109">GDI + 會使用表單系列的四個樣式： 一般、 粗體、 斜體和粗體斜體。</span><span class="sxs-lookup"><span data-stu-id="a9187-109">GDI+ uses four styles to form families: regular, bold, italic, and bold italic.</span></span> <span data-ttu-id="a9187-110">這類的形容詞*縮小*並*捨入*不會被視為樣式; 而是它們屬於的系列名稱。</span><span class="sxs-lookup"><span data-stu-id="a9187-110">Adjectives such as *narrow* and *rounded* are not considered styles; rather they are part of the family name.</span></span> <span data-ttu-id="a9187-111">比方說，新細明體窄時，為字型家族，具有下列成員：</span><span class="sxs-lookup"><span data-stu-id="a9187-111">For example, Arial Narrow is a font family with the following members:</span></span>  
  
- <span data-ttu-id="a9187-112">新細明體窄一般</span><span class="sxs-lookup"><span data-stu-id="a9187-112">Arial Narrow Regular</span></span>  
  
- <span data-ttu-id="a9187-113">粗體的新細明體</span><span class="sxs-lookup"><span data-stu-id="a9187-113">Arial Narrow Bold</span></span>  
  
- <span data-ttu-id="a9187-114">新細明體窄斜體</span><span class="sxs-lookup"><span data-stu-id="a9187-114">Arial Narrow Italic</span></span>  
  
- <span data-ttu-id="a9187-115">窄的新細明體</span><span class="sxs-lookup"><span data-stu-id="a9187-115">Arial Narrow Bold Italic</span></span>  
  
 <span data-ttu-id="a9187-116">您可以繪製使用 GDI + 的文字之前，您必須建構<xref:System.Drawing.FontFamily>物件和<xref:System.Drawing.Font>物件。</span><span class="sxs-lookup"><span data-stu-id="a9187-116">Before you can draw text with GDI+, you need to construct a <xref:System.Drawing.FontFamily> object and a <xref:System.Drawing.Font> object.</span></span> <span data-ttu-id="a9187-117"><xref:System.Drawing.FontFamily>物件會指定 （例如，新細明體），字樣和<xref:System.Drawing.Font>物件指定大小、 樣式和單位。</span><span class="sxs-lookup"><span data-stu-id="a9187-117">The <xref:System.Drawing.FontFamily> object specifies the typeface (for example, Arial), and the <xref:System.Drawing.Font> object specifies the size, style, and units.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9187-118">範例</span><span class="sxs-lookup"><span data-stu-id="a9187-118">Example</span></span>  
 <span data-ttu-id="a9187-119">下列範例會建構規則的樣式新細明體字型的大小為 16 個像素。</span><span class="sxs-lookup"><span data-stu-id="a9187-119">The following example constructs a regular style Arial font with a size of 16 pixels.</span></span> <span data-ttu-id="a9187-120">在下列程式碼中，第一個引數傳遞給<xref:System.Drawing.Font.%23ctor%2A>建構函式是<xref:System.Drawing.FontFamily>物件。</span><span class="sxs-lookup"><span data-stu-id="a9187-120">In the following code, the first argument passed to the <xref:System.Drawing.Font.%23ctor%2A> constructor is the <xref:System.Drawing.FontFamily> object.</span></span> <span data-ttu-id="a9187-121">第二個引數會指定在第四個引數所識別的單位中測量的字型的大小。</span><span class="sxs-lookup"><span data-stu-id="a9187-121">The second argument specifies the size of the font measured in units identified by the fourth argument.</span></span> <span data-ttu-id="a9187-122">第三個引數識別的樣式。</span><span class="sxs-lookup"><span data-stu-id="a9187-122">The third argument identifies the style.</span></span>  
  
 <span data-ttu-id="a9187-123"><xref:System.Drawing.GraphicsUnit.Pixel> 隸屬<xref:System.Drawing.GraphicsUnit>列舉型別，並<xref:System.Drawing.FontStyle.Regular>隸屬<xref:System.Drawing.FontStyle>列舉型別。</span><span class="sxs-lookup"><span data-stu-id="a9187-123"><xref:System.Drawing.GraphicsUnit.Pixel> is a member of the <xref:System.Drawing.GraphicsUnit> enumeration, and <xref:System.Drawing.FontStyle.Regular> is a member of the <xref:System.Drawing.FontStyle> enumeration.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.FontsAndText#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a9187-124">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="a9187-124">Compiling the Code</span></span>  
 <span data-ttu-id="a9187-125">上述範例中專為搭配 Windows Form 使用，而且需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.PaintEventHandler>。</span><span class="sxs-lookup"><span data-stu-id="a9187-125">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9187-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9187-126">See also</span></span>

- [<span data-ttu-id="a9187-127">使用字型和文字</span><span class="sxs-lookup"><span data-stu-id="a9187-127">Using Fonts and Text</span></span>](using-fonts-and-text.md)
- [<span data-ttu-id="a9187-128">Windows Forms 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="a9187-128">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)

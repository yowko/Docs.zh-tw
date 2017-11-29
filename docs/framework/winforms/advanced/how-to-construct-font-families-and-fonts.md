---
title: "如何：建構字型系列和字型"
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
- font families [Windows Forms], constructing
- fonts [Windows Forms], constructing
ms.assetid: d3a4a223-9492-4b54-9afd-db1c31c3cefd
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 066cf358e43dabb3b952b32ecec34ca77c6e8c38
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-construct-font-families-and-fonts"></a><span data-ttu-id="4cb8d-102">如何：建構字型系列和字型</span><span class="sxs-lookup"><span data-stu-id="4cb8d-102">How to: Construct Font Families and Fonts</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="4cb8d-103">字型的字體相同但不同的樣式分組字型家族。</span><span class="sxs-lookup"><span data-stu-id="4cb8d-103"> groups fonts with the same typeface but different styles into font families.</span></span> <span data-ttu-id="4cb8d-104">例如，新細明體字型系列包含下列字型：</span><span class="sxs-lookup"><span data-stu-id="4cb8d-104">For example, the Arial font family contains the following fonts:</span></span>  
  
-   <span data-ttu-id="4cb8d-105">新細明體一般</span><span class="sxs-lookup"><span data-stu-id="4cb8d-105">Arial Regular</span></span>  
  
-   <span data-ttu-id="4cb8d-106">新細明體粗體</span><span class="sxs-lookup"><span data-stu-id="4cb8d-106">Arial Bold</span></span>  
  
-   <span data-ttu-id="4cb8d-107">新細明體，斜體</span><span class="sxs-lookup"><span data-stu-id="4cb8d-107">Arial Italic</span></span>  
  
-   <span data-ttu-id="4cb8d-108">新細明體</span><span class="sxs-lookup"><span data-stu-id="4cb8d-108">Arial Bold Italic</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="4cb8d-109">使用四個以表單系列樣式： 一般、 粗體、 斜體和粗體斜體。</span><span class="sxs-lookup"><span data-stu-id="4cb8d-109"> uses four styles to form families: regular, bold, italic, and bold italic.</span></span> <span data-ttu-id="4cb8d-110">例如形容詞*縮小*和*四捨五入*不會被視為樣式; 而是它們是完整的系列名稱。</span><span class="sxs-lookup"><span data-stu-id="4cb8d-110">Adjectives such as *narrow* and *rounded* are not considered styles; rather they are part of the family name.</span></span> <span data-ttu-id="4cb8d-111">例如，新細明體窄是字型家族具有下列成員：</span><span class="sxs-lookup"><span data-stu-id="4cb8d-111">For example, Arial Narrow is a font family with the following members:</span></span>  
  
-   <span data-ttu-id="4cb8d-112">新細明體窄的規則</span><span class="sxs-lookup"><span data-stu-id="4cb8d-112">Arial Narrow Regular</span></span>  
  
-   <span data-ttu-id="4cb8d-113">粗體的新細明體</span><span class="sxs-lookup"><span data-stu-id="4cb8d-113">Arial Narrow Bold</span></span>  
  
-   <span data-ttu-id="4cb8d-114">新細明體窄斜體</span><span class="sxs-lookup"><span data-stu-id="4cb8d-114">Arial Narrow Italic</span></span>  
  
-   <span data-ttu-id="4cb8d-115">窄的新細明體</span><span class="sxs-lookup"><span data-stu-id="4cb8d-115">Arial Narrow Bold Italic</span></span>  
  
 <span data-ttu-id="4cb8d-116">您可以繪製的文字之前[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]，您必須建構<xref:System.Drawing.FontFamily>物件和<xref:System.Drawing.Font>物件。</span><span class="sxs-lookup"><span data-stu-id="4cb8d-116">Before you can draw text with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you need to construct a <xref:System.Drawing.FontFamily> object and a <xref:System.Drawing.Font> object.</span></span> <span data-ttu-id="4cb8d-117"><xref:System.Drawing.FontFamily>物件指定字體 （例如，新細明體），而<xref:System.Drawing.Font>物件指定大小、 樣式和單位。</span><span class="sxs-lookup"><span data-stu-id="4cb8d-117">The <xref:System.Drawing.FontFamily> object specifies the typeface (for example, Arial), and the <xref:System.Drawing.Font> object specifies the size, style, and units.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4cb8d-118">範例</span><span class="sxs-lookup"><span data-stu-id="4cb8d-118">Example</span></span>  
 <span data-ttu-id="4cb8d-119">下列範例會建構標準大小為 16 個像素的新細明體字型樣式。</span><span class="sxs-lookup"><span data-stu-id="4cb8d-119">The following example constructs a regular style Arial font with a size of 16 pixels.</span></span> <span data-ttu-id="4cb8d-120">在下列程式碼中，第一個引數傳遞給<xref:System.Drawing.Font.%23ctor%2A>建構函式是<xref:System.Drawing.FontFamily>物件。</span><span class="sxs-lookup"><span data-stu-id="4cb8d-120">In the following code, the first argument passed to the <xref:System.Drawing.Font.%23ctor%2A> constructor is the <xref:System.Drawing.FontFamily> object.</span></span> <span data-ttu-id="4cb8d-121">第二個引數會指定第四個引數所識別的單位之字型的大小。</span><span class="sxs-lookup"><span data-stu-id="4cb8d-121">The second argument specifies the size of the font measured in units identified by the fourth argument.</span></span> <span data-ttu-id="4cb8d-122">第三個引數識別樣式。</span><span class="sxs-lookup"><span data-stu-id="4cb8d-122">The third argument identifies the style.</span></span>  
  
 <span data-ttu-id="4cb8d-123"><xref:System.Drawing.GraphicsUnit.Pixel>成員的<xref:System.Drawing.GraphicsUnit>列舉型別和<xref:System.Drawing.FontStyle.Regular>隸屬<xref:System.Drawing.FontStyle>列舉型別。</span><span class="sxs-lookup"><span data-stu-id="4cb8d-123"><xref:System.Drawing.GraphicsUnit.Pixel> is a member of the <xref:System.Drawing.GraphicsUnit> enumeration, and <xref:System.Drawing.FontStyle.Regular> is a member of the <xref:System.Drawing.FontStyle> enumeration.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.FontsAndText#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4cb8d-124">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="4cb8d-124">Compiling the Code</span></span>  
 <span data-ttu-id="4cb8d-125">上述範例設計是為搭配 Windows Form 使用所設計，而且需要 <xref:System.Windows.Forms.PaintEventArgs>`e`，這是 <xref:System.Windows.Forms.PaintEventHandler> 的參數。</span><span class="sxs-lookup"><span data-stu-id="4cb8d-125">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cb8d-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4cb8d-126">See Also</span></span>  
 [<span data-ttu-id="4cb8d-127">使用字型和文字</span><span class="sxs-lookup"><span data-stu-id="4cb8d-127">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [<span data-ttu-id="4cb8d-128">Windows Forms 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="4cb8d-128">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)

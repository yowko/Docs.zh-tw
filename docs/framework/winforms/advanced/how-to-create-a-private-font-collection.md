---
title: "如何：建立私用字型集合"
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
- private font collections [Windows Forms], creating
- fonts [Windows Forms], creating private collections
ms.assetid: 6533d5e5-a8dc-4b76-9fc4-3bf75c8b9212
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8c0107b1ef1d5259835c6fb1666519d3fc06f4e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-private-font-collection"></a><span data-ttu-id="ed12f-102">如何：建立私用字型集合</span><span class="sxs-lookup"><span data-stu-id="ed12f-102">How to: Create a Private Font Collection</span></span>
<span data-ttu-id="ed12f-103"><xref:System.Drawing.Text.PrivateFontCollection>類別繼承自<xref:System.Drawing.Text.FontCollection>抽象基底類別。</span><span class="sxs-lookup"><span data-stu-id="ed12f-103">The <xref:System.Drawing.Text.PrivateFontCollection> class inherits from the <xref:System.Drawing.Text.FontCollection> abstract base class.</span></span> <span data-ttu-id="ed12f-104">您可以使用<xref:System.Drawing.Text.PrivateFontCollection>来維護一組專為您的應用程式的字型的物件。</span><span class="sxs-lookup"><span data-stu-id="ed12f-104">You can use a <xref:System.Drawing.Text.PrivateFontCollection> object to maintain a set of fonts specifically for your application.</span></span> <span data-ttu-id="ed12f-105">私用字型集合可以包含已安裝的系統字型，以及在電腦尚未安裝的字型。</span><span class="sxs-lookup"><span data-stu-id="ed12f-105">A private font collection can include installed system fonts as well as fonts that have not been installed on the computer.</span></span> <span data-ttu-id="ed12f-106">若要將字型檔案加入至私用字型集合中，呼叫<xref:System.Drawing.Text.PrivateFontCollection.AddFontFile%2A>方法<xref:System.Drawing.Text.PrivateFontCollection>物件。</span><span class="sxs-lookup"><span data-stu-id="ed12f-106">To add a font file to a private font collection, call the <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile%2A> method of a <xref:System.Drawing.Text.PrivateFontCollection> object.</span></span>  
  
 <span data-ttu-id="ed12f-107"><xref:System.Drawing.Text.FontCollection.Families%2A>屬性<xref:System.Drawing.Text.PrivateFontCollection>物件包含的陣列<xref:System.Drawing.FontFamily>物件。</span><span class="sxs-lookup"><span data-stu-id="ed12f-107">The <xref:System.Drawing.Text.FontCollection.Families%2A> property of a <xref:System.Drawing.Text.PrivateFontCollection> object contains an array of <xref:System.Drawing.FontFamily> objects.</span></span>  
  
 <span data-ttu-id="ed12f-108">私用字型集合中的字型家族的數目不一定已加入至集合中的字型檔案的數目相同。</span><span class="sxs-lookup"><span data-stu-id="ed12f-108">The number of font families in a private font collection is not necessarily the same as the number of font files that have been added to the collection.</span></span> <span data-ttu-id="ed12f-109">例如，假設您將 ArialBd.tff、 Times.tff 和 TimesBd.tff 檔案加入至集合。</span><span class="sxs-lookup"><span data-stu-id="ed12f-109">For example, suppose you add the files ArialBd.tff, Times.tff, and TimesBd.tff to a collection.</span></span> <span data-ttu-id="ed12f-110">會有三個檔案，但集合中的只有兩個系列因為 Times.tff 和 TimesBd.tff 屬於相同的系列。</span><span class="sxs-lookup"><span data-stu-id="ed12f-110">There will be three files but only two families in the collection because Times.tff and TimesBd.tff belong to the same family.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed12f-111">範例</span><span class="sxs-lookup"><span data-stu-id="ed12f-111">Example</span></span>  
 <span data-ttu-id="ed12f-112">下列範例會將在下列三個字型檔案<xref:System.Drawing.Text.PrivateFontCollection>物件：</span><span class="sxs-lookup"><span data-stu-id="ed12f-112">The following example adds the following three font files to a <xref:System.Drawing.Text.PrivateFontCollection> object:</span></span>  
  
-   <span data-ttu-id="ed12f-113">C:\\*systemroot*\Fonts\Arial.tff （新細明體，規則）</span><span class="sxs-lookup"><span data-stu-id="ed12f-113">C:\\*systemroot*\Fonts\Arial.tff (Arial, regular)</span></span>  
  
-   <span data-ttu-id="ed12f-114">C:\\*systemroot*\Fonts\CourBI.tff （： Courier New，粗體斜體)</span><span class="sxs-lookup"><span data-stu-id="ed12f-114">C:\\*systemroot*\Fonts\CourBI.tff (Courier New, bold italic)</span></span>  
  
-   <span data-ttu-id="ed12f-115">C:\\*systemroot*\Fonts\TimesBd.tff （新細明體，粗體顯示）</span><span class="sxs-lookup"><span data-stu-id="ed12f-115">C:\\*systemroot*\Fonts\TimesBd.tff (Times New Roman, bold)</span></span>  
  
 <span data-ttu-id="ed12f-116">程式碼會擷取陣列<xref:System.Drawing.FontFamily>物件從<xref:System.Drawing.Text.FontCollection.Families%2A>屬性<xref:System.Drawing.Text.PrivateFontCollection>物件。</span><span class="sxs-lookup"><span data-stu-id="ed12f-116">The code retrieves an array of <xref:System.Drawing.FontFamily> objects from the <xref:System.Drawing.Text.FontCollection.Families%2A> property of the <xref:System.Drawing.Text.PrivateFontCollection> object.</span></span>  
  
 <span data-ttu-id="ed12f-117">每個<xref:System.Drawing.FontFamily>物件在集合中，程式碼會呼叫<xref:System.Drawing.FontFamily.IsStyleAvailable%2A>方法，以判斷是否有可用的各種樣式 （一般、 粗體、 斜體、 粗體斜體、 底線和刪除線）。</span><span class="sxs-lookup"><span data-stu-id="ed12f-117">For each <xref:System.Drawing.FontFamily> object in the collection, the code calls the <xref:System.Drawing.FontFamily.IsStyleAvailable%2A> method to determine whether various styles (regular, bold, italic, bold italic, underline, and strikeout) are available.</span></span> <span data-ttu-id="ed12f-118">引數傳遞至<xref:System.Drawing.FontFamily.IsStyleAvailable%2A>方法屬於<xref:System.Drawing.FontStyle>列舉型別。</span><span class="sxs-lookup"><span data-stu-id="ed12f-118">The arguments passed to the <xref:System.Drawing.FontFamily.IsStyleAvailable%2A> method are members of the <xref:System.Drawing.FontStyle> enumeration.</span></span>  
  
 <span data-ttu-id="ed12f-119">如果指定的家族樣式組合功能<xref:System.Drawing.Font>物件建構使用該家族和樣式。</span><span class="sxs-lookup"><span data-stu-id="ed12f-119">If a given family/style combination is available, a <xref:System.Drawing.Font> object is constructed using that family and style.</span></span> <span data-ttu-id="ed12f-120">第一個引數傳遞至<xref:System.Drawing.Font.%23ctor%2A>建構函式是字型家族名稱 (不<xref:System.Drawing.FontFamily>物件適用於其他變化<xref:System.Drawing.Font.%23ctor%2A>建構函式)。</span><span class="sxs-lookup"><span data-stu-id="ed12f-120">The first argument passed to the <xref:System.Drawing.Font.%23ctor%2A> constructor is the font family name (not a <xref:System.Drawing.FontFamily> object as is the case for other variations of the <xref:System.Drawing.Font.%23ctor%2A> constructor).</span></span> <span data-ttu-id="ed12f-121">之後<xref:System.Drawing.Font>建構物件，它會傳遞至<xref:System.Drawing.Graphics.DrawString%2A>方法<xref:System.Drawing.Graphics>類別來顯示系列名稱，連同樣式的名稱。</span><span class="sxs-lookup"><span data-stu-id="ed12f-121">After the <xref:System.Drawing.Font> object is constructed, it is passed to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> class to display the family name along with the name of the style.</span></span>  
  
 <span data-ttu-id="ed12f-122">下列程式碼的輸出與下圖中顯示的輸出相似。</span><span class="sxs-lookup"><span data-stu-id="ed12f-122">The output of the following code is similar to the output shown in the following illustration.</span></span>  
  
 <span data-ttu-id="ed12f-123">![字型文字](../../../../docs/framework/winforms/advanced/media/csfontstext7.png "csfontstext7")</span><span class="sxs-lookup"><span data-stu-id="ed12f-123">![Fonts Text](../../../../docs/framework/winforms/advanced/media/csfontstext7.png "csfontstext7")</span></span>  
  
 <span data-ttu-id="ed12f-124">Arial.tff （其中已加入至下列程式碼範例的私用字型集合） 是字型檔案，新細明體標準的樣式。</span><span class="sxs-lookup"><span data-stu-id="ed12f-124">Arial.tff (which was added to the private font collection in the following code example) is the font file for the Arial regular style.</span></span> <span data-ttu-id="ed12f-125">不過請注意，程式輸出會顯示數個可用樣式，而不是一般的新細明體字型系列。</span><span class="sxs-lookup"><span data-stu-id="ed12f-125">Note, however, that the program output shows several available styles other than regular for the Arial font family.</span></span> <span data-ttu-id="ed12f-126">這是因為[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]可以模擬粗體、 斜體和粗體斜體樣式，從標準的樣式。</span><span class="sxs-lookup"><span data-stu-id="ed12f-126">That is because [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] can simulate the bold, italic, and bold italic styles from the regular style.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="ed12f-127">也可產生底線與 strikeouts 從標準的樣式。</span><span class="sxs-lookup"><span data-stu-id="ed12f-127"> can also produce underlines and strikeouts from the regular style.</span></span>  
  
 <span data-ttu-id="ed12f-128">同樣地，[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]可以模擬從粗體樣式或斜體樣式的粗體斜體樣式。</span><span class="sxs-lookup"><span data-stu-id="ed12f-128">Similarly, [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] can simulate the bold italic style from either the bold style or the italic style.</span></span> <span data-ttu-id="ed12f-129">程式輸出顯示在即使 TimesBd.tff （新細明體，粗體顯示） 是唯一適用於時間系列粗體斜體樣式集合中的次檔案。</span><span class="sxs-lookup"><span data-stu-id="ed12f-129">The program output shows that the bold italic style is available for the Times family even though TimesBd.tff (Times New Roman, bold) is the only Times file in the collection.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.FontsAndText#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ed12f-130">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="ed12f-130">Compiling the Code</span></span>  
 <span data-ttu-id="ed12f-131">上述範例設計是為搭配 Windows Form 使用所設計，而且需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.PaintEventHandler> 的參數。</span><span class="sxs-lookup"><span data-stu-id="ed12f-131">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed12f-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="ed12f-132">See Also</span></span>  
 <xref:System.Drawing.Text.PrivateFontCollection>  
 [<span data-ttu-id="ed12f-133">使用字型和文字</span><span class="sxs-lookup"><span data-stu-id="ed12f-133">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)

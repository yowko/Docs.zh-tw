---
title: HOW TO：將自訂資料新增至筆墨資料
ms.date: 03/30/2017
helpviewer_keywords:
- ink data [WPF], adding custom data
- InkCanvas [WPF], displaying
ms.assetid: f02aac6f-3436-4f7c-b6ea-0452cba5332c
ms.openlocfilehash: 7c59a205df5358daec101339cc6a308c8e38a9d6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64640860"
---
# <a name="how-to-add-custom-data-to-ink-data"></a><span data-ttu-id="45770-102">HOW TO：將自訂資料新增至筆墨資料</span><span class="sxs-lookup"><span data-stu-id="45770-102">How to: Add Custom Data to Ink Data</span></span>
<span data-ttu-id="45770-103">您可以將自訂資料加入時，筆墨會儲存成筆墨序列化格式 (ISF) 將儲存的筆墨。</span><span class="sxs-lookup"><span data-stu-id="45770-103">You can add custom data to ink that will be saved when the ink is saved as ink serialized format (ISF).</span></span>  <span data-ttu-id="45770-104">您可以自訂將資料儲存到<xref:System.Windows.Ink.DrawingAttributes>，則<xref:System.Windows.Ink.StrokeCollection>，或<xref:System.Windows.Ink.Stroke>。</span><span class="sxs-lookup"><span data-stu-id="45770-104">You can save the custom data to the <xref:System.Windows.Ink.DrawingAttributes>, the <xref:System.Windows.Ink.StrokeCollection>, or the <xref:System.Windows.Ink.Stroke>.</span></span>  <span data-ttu-id="45770-105">能夠將自訂的資料儲存在三個物件上，讓您能夠決定最佳的位置來儲存資料。</span><span class="sxs-lookup"><span data-stu-id="45770-105">Being able to save custom data on three objects gives you the ability to decide the best place to save the data.</span></span>  <span data-ttu-id="45770-106">所有三個類別會使用類似的方法，來儲存及存取自訂的資料。</span><span class="sxs-lookup"><span data-stu-id="45770-106">All three classes use similar methods to store and access custom data.</span></span>  
  
 <span data-ttu-id="45770-107">只有下列類型可以儲存為自訂的資料：</span><span class="sxs-lookup"><span data-stu-id="45770-107">Only the following types can be saved as custom data:</span></span>  
  
- <xref:System.Boolean>  
  
- <span data-ttu-id="45770-108"><xref:System.Boolean>[]</span><span class="sxs-lookup"><span data-stu-id="45770-108"><xref:System.Boolean>[]</span></span>  
  
- <xref:System.Byte>  
  
- <span data-ttu-id="45770-109"><xref:System.Byte>[]</span><span class="sxs-lookup"><span data-stu-id="45770-109"><xref:System.Byte>[]</span></span>  
  
- <xref:System.Char>  
  
- <span data-ttu-id="45770-110"><xref:System.Char>[]</span><span class="sxs-lookup"><span data-stu-id="45770-110"><xref:System.Char>[]</span></span>  
  
- <xref:System.DateTime>  
  
- <span data-ttu-id="45770-111"><xref:System.DateTime>[]</span><span class="sxs-lookup"><span data-stu-id="45770-111"><xref:System.DateTime>[]</span></span>  
  
- <xref:System.Decimal>  
  
- <span data-ttu-id="45770-112"><xref:System.Decimal>[]</span><span class="sxs-lookup"><span data-stu-id="45770-112"><xref:System.Decimal>[]</span></span>  
  
- <xref:System.Double>  
  
- <span data-ttu-id="45770-113"><xref:System.Double>[]</span><span class="sxs-lookup"><span data-stu-id="45770-113"><xref:System.Double>[]</span></span>  
  
- <xref:System.Int16>  
  
- <span data-ttu-id="45770-114"><xref:System.Int16>[]</span><span class="sxs-lookup"><span data-stu-id="45770-114"><xref:System.Int16>[]</span></span>  
  
- <xref:System.Int32>  
  
- <span data-ttu-id="45770-115"><xref:System.Int32>[]</span><span class="sxs-lookup"><span data-stu-id="45770-115"><xref:System.Int32>[]</span></span>  
  
- <xref:System.Int64>  
  
- <span data-ttu-id="45770-116"><xref:System.Int64>[]</span><span class="sxs-lookup"><span data-stu-id="45770-116"><xref:System.Int64>[]</span></span>  
  
- <xref:System.Single>  
  
- <span data-ttu-id="45770-117"><xref:System.Single>[]</span><span class="sxs-lookup"><span data-stu-id="45770-117"><xref:System.Single>[]</span></span>  
  
- <xref:System.String>  
  
- <xref:System.UInt16>  
  
- <span data-ttu-id="45770-118"><xref:System.UInt16>[]</span><span class="sxs-lookup"><span data-stu-id="45770-118"><xref:System.UInt16>[]</span></span>  
  
- <xref:System.UInt32>  
  
- <span data-ttu-id="45770-119"><xref:System.UInt32>[]</span><span class="sxs-lookup"><span data-stu-id="45770-119"><xref:System.UInt32>[]</span></span>  
  
- <xref:System.UInt64>  
  
- <span data-ttu-id="45770-120"><xref:System.UInt64>[]</span><span class="sxs-lookup"><span data-stu-id="45770-120"><xref:System.UInt64>[]</span></span>  
  
## <a name="example"></a><span data-ttu-id="45770-121">範例</span><span class="sxs-lookup"><span data-stu-id="45770-121">Example</span></span>  
 <span data-ttu-id="45770-122">下列範例示範如何新增和擷取自訂的資料，從<xref:System.Windows.Ink.StrokeCollection>。</span><span class="sxs-lookup"><span data-stu-id="45770-122">The following example demonstrates how to add and retrieve custom data from a <xref:System.Windows.Ink.StrokeCollection>.</span></span>  
  
 [!code-csharp[HowToAddCustomDataToInk#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#1)]  
  
 <span data-ttu-id="45770-123">下列範例會建立應用程式，顯示<xref:System.Windows.Controls.InkCanvas>和兩個按鈕。</span><span class="sxs-lookup"><span data-stu-id="45770-123">The following example creates an application that displays an <xref:System.Windows.Controls.InkCanvas> and two buttons.</span></span>  <span data-ttu-id="45770-124">[] 按鈕， `switchAuthor`，可讓兩個不同的作者所使用的兩種筆。</span><span class="sxs-lookup"><span data-stu-id="45770-124">The button, `switchAuthor`, enables two pens to be used by two different authors.</span></span>  <span data-ttu-id="45770-125">[] 按鈕`changePenColors`上變更的每個筆劃色彩<xref:System.Windows.Controls.InkCanvas>根據作者。</span><span class="sxs-lookup"><span data-stu-id="45770-125">The button `changePenColors` changes the color of each stroke on the <xref:System.Windows.Controls.InkCanvas> according to the author.</span></span>  <span data-ttu-id="45770-126">應用程式會定義兩個<xref:System.Windows.Ink.DrawingAttributes>物件，並將自訂屬性加入至作者所繪製的圖會指出每個<xref:System.Windows.Ink.Stroke>。</span><span class="sxs-lookup"><span data-stu-id="45770-126">The application defines two <xref:System.Windows.Ink.DrawingAttributes> objects and adds a custom property to each one that indicates which author drew the <xref:System.Windows.Ink.Stroke>.</span></span>  <span data-ttu-id="45770-127">當使用者按一下`changePenColors`，應用程式的自訂屬性的值根據筆劃的外觀會變更。</span><span class="sxs-lookup"><span data-stu-id="45770-127">When the user clicks `changePenColors`, the application changes the appearance of the stroke according to the value of the custom property.</span></span>  
  
 [!code-xaml[HowToAddCustomDataToInk#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[HowToAddCustomDataToInk#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#3)]

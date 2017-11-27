---
title: "如何：將自訂資料加入至筆墨資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ink data [WPF], adding custom data
- InkCanvas [WPF], displaying
ms.assetid: f02aac6f-3436-4f7c-b6ea-0452cba5332c
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f266f3c98ca64c80ccbb669a1cc646321754579f
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-add-custom-data-to-ink-data"></a><span data-ttu-id="da5f0-102">如何：將自訂資料加入至筆墨資料</span><span class="sxs-lookup"><span data-stu-id="da5f0-102">How to: Add Custom Data to Ink Data</span></span>
<span data-ttu-id="da5f0-103">您可以將自訂資料加入筆墨會儲存為筆跡序列化格式 (ISF) 時將會儲存的筆墨。</span><span class="sxs-lookup"><span data-stu-id="da5f0-103">You can add custom data to ink that will be saved when the ink is saved as ink serialized format (ISF).</span></span>  <span data-ttu-id="da5f0-104">您可以將自訂的資料，以儲存<xref:System.Windows.Ink.DrawingAttributes>、 <xref:System.Windows.Ink.StrokeCollection>，或<xref:System.Windows.Ink.Stroke>。</span><span class="sxs-lookup"><span data-stu-id="da5f0-104">You can save the custom data to the <xref:System.Windows.Ink.DrawingAttributes>, the <xref:System.Windows.Ink.StrokeCollection>, or the <xref:System.Windows.Ink.Stroke>.</span></span>  <span data-ttu-id="da5f0-105">能夠將自訂資料儲存在三個物件上，讓您能夠決定最佳的位置來儲存資料。</span><span class="sxs-lookup"><span data-stu-id="da5f0-105">Being able to save custom data on three objects gives you the ability to decide the best place to save the data.</span></span>  <span data-ttu-id="da5f0-106">所有三個類別使用類似的方法來儲存及存取自訂的資料。</span><span class="sxs-lookup"><span data-stu-id="da5f0-106">All three classes use similar methods to store and access custom data.</span></span>  
  
 <span data-ttu-id="da5f0-107">只能使用下列類型可以儲存為自訂的資料：</span><span class="sxs-lookup"><span data-stu-id="da5f0-107">Only the following types can be saved as custom data:</span></span>  
  
-   <xref:System.Boolean>  
  
-   <span data-ttu-id="da5f0-108"><xref:System.Boolean>[]</span><span class="sxs-lookup"><span data-stu-id="da5f0-108"><xref:System.Boolean>[]</span></span>  
  
-   <xref:System.Byte>  
  
-   <span data-ttu-id="da5f0-109"><xref:System.Byte>[]</span><span class="sxs-lookup"><span data-stu-id="da5f0-109"><xref:System.Byte>[]</span></span>  
  
-   <xref:System.Char>  
  
-   <span data-ttu-id="da5f0-110"><xref:System.Char>[]</span><span class="sxs-lookup"><span data-stu-id="da5f0-110"><xref:System.Char>[]</span></span>  
  
-   <xref:System.DateTime>  
  
-   <span data-ttu-id="da5f0-111"><xref:System.DateTime>[]</span><span class="sxs-lookup"><span data-stu-id="da5f0-111"><xref:System.DateTime>[]</span></span>  
  
-   <xref:System.Decimal>  
  
-   <span data-ttu-id="da5f0-112"><xref:System.Decimal>[]</span><span class="sxs-lookup"><span data-stu-id="da5f0-112"><xref:System.Decimal>[]</span></span>  
  
-   <xref:System.Double>  
  
-   <span data-ttu-id="da5f0-113"><xref:System.Double>[]</span><span class="sxs-lookup"><span data-stu-id="da5f0-113"><xref:System.Double>[]</span></span>  
  
-   <xref:System.Int16>  
  
-   <span data-ttu-id="da5f0-114"><xref:System.Int16>[]</span><span class="sxs-lookup"><span data-stu-id="da5f0-114"><xref:System.Int16>[]</span></span>  
  
-   <xref:System.Int32>  
  
-   <span data-ttu-id="da5f0-115"><xref:System.Int32>[]</span><span class="sxs-lookup"><span data-stu-id="da5f0-115"><xref:System.Int32>[]</span></span>  
  
-   <xref:System.Int64>  
  
-   <span data-ttu-id="da5f0-116"><xref:System.Int64>[]</span><span class="sxs-lookup"><span data-stu-id="da5f0-116"><xref:System.Int64>[]</span></span>  
  
-   <xref:System.Single>  
  
-   <span data-ttu-id="da5f0-117"><xref:System.Single>[]</span><span class="sxs-lookup"><span data-stu-id="da5f0-117"><xref:System.Single>[]</span></span>  
  
-   <xref:System.String>  
  
-   <xref:System.UInt16>  
  
-   <span data-ttu-id="da5f0-118"><xref:System.UInt16>[]</span><span class="sxs-lookup"><span data-stu-id="da5f0-118"><xref:System.UInt16>[]</span></span>  
  
-   <xref:System.UInt32>  
  
-   <span data-ttu-id="da5f0-119"><xref:System.UInt32>[]</span><span class="sxs-lookup"><span data-stu-id="da5f0-119"><xref:System.UInt32>[]</span></span>  
  
-   <xref:System.UInt64>  
  
-   <span data-ttu-id="da5f0-120"><xref:System.UInt64>[]</span><span class="sxs-lookup"><span data-stu-id="da5f0-120"><xref:System.UInt64>[]</span></span>  
  
## <a name="example"></a><span data-ttu-id="da5f0-121">範例</span><span class="sxs-lookup"><span data-stu-id="da5f0-121">Example</span></span>  
 <span data-ttu-id="da5f0-122">下列範例示範如何加入和擷取自訂的資料，從<xref:System.Windows.Ink.StrokeCollection>。</span><span class="sxs-lookup"><span data-stu-id="da5f0-122">The following example demonstrates how to add and retrieve custom data from a <xref:System.Windows.Ink.StrokeCollection>.</span></span>  
  
 [!code-csharp[HowToAddCustomDataToInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#1)]  
  
 <span data-ttu-id="da5f0-123">下列範例會建立應用程式，顯示<xref:System.Windows.Controls.InkCanvas>和兩個按鈕。</span><span class="sxs-lookup"><span data-stu-id="da5f0-123">The following example creates an application that displays an <xref:System.Windows.Controls.InkCanvas> and two buttons.</span></span>  <span data-ttu-id="da5f0-124">[] 按鈕， `switchAuthor`，可讓兩個不同的作者可以使用兩個的畫筆。</span><span class="sxs-lookup"><span data-stu-id="da5f0-124">The button, `switchAuthor`, enables two pens to be used by two different authors.</span></span>  <span data-ttu-id="da5f0-125">按鈕`changePenColors`上變更的每一個色彩<xref:System.Windows.Controls.InkCanvas>根據作者。</span><span class="sxs-lookup"><span data-stu-id="da5f0-125">The button `changePenColors` changes the color of each stroke on the <xref:System.Windows.Controls.InkCanvas> according to the author.</span></span>  <span data-ttu-id="da5f0-126">應用程式會定義兩個<xref:System.Windows.Ink.DrawingAttributes>物件，並將自訂屬性加入至所指出的作者所繪製的每一個<xref:System.Windows.Ink.Stroke>。</span><span class="sxs-lookup"><span data-stu-id="da5f0-126">The application defines two <xref:System.Windows.Ink.DrawingAttributes> objects and adds a custom property to each one that indicates which author drew the <xref:System.Windows.Ink.Stroke>.</span></span>  <span data-ttu-id="da5f0-127">當使用者按一下`changePenColors`，應用程式的自訂屬性的值根據筆劃的外觀會變更。</span><span class="sxs-lookup"><span data-stu-id="da5f0-127">When the user clicks `changePenColors`, the application changes the appearance of the stroke according to the value of the custom property.</span></span>  
  
 [!code-xaml[HowToAddCustomDataToInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[HowToAddCustomDataToInk#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#3)]

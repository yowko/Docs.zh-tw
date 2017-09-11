---
title: "在 XNA 應用程式中使用操作和慣性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b7c18905-850c-4da4-8977-a074406a4263
caps.latest.revision: 7
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7d623a8c2276811ae443a4d745faffeeb79ffc6f
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="using-manipulations-and-inertia-in-an-xna-application"></a><span data-ttu-id="f4654-102">在 XNA 應用程式中使用操作和慣性</span><span class="sxs-lookup"><span data-stu-id="f4654-102">Using Manipulations and Inertia in an XNA Application</span></span>
<span data-ttu-id="f4654-103">本文說明如何在 Microsoft XNA 應用程式中使用操作和慣性處理，來控制遊戲個件的移動。</span><span class="sxs-lookup"><span data-stu-id="f4654-103">This article describes how you can use manipulations and inertia processing in a Microsoft XNA application to control the movement of game pieces.</span></span> <span data-ttu-id="f4654-104">在閱讀本文之前，您應該先熟悉[操作和慣性概觀](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md)主題和基本 XNA 程式設計概念。</span><span class="sxs-lookup"><span data-stu-id="f4654-104">Before you read this article, you should be familiar with the [Manipulations and Inertia Overview](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md) topic, and be familiar with basic XNA programming concepts.</span></span>  
  
 <span data-ttu-id="f4654-105">若要執行本文描述的工作，您的 XNA 專案必須參考 <xref:System.Windows.Input.Manipulations> 組件，而您的電腦上必須安裝 [XNA Game Studio](http://msdn.microsoft.com/library/bb200104.aspx) ([下載](http://www.microsoft.com/downloads/details.aspx?FamilyId=7D70D6ED-1EDD-4852-9883-9A33C0AD8FEE&displaylang=en))，以便專案可以參考 XNA 組件。</span><span class="sxs-lookup"><span data-stu-id="f4654-105">To perform the tasks described in this article, your XNA project must reference the <xref:System.Windows.Input.Manipulations> assembly, and you must have [XNA Game Studio](http://msdn.microsoft.com/library/bb200104.aspx) ([download](http://www.microsoft.com/downloads/details.aspx?FamilyId=7D70D6ED-1EDD-4852-9883-9A33C0AD8FEE&displaylang=en)) installed on your computer so that your project can reference the XNA assemblies.</span></span>  
  
## <a name="overview-of-functionality"></a><span data-ttu-id="f4654-106">功能概觀</span><span class="sxs-lookup"><span data-stu-id="f4654-106">Overview of Functionality</span></span>  
 <span data-ttu-id="f4654-107">本文示範如何建立代表使用操作和慣性處理之遊戲個件的自訂類別。</span><span class="sxs-lookup"><span data-stu-id="f4654-107">This article shows you how to create a custom class that represents a game piece that uses manipulation and inertia processing.</span></span> <span data-ttu-id="f4654-108">這個類別可讓您透過使用滑鼠拖曳再放開的方式，在畫面上操作遊戲個件。</span><span class="sxs-lookup"><span data-stu-id="f4654-108">This class enables you to manipulate a game piece across the screen by dragging it with the mouse, and then releasing it.</span></span> <span data-ttu-id="f4654-109">放開滑鼠之後，慣性處理會讓遊戲個件保持移動，但速度會逐漸變慢。</span><span class="sxs-lookup"><span data-stu-id="f4654-109">Once released, inertia processing keeps the game piece moving as it gradually slows down.</span></span> <span data-ttu-id="f4654-110">移動方式包括線性移動和角度移動。</span><span class="sxs-lookup"><span data-stu-id="f4654-110">Movement is both linear and angular.</span></span>  
  
 <span data-ttu-id="f4654-111">![簡單的操作和慣性應用。](../../../docs/framework/common-client-technologies/media/ndp-gamexna.jpg "NDP_GameXna")</span><span class="sxs-lookup"><span data-stu-id="f4654-111">![A simple manipulations and inertia application.](../../../docs/framework/common-client-technologies/media/ndp-gamexna.jpg "NDP_GameXna")</span></span>  
  
 <span data-ttu-id="f4654-112">此外，您可以建立管理多個遊戲個件的自訂集合。</span><span class="sxs-lookup"><span data-stu-id="f4654-112">In addition, a custom collection is created that manages multiple game pieces.</span></span> <span data-ttu-id="f4654-113">這樣做會簡化 XNA Game 類別所需的處理。</span><span class="sxs-lookup"><span data-stu-id="f4654-113">This simplifies the handling that is required from the XNA Game class.</span></span>  
  
 [<span data-ttu-id="f4654-114">建立 GamePiece 類別</span><span class="sxs-lookup"><span data-stu-id="f4654-114">Creating the GamePiece Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
  
 [<span data-ttu-id="f4654-115">建立 GamePieceCollection 類別</span><span class="sxs-lookup"><span data-stu-id="f4654-115">Creating the GamePieceCollection Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
  
 [<span data-ttu-id="f4654-116">建立 Game1 類別</span><span class="sxs-lookup"><span data-stu-id="f4654-116">Creating the Game1 Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)  
  
 [<span data-ttu-id="f4654-117">完整程式碼清單</span><span class="sxs-lookup"><span data-stu-id="f4654-117">Full Code Listings</span></span>](../../../docs/framework/common-client-technologies/full-code-listings.md)  
  
## <a name="see-also"></a><span data-ttu-id="f4654-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4654-118">See Also</span></span>  
 <span data-ttu-id="f4654-119"><xref:System.Windows.Input.Manipulations></span><span class="sxs-lookup"><span data-stu-id="f4654-119"><xref:System.Windows.Input.Manipulations></span></span>   
 [<span data-ttu-id="f4654-120">操作和慣性概觀</span><span class="sxs-lookup"><span data-stu-id="f4654-120">Manipulations and Inertia Overview</span></span>](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md)


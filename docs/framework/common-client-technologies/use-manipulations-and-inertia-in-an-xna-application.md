---
title: 在 XNA 應用程式中使用操作和慣性
ms.date: 03/30/2017
ms.assetid: b7c18905-850c-4da4-8977-a074406a4263
ms.openlocfilehash: 70b8d0c5c098089b6f16ef817ff86698f68cf7c3
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2018
ms.locfileid: "43478139"
---
# <a name="using-manipulations-and-inertia-in-an-xna-application"></a><span data-ttu-id="b172d-102">在 XNA 應用程式中使用操作和慣性</span><span class="sxs-lookup"><span data-stu-id="b172d-102">Using Manipulations and Inertia in an XNA Application</span></span>
<span data-ttu-id="b172d-103">本文說明如何在 Microsoft XNA 應用程式中使用操作和慣性處理，來控制遊戲個件的移動。</span><span class="sxs-lookup"><span data-stu-id="b172d-103">This article describes how you can use manipulations and inertia processing in a Microsoft XNA application to control the movement of game pieces.</span></span> <span data-ttu-id="b172d-104">在閱讀本文之前，您應該先熟悉[操作和慣性概觀](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md)主題和基本 XNA 程式設計概念。</span><span class="sxs-lookup"><span data-stu-id="b172d-104">Before you read this article, you should be familiar with the [Manipulations and Inertia Overview](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md) topic, and be familiar with basic XNA programming concepts.</span></span>  
  
 <span data-ttu-id="b172d-105">若要執行本文描述的工作，您的 XNA 專案必須參考 <xref:System.Windows.Input.Manipulations> 組件，而您的電腦上必須安裝 [XNA Game Studio](https://msdn.microsoft.com/library/bb200104.aspx) ([下載](https://www.microsoft.com/downloads/details.aspx?FamilyId=7D70D6ED-1EDD-4852-9883-9A33C0AD8FEE&displaylang=en))，以便專案可以參考 XNA 組件。</span><span class="sxs-lookup"><span data-stu-id="b172d-105">To perform the tasks described in this article, your XNA project must reference the <xref:System.Windows.Input.Manipulations> assembly, and you must have [XNA Game Studio](https://msdn.microsoft.com/library/bb200104.aspx) ([download](https://www.microsoft.com/downloads/details.aspx?FamilyId=7D70D6ED-1EDD-4852-9883-9A33C0AD8FEE&displaylang=en)) installed on your computer so that your project can reference the XNA assemblies.</span></span>  
  
## <a name="overview-of-functionality"></a><span data-ttu-id="b172d-106">功能概觀</span><span class="sxs-lookup"><span data-stu-id="b172d-106">Overview of Functionality</span></span>  
 <span data-ttu-id="b172d-107">本文示範如何建立代表使用操作和慣性處理之遊戲個件的自訂類別。</span><span class="sxs-lookup"><span data-stu-id="b172d-107">This article shows you how to create a custom class that represents a game piece that uses manipulation and inertia processing.</span></span> <span data-ttu-id="b172d-108">這個類別可讓您透過使用滑鼠拖曳再放開的方式，在畫面上操作遊戲個件。</span><span class="sxs-lookup"><span data-stu-id="b172d-108">This class enables you to manipulate a game piece across the screen by dragging it with the mouse, and then releasing it.</span></span> <span data-ttu-id="b172d-109">放開滑鼠之後，慣性處理會讓遊戲個件保持移動，但速度會逐漸變慢。</span><span class="sxs-lookup"><span data-stu-id="b172d-109">Once released, inertia processing keeps the game piece moving as it gradually slows down.</span></span> <span data-ttu-id="b172d-110">移動方式包括線性移動和角度移動。</span><span class="sxs-lookup"><span data-stu-id="b172d-110">Movement is both linear and angular.</span></span>  
  
 <span data-ttu-id="b172d-111">![簡單的操作和慣性應用。](../../../docs/framework/common-client-technologies/media/ndp-gamexna.jpg "NDP_GameXna")</span><span class="sxs-lookup"><span data-stu-id="b172d-111">![A simple manipulations and inertia application.](../../../docs/framework/common-client-technologies/media/ndp-gamexna.jpg "NDP_GameXna")</span></span>  
  
 <span data-ttu-id="b172d-112">此外，您可以建立管理多個遊戲個件的自訂集合。</span><span class="sxs-lookup"><span data-stu-id="b172d-112">In addition, a custom collection is created that manages multiple game pieces.</span></span> <span data-ttu-id="b172d-113">這樣做會簡化 XNA Game 類別所需的處理。</span><span class="sxs-lookup"><span data-stu-id="b172d-113">This simplifies the handling that is required from the XNA Game class.</span></span>  
  
 [<span data-ttu-id="b172d-114">建立 GamePiece 類別</span><span class="sxs-lookup"><span data-stu-id="b172d-114">Creating the GamePiece Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
  
 [<span data-ttu-id="b172d-115">建立 GamePieceCollection 類別</span><span class="sxs-lookup"><span data-stu-id="b172d-115">Creating the GamePieceCollection Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
  
 [<span data-ttu-id="b172d-116">建立 Game1 類別</span><span class="sxs-lookup"><span data-stu-id="b172d-116">Creating the Game1 Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)  
  
 [<span data-ttu-id="b172d-117">完整程式碼清單</span><span class="sxs-lookup"><span data-stu-id="b172d-117">Full Code Listings</span></span>](../../../docs/framework/common-client-technologies/full-code-listings.md)  
  
## <a name="see-also"></a><span data-ttu-id="b172d-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="b172d-118">See Also</span></span>  
 <xref:System.Windows.Input.Manipulations>  
 [<span data-ttu-id="b172d-119">操作和慣性概觀</span><span class="sxs-lookup"><span data-stu-id="b172d-119">Manipulations and Inertia Overview</span></span>](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md)

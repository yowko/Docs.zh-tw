---
title: "建立 Game1 類別"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 47932ce3-2ba5-476f-a26b-3ddfd5226f27
caps.latest.revision: 8
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9c6d0bdfd21f431ae6da38e3868386f91d5b725b
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="creating-the-game1-class"></a><span data-ttu-id="609a7-102">建立 Game1 類別</span><span class="sxs-lookup"><span data-stu-id="609a7-102">Creating the Game1 Class</span></span>
<span data-ttu-id="609a7-103">針對所有 Microsoft XNA 專案，Game1 類別衍生自 [Microsoft.Xna.Framework.Game](http://msdn.microsoft.com/library/microsoft.xna.framework.game.aspx) 類別，其為 XNA 遊戲提供基本的圖形裝置初始化、遊戲邏輯和轉譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="609a7-103">As with all Microsoft XNA projects, the Game1 class derives from the [Microsoft.Xna.Framework.Game](http://msdn.microsoft.com/library/microsoft.xna.framework.game.aspx) class, which provides basic graphics device initialization, game logic, and rendering code for XNA games.</span></span> <span data-ttu-id="609a7-104">Game1 類別相當簡單，因為大部分工作都是在 GamePiece 和 GamePieceCollection 類別中完成。</span><span class="sxs-lookup"><span data-stu-id="609a7-104">The Game1 class is fairly simple because most of the work in done in the GamePiece and GamePieceCollection classes.</span></span>  
  
## <a name="creating-the-code"></a><span data-ttu-id="609a7-105">建立程式碼</span><span class="sxs-lookup"><span data-stu-id="609a7-105">Creating the Code</span></span>  
 <span data-ttu-id="609a7-106">此類別的私用成員包含一個 **GamePieceCollection** 物件來保留遊戲片段、一個 [GraphicsDeviceManager](http://msdn.microsoft.com/library/microsoft.xna.framework.graphicsdevicemanager.aspx) 物件和一個用來轉譯遊戲片段的 [SpriteBatch](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.aspx) 物件。</span><span class="sxs-lookup"><span data-stu-id="609a7-106">The private members for the class consist of a **GamePieceCollection** object to hold the game pieces, a [GraphicsDeviceManager](http://msdn.microsoft.com/library/microsoft.xna.framework.graphicsdevicemanager.aspx) object, and a [SpriteBatch](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.aspx) object used to render game pieces.</span></span>  
  
 <span data-ttu-id="609a7-107">[!code-csharp[ManipulationXNA#_Game1_PrivateMembers](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_privatemembers)]</span><span class="sxs-lookup"><span data-stu-id="609a7-107">[!code-csharp[ManipulationXNA#_Game1_PrivateMembers](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_privatemembers)]</span></span>  
  
 <span data-ttu-id="609a7-108">在遊戲初始化期間，這些物件會具現化。</span><span class="sxs-lookup"><span data-stu-id="609a7-108">During game initialization, these objects are instantiated.</span></span>  
  
 <span data-ttu-id="609a7-109">[!code-csharp[ManipulationXNA#_Game1_ConstructorInitialize](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_constructorinitialize)]</span><span class="sxs-lookup"><span data-stu-id="609a7-109">[!code-csharp[ManipulationXNA#_Game1_ConstructorInitialize](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_constructorinitialize)]</span></span>  
  
 <span data-ttu-id="609a7-110">呼叫 [LoadContent](http://msdn.microsoft.com/library/microsoft.xna.framework.game.loadcontent.aspx) 方法時，會建立遊戲片段，並將其指派給 **GamePieceCollection** 物件。</span><span class="sxs-lookup"><span data-stu-id="609a7-110">When the [LoadContent](http://msdn.microsoft.com/library/microsoft.xna.framework.game.loadcontent.aspx) method is called, the game pieces are created and assigned to the **GamePieceCollection** object.</span></span> <span data-ttu-id="609a7-111">遊戲片段分為兩種類型：</span><span class="sxs-lookup"><span data-stu-id="609a7-111">There are two types of game pieces.</span></span> <span data-ttu-id="609a7-112">片段的縮放比例稍有變更，導致有些片段較小，有些片段較大。</span><span class="sxs-lookup"><span data-stu-id="609a7-112">The scale factor for the pieces is changed slightly so that there are some smaller and some larger pieces.</span></span>  
  
 <span data-ttu-id="609a7-113">[!code-csharp[ManipulationXNA#_Game1_LoadContent](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_loadcontent)]</span><span class="sxs-lookup"><span data-stu-id="609a7-113">[!code-csharp[ManipulationXNA#_Game1_LoadContent](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_loadcontent)]</span></span>  
  
 <span data-ttu-id="609a7-114">在執行遊戲時，XNA Framework 會重複呼叫 [Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) 方法。</span><span class="sxs-lookup"><span data-stu-id="609a7-114">The [Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) method is called repeatedly by the XNA Framework while the game is running.</span></span> <span data-ttu-id="609a7-115">[Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) 方法會在遊戲片段集合上呼叫 **ProcessInertia** 和 **UpdateFromMouse** 方法。</span><span class="sxs-lookup"><span data-stu-id="609a7-115">The [Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) method calls the **ProcessInertia** and the **UpdateFromMouse** methods on the game piece collection.</span></span> <span data-ttu-id="609a7-116">[建立 GamePieceCollection 類別](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)中有這些方法的說明。</span><span class="sxs-lookup"><span data-stu-id="609a7-116">These methods are described in [Creating the GamePieceCollection Class](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md).</span></span>  
  
 <span data-ttu-id="609a7-117">[!code-csharp[ManipulationXNA#_Game1_UpdateGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_updategame)]</span><span class="sxs-lookup"><span data-stu-id="609a7-117">[!code-csharp[ManipulationXNA#_Game1_UpdateGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_updategame)]</span></span>  
  
 <span data-ttu-id="609a7-118">在執行遊戲時，XNA Framework 也會重複呼叫 [Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) 方法。</span><span class="sxs-lookup"><span data-stu-id="609a7-118">The [Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) method is also called repeatedly by the XNA Framework while the game is running.</span></span> <span data-ttu-id="609a7-119">[Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) 方法會呼叫 **GamePieceCollection** 物件的 **Draw** 方法，來執行遊戲片段的轉譯。</span><span class="sxs-lookup"><span data-stu-id="609a7-119">The [Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) method performs the rendering of game pieces by calling the **Draw** method of the **GamePieceCollection** object.</span></span> <span data-ttu-id="609a7-120">[建立 GamePieceCollection 類別](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)中有這個方法的說明。</span><span class="sxs-lookup"><span data-stu-id="609a7-120">This method is described in[Creating the GamePieceCollection Class](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md).</span></span>  
  
 <span data-ttu-id="609a7-121">[!code-csharp[ManipulationXNA#_Game1_DrawGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_drawgame)]</span><span class="sxs-lookup"><span data-stu-id="609a7-121">[!code-csharp[ManipulationXNA#_Game1_DrawGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_drawgame)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="609a7-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="609a7-122">See Also</span></span>  
 <span data-ttu-id="609a7-123">[操作和慣性](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md) </span><span class="sxs-lookup"><span data-stu-id="609a7-123">[Manipulations and Inertia](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md) </span></span>  
 <span data-ttu-id="609a7-124">[在 XNA 應用程式中使用操作和慣性](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md) </span><span class="sxs-lookup"><span data-stu-id="609a7-124">[Using Manipulations and Inertia in an XNA Application](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md) </span></span>  
 <span data-ttu-id="609a7-125">[建立 GamePiece 類別](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md) </span><span class="sxs-lookup"><span data-stu-id="609a7-125">[Creating the GamePiece Class](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md) </span></span>  
 <span data-ttu-id="609a7-126">[建立 GamePieceCollection 類別](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md) </span><span class="sxs-lookup"><span data-stu-id="609a7-126">[Creating the GamePieceCollection Class](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md) </span></span>  
 [<span data-ttu-id="609a7-127">完整程式碼清單</span><span class="sxs-lookup"><span data-stu-id="609a7-127">Full Code Listings</span></span>](../../../docs/framework/common-client-technologies/full-code-listings.md)


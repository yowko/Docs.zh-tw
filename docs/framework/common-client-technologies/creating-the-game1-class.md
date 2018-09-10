---
title: 建立 Game1 類別
ms.date: 03/30/2017
ms.assetid: 47932ce3-2ba5-476f-a26b-3ddfd5226f27
ms.openlocfilehash: 368da9df4dffc7017abb02888bc2eb2641f04b8b
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44197834"
---
# <a name="creating-the-game1-class"></a><span data-ttu-id="03c99-102">建立 Game1 類別</span><span class="sxs-lookup"><span data-stu-id="03c99-102">Creating the Game1 Class</span></span>
<span data-ttu-id="03c99-103">針對所有 Microsoft XNA 專案，Game1 類別衍生自 [Microsoft.Xna.Framework.Game](https://msdn.microsoft.com/library/microsoft.xna.framework.game.aspx) 類別，其為 XNA 遊戲提供基本的圖形裝置初始化、遊戲邏輯和轉譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="03c99-103">As with all Microsoft XNA projects, the Game1 class derives from the [Microsoft.Xna.Framework.Game](https://msdn.microsoft.com/library/microsoft.xna.framework.game.aspx) class, which provides basic graphics device initialization, game logic, and rendering code for XNA games.</span></span> <span data-ttu-id="03c99-104">Game1 類別相當簡單，因為大部分工作都是在 GamePiece 和 GamePieceCollection 類別中完成。</span><span class="sxs-lookup"><span data-stu-id="03c99-104">The Game1 class is fairly simple because most of the work in done in the GamePiece and GamePieceCollection classes.</span></span>  
  
## <a name="creating-the-code"></a><span data-ttu-id="03c99-105">建立程式碼</span><span class="sxs-lookup"><span data-stu-id="03c99-105">Creating the Code</span></span>  
 <span data-ttu-id="03c99-106">此類別的私用成員包含一個 **GamePieceCollection** 物件來保留遊戲片段、一個 [GraphicsDeviceManager](https://msdn.microsoft.com/library/microsoft.xna.framework.graphicsdevicemanager.aspx) 物件和一個用來轉譯遊戲片段的 [SpriteBatch](https://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.aspx) 物件。</span><span class="sxs-lookup"><span data-stu-id="03c99-106">The private members for the class consist of a **GamePieceCollection** object to hold the game pieces, a [GraphicsDeviceManager](https://msdn.microsoft.com/library/microsoft.xna.framework.graphicsdevicemanager.aspx) object, and a [SpriteBatch](https://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.aspx) object used to render game pieces.</span></span>  
  
 [!code-csharp[ManipulationXNA#_Game1_PrivateMembers](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_privatemembers)]  
  
 <span data-ttu-id="03c99-107">在遊戲初始化期間，這些物件會具現化。</span><span class="sxs-lookup"><span data-stu-id="03c99-107">During game initialization, these objects are instantiated.</span></span>  
  
 [!code-csharp[ManipulationXNA#_Game1_ConstructorInitialize](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_constructorinitialize)]  
  
 <span data-ttu-id="03c99-108">呼叫 [LoadContent](https://msdn.microsoft.com/library/microsoft.xna.framework.game.loadcontent.aspx) 方法時，會建立遊戲片段，並將其指派給 **GamePieceCollection** 物件。</span><span class="sxs-lookup"><span data-stu-id="03c99-108">When the [LoadContent](https://msdn.microsoft.com/library/microsoft.xna.framework.game.loadcontent.aspx) method is called, the game pieces are created and assigned to the **GamePieceCollection** object.</span></span> <span data-ttu-id="03c99-109">遊戲片段分為兩種類型：</span><span class="sxs-lookup"><span data-stu-id="03c99-109">There are two types of game pieces.</span></span> <span data-ttu-id="03c99-110">片段的縮放比例稍有變更，導致有些片段較小，有些片段較大。</span><span class="sxs-lookup"><span data-stu-id="03c99-110">The scale factor for the pieces is changed slightly so that there are some smaller and some larger pieces.</span></span>  
  
 [!code-csharp[ManipulationXNA#_Game1_LoadContent](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_loadcontent)]  
  
 <span data-ttu-id="03c99-111">在執行遊戲時，XNA Framework 會重複呼叫 [Update](https://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) 方法。</span><span class="sxs-lookup"><span data-stu-id="03c99-111">The [Update](https://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) method is called repeatedly by the XNA Framework while the game is running.</span></span> <span data-ttu-id="03c99-112">[Update](https://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) 方法會在遊戲片段集合上呼叫 **ProcessInertia** 和 **UpdateFromMouse** 方法。</span><span class="sxs-lookup"><span data-stu-id="03c99-112">The [Update](https://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) method calls the **ProcessInertia** and the **UpdateFromMouse** methods on the game piece collection.</span></span> <span data-ttu-id="03c99-113">[建立 GamePieceCollection 類別](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)中有這些方法的說明。</span><span class="sxs-lookup"><span data-stu-id="03c99-113">These methods are described in [Creating the GamePieceCollection Class](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md).</span></span>  
  
 [!code-csharp[ManipulationXNA#_Game1_UpdateGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_updategame)]  
  
 <span data-ttu-id="03c99-114">在執行遊戲時，XNA Framework 也會重複呼叫 [Draw](https://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) 方法。</span><span class="sxs-lookup"><span data-stu-id="03c99-114">The [Draw](https://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) method is also called repeatedly by the XNA Framework while the game is running.</span></span> <span data-ttu-id="03c99-115">[Draw](https://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) 方法會呼叫 **GamePieceCollection** 物件的 **Draw** 方法，來執行遊戲片段的轉譯。</span><span class="sxs-lookup"><span data-stu-id="03c99-115">The [Draw](https://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) method performs the rendering of game pieces by calling the **Draw** method of the **GamePieceCollection** object.</span></span> <span data-ttu-id="03c99-116">[建立 GamePieceCollection 類別](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)中有這個方法的說明。</span><span class="sxs-lookup"><span data-stu-id="03c99-116">This method is described in[Creating the GamePieceCollection Class](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md).</span></span>  
  
 [!code-csharp[ManipulationXNA#_Game1_DrawGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_drawgame)]  
  
## <a name="see-also"></a><span data-ttu-id="03c99-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="03c99-117">See Also</span></span>  
 [<span data-ttu-id="03c99-118">操作和慣性</span><span class="sxs-lookup"><span data-stu-id="03c99-118">Manipulations and Inertia</span></span>](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md)  
 [<span data-ttu-id="03c99-119">在 XNA 應用程式中使用操作和慣性</span><span class="sxs-lookup"><span data-stu-id="03c99-119">Using Manipulations and Inertia in an XNA Application</span></span>](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md)  
 [<span data-ttu-id="03c99-120">建立 GamePiece 類別</span><span class="sxs-lookup"><span data-stu-id="03c99-120">Creating the GamePiece Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
 [<span data-ttu-id="03c99-121">建立 GamePieceCollection 類別</span><span class="sxs-lookup"><span data-stu-id="03c99-121">Creating the GamePieceCollection Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
 [<span data-ttu-id="03c99-122">完整程式碼清單</span><span class="sxs-lookup"><span data-stu-id="03c99-122">Full Code Listings</span></span>](../../../docs/framework/common-client-technologies/full-code-listings.md)

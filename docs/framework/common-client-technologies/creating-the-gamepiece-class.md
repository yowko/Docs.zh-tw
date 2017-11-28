---
title: "建立 GamePiece 類別"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37a27a86-ac1c-47be-b477-cb4b819459d3
caps.latest.revision: "9"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 989883034b30c3ec67f5441c5512418643546519
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="creating-the-gamepiece-class"></a><span data-ttu-id="b0119-102">建立 GamePiece 類別</span><span class="sxs-lookup"><span data-stu-id="b0119-102">Creating the GamePiece Class</span></span>
<span data-ttu-id="b0119-103">**GamePiece** 類別包含下列作業需要的所有功能：載入 Microsoft XNA 遊戲片段映像、追蹤與遊戲片段相關的滑鼠狀態、捕捉滑鼠、提供操作和慣性處理，以及提供當遊戲片段達到檢視區限制時的彈回功能。</span><span class="sxs-lookup"><span data-stu-id="b0119-103">The **GamePiece** class encapsulates all the functionality required to load a Microsoft XNA game piece image, track the state of the mouse in relation to the game piece, capture the mouse, provide manipulation and inertia processing, and provide bouncing capability when the game piece reaches the limits of the view port.</span></span>  
  
## <a name="private-members"></a><span data-ttu-id="b0119-104">私用成員</span><span class="sxs-lookup"><span data-stu-id="b0119-104">Private Members</span></span>  
 <span data-ttu-id="b0119-105">在 **GamePiece** 類別頂端，會宣告數個私用成員。</span><span class="sxs-lookup"><span data-stu-id="b0119-105">At the top of the **GamePiece** class, several private members are declared.</span></span>  
  
 [!code-csharp[ManipulationXNA#_GamePiece_PrivateMembers](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_privatemembers)]  
  
## <a name="public-properties"></a><span data-ttu-id="b0119-106">公用屬性</span><span class="sxs-lookup"><span data-stu-id="b0119-106">Public Properties</span></span>  
 <span data-ttu-id="b0119-107">其中三個私用成員會透過公用屬性公開。</span><span class="sxs-lookup"><span data-stu-id="b0119-107">Three of these private members are exposed through public properties.</span></span> <span data-ttu-id="b0119-108">**Scale** 和 **PieceColor** 屬性分別可讓應用程式指定比例和片段的色彩。</span><span class="sxs-lookup"><span data-stu-id="b0119-108">The **Scale** and **PieceColor** properties enable the application to specify the scale and the color of the piece, respectively.</span></span> <span data-ttu-id="b0119-109">**Bounds** 屬性的出現可讓一個片段利用另一個片段的界限來呈現其本身，例如當一個片段應重疊另一個片段時。</span><span class="sxs-lookup"><span data-stu-id="b0119-109">The **Bounds** property is exposed to enable one piece to use the bounds of another to render itself, such as when one piece should overlay another.</span></span> <span data-ttu-id="b0119-110">下列程式碼範例顯示公用屬性的宣告。</span><span class="sxs-lookup"><span data-stu-id="b0119-110">The following code shows the declaration of the public properties.</span></span>  
  
 [!code-csharp[ManipulationXNA#_GamePiece_PublicProperties](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_publicproperties)]  
  
## <a name="class-constructor"></a><span data-ttu-id="b0119-111">類別建構函式</span><span class="sxs-lookup"><span data-stu-id="b0119-111">Class Constructor</span></span>  
 <span data-ttu-id="b0119-112">**GamePiece** 類別的建構函式可接受下列參數：</span><span class="sxs-lookup"><span data-stu-id="b0119-112">The constructor for the **GamePiece** class accepts the following parameters:</span></span>  
  
-   <span data-ttu-id="b0119-113">[SpriteBatch](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.aspx) 類型。</span><span class="sxs-lookup"><span data-stu-id="b0119-113">A [SpriteBatch](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.aspx) type.</span></span> <span data-ttu-id="b0119-114">傳遞到這裡的參考會指派給私用成員 `spriteBatch`，並且在遊戲片段呈現其本身時，用來存取 [SpriteBatch.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.draw.aspx) 方法。</span><span class="sxs-lookup"><span data-stu-id="b0119-114">The reference passed here is assigned to the private member `spriteBatch`, and is used to access the [SpriteBatch.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.draw.aspx) method when the game piece renders itself.</span></span> <span data-ttu-id="b0119-115">此外，還會使用 [GraphicsDevice](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.graphicsdevice.aspx) 屬性來建立與遊戲片段建立關聯的 [Texture](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.texture.aspx) 物件，以及取得檢視區大小，以偵測遊戲片段何時遇到視窗界限，讓片段可以彈開。</span><span class="sxs-lookup"><span data-stu-id="b0119-115">In addition, the [GraphicsDevice](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.graphicsdevice.aspx) property is used to create the [Texture](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.texture.aspx) object associated with the game piece, and to obtain the size of the view port in order to detect when the game piece encounters a window boundary so that the piece can bounce.</span></span>  
  
-   <span data-ttu-id="b0119-116">字串，指定要用於遊戲片段的映像檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="b0119-116">A string that specifies the file name of the image to use for the game piece.</span></span>  
  
 <span data-ttu-id="b0119-117">此建構函式也會建立 <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D> 物件和 <xref:System.Windows.Input.Manipulations.InertiaProcessor2D> 物件，並針對這些物件的事件建立事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="b0119-117">The constructor also creates a <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D> object and an <xref:System.Windows.Input.Manipulations.InertiaProcessor2D> object, and establishes event handlers for their events.</span></span>  
  
 <span data-ttu-id="b0119-118">下列程式碼顯示 **GamePiece** 類別的建構函式。</span><span class="sxs-lookup"><span data-stu-id="b0119-118">The following code shows the constructor for the **GamePiece** class.</span></span>  
  
 [!code-csharp[ManipulationXNA#_GamePiece_Constructor](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_constructor)]  
  
## <a name="capturing-mouse-input"></a><span data-ttu-id="b0119-119">捕捉滑鼠輸入</span><span class="sxs-lookup"><span data-stu-id="b0119-119">Capturing Mouse Input</span></span>  
 <span data-ttu-id="b0119-120">**UpdateFromMouse** 方法負責偵測當滑鼠位於遊戲片段界限內時，何時按下滑鼠按鈕，以及偵測何時放開滑鼠按鈕。</span><span class="sxs-lookup"><span data-stu-id="b0119-120">The **UpdateFromMouse** method is responsible for detecting when a mouse button is pressed while the mouse is within the boundaries of the game piece, and for detecting when the mouse button has been released.</span></span>  
  
 <span data-ttu-id="b0119-121">按下滑鼠左鍵時 (當滑鼠位於片段界限)，這個方法會設定旗標，指出這個遊戲片段已捕捉滑鼠，並開始操作處理。</span><span class="sxs-lookup"><span data-stu-id="b0119-121">When the left mouse button is pressed (while the mouse is inside the piece boundaries), this method sets a flag to indicate that this game piece has captured the mouse, and begins manipulation processing.</span></span>  
  
 <span data-ttu-id="b0119-122">操作處理一開始會建立 <xref:System.Windows.Input.Manipulations.Manipulator2D> 物件的陣列，並將其傳遞至 <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D> 物件。</span><span class="sxs-lookup"><span data-stu-id="b0119-122">Manipulation processing is started by creating an array of <xref:System.Windows.Input.Manipulations.Manipulator2D> objects and passing them to the <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D> object.</span></span> <span data-ttu-id="b0119-123">這會導致操作處理器評估操作工具 (在此案例中為單一操作工具)，並引發操作事件。</span><span class="sxs-lookup"><span data-stu-id="b0119-123">This causes the manipulation processor to evaluate the manipulators (in this case a single manipulator), and raise manipulation events.</span></span>  
  
 <span data-ttu-id="b0119-124">此外，也會儲存發生拖曳的點。</span><span class="sxs-lookup"><span data-stu-id="b0119-124">In addition, the point at which the drag is occurring is saved.</span></span> <span data-ttu-id="b0119-125">在之後的 <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> 事件期間，將會使用這個點來調整差異轉譯值，讓遊戲片段轉向拖曳點後面的字行中。</span><span class="sxs-lookup"><span data-stu-id="b0119-125">This is used later during the <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> event to adjust the delta translation values so that the game piece swings into line behind the drag point.</span></span>  
  
 <span data-ttu-id="b0119-126">最後，此方法會傳回滑鼠捕捉的狀態。</span><span class="sxs-lookup"><span data-stu-id="b0119-126">Finally, this method returns the state of the mouse capture.</span></span> <span data-ttu-id="b0119-127">如此可讓 [GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md) 物件在有多個遊戲片段時，管理擷取動作。</span><span class="sxs-lookup"><span data-stu-id="b0119-127">This enables the [GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md) object to manage capturing when there are multiple game pieces.</span></span>  
  
 <span data-ttu-id="b0119-128">下列程式碼顯示 **UpdateFromMouse** 方法。</span><span class="sxs-lookup"><span data-stu-id="b0119-128">The following code shows the **UpdateFromMouse** method.</span></span>  
  
 [!code-csharp[ManipulationXNA#_GamePiece_UpdateFromMouse](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_updatefrommouse)]  
  
## <a name="processing-manipulations"></a><span data-ttu-id="b0119-129">處理操作</span><span class="sxs-lookup"><span data-stu-id="b0119-129">Processing Manipulations</span></span>  
 <span data-ttu-id="b0119-130">操作開始時，會引發 <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Started> 事件。</span><span class="sxs-lookup"><span data-stu-id="b0119-130">When manipulation begins, the <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Started> event is raised.</span></span> <span data-ttu-id="b0119-131">此事件的處理常式會在慣性處理發生時加以停止，並將 *processInertia* 旗標設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="b0119-131">The handler for this event stops inertia processing if it is occurring, and sets the *processInertia* flag to `false`.</span></span>  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnManipulationStarted](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_onmanipulationstarted)]  
  
 <span data-ttu-id="b0119-132">與操作相關聯的值變更時，會引發 <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> 事件。</span><span class="sxs-lookup"><span data-stu-id="b0119-132">As the values associated with the manipulation change, the <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> event is raised.</span></span> <span data-ttu-id="b0119-133">此事件的處理常式會使用以事件引數傳遞的差異值，對遊戲片段的位置和旋轉值進行變更。</span><span class="sxs-lookup"><span data-stu-id="b0119-133">The handler for this event uses the delta values passed in the event arguments to make changes to the position and rotation values of the game piece.</span></span>  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnManipulationDelta](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_onmanipulationdelta)]  
  
 <span data-ttu-id="b0119-134">與操作相關聯的所有操作工具 (在此案例中為單一操作工具) 被移除時，操作處理器會引發 <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Completed> 事件。</span><span class="sxs-lookup"><span data-stu-id="b0119-134">When all of the manipulators (in this case, a single manipulator) that are associated with a manipulation are removed, the manipulation processor raises the <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Completed> event.</span></span> <span data-ttu-id="b0119-135">此事件的處理常式開始進行慣性處理時，會將慣性處理器的初始速度設為事件引數所報告的速度，並將 *processInertia* 旗標設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="b0119-135">The handler for this event begins inertia processing by setting the initial velocities of the inertia processor to those reported by the event arguments, and sets the *processInertia* flag to `true`.</span></span>  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnManipulationCompleted](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_onmanipulationcompleted)]  
  
## <a name="processing-inertia"></a><span data-ttu-id="b0119-136">處理慣性</span><span class="sxs-lookup"><span data-stu-id="b0119-136">Processing Inertia</span></span>  
 <span data-ttu-id="b0119-137">當慣性處理針對角度和線性速度、位置 (轉譯) 座標以及旋轉外推新的值時，會引發 <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Delta> 事件。</span><span class="sxs-lookup"><span data-stu-id="b0119-137">As inertia processing extrapolates new values for angular and linear velocities, position (translation) coordinates, and rotation, the <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Delta> event is raised.</span></span> <span data-ttu-id="b0119-138">此事件的處理常式會使用以事件引數傳遞的差異值，來修改遊戲片段的位置和旋轉。</span><span class="sxs-lookup"><span data-stu-id="b0119-138">The handler for this event uses the delta values passed in the event arguments to modify the position and rotation of the game piece.</span></span>  
  
 <span data-ttu-id="b0119-139">如果新的座標導致遊戲片段移到檢視區界限之外，慣性處理的速度會反轉。</span><span class="sxs-lookup"><span data-stu-id="b0119-139">If the new coordinates result in the game piece moving beyond the view port boundaries, the velocity of the inertia processing is reversed.</span></span> <span data-ttu-id="b0119-140">這會使遊戲片段從其遇到的檢視區界限彈開。</span><span class="sxs-lookup"><span data-stu-id="b0119-140">This causes the game piece to bounce off the view port boundary that it has encountered.</span></span>  
  
 <span data-ttu-id="b0119-141">當 <xref:System.Windows.Input.Manipulations.InertiaProcessor2D> 物件在執行外推時，您無法變更其屬性。</span><span class="sxs-lookup"><span data-stu-id="b0119-141">You cannot change the properties of an <xref:System.Windows.Input.Manipulations.InertiaProcessor2D> object while it is running extrapolation.</span></span> <span data-ttu-id="b0119-142">因此，在反轉 X 或 Y 速度時，事件處理常式會先呼叫 <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Complete%2A> 方法來停止慣性。</span><span class="sxs-lookup"><span data-stu-id="b0119-142">Therefore, when reversing the X or Y velocity, the event handler first stops inertia by calling the <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Complete%2A> method.</span></span> <span data-ttu-id="b0119-143">然後它會指派新的初始速度值作為目前的速度值 (針對海綿行為進行調整)，並將 *processInertia* 旗標設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="b0119-143">It then assigns the new initial velocity values to be the current velocity values (adjusted for sponge behavior), and sets the *processInertia* flag to `true`.</span></span>  
  
 <span data-ttu-id="b0119-144">下列程式碼顯示 <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Delta> 事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="b0119-144">The following code shows the event handler for the <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Delta> event.</span></span>  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnInertiaDelta](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_oninertiadelta)]  
  
 <span data-ttu-id="b0119-145">當慣性處理完成時，慣性處理器會引發 <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Completed> 事件。</span><span class="sxs-lookup"><span data-stu-id="b0119-145">When inertia processing is complete, the inertia processor raises the <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Completed> event.</span></span> <span data-ttu-id="b0119-146">此事件的處理常式會將 *processInertia* 旗標設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="b0119-146">The handler for this event sets the *processInertia* flag to `false`.</span></span>  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnInertiaCompleted](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_oninertiacompleted)]  
  
 <span data-ttu-id="b0119-147">截至目前為止，沒有任何存在的邏輯真正導致慣性外推發生。</span><span class="sxs-lookup"><span data-stu-id="b0119-147">None of the logic presented so far actually causes inertia extrapolation to occur.</span></span> <span data-ttu-id="b0119-148">這會在 **ProcessInertia** 方法中完成。</span><span class="sxs-lookup"><span data-stu-id="b0119-148">This is accomplished in the **ProcessInertia** method.</span></span> <span data-ttu-id="b0119-149">這個方法是從遊戲更新迴圈 ([Game.Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) 方法) 重複呼叫，以檢查 *processInertia* 旗標是否設為 `true`；如果是，則會呼叫 <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Process%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="b0119-149">This method, which is called repeatedly from the game update loop (the [Game.Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) method) checks to see if the *processInertia* flag is set to `true`, and if so, calls the <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Process%2A> method.</span></span> <span data-ttu-id="b0119-150">呼叫這個方法會導致外推發生，並引發 <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Delta> 事件。</span><span class="sxs-lookup"><span data-stu-id="b0119-150">Calling this method causes extrapolation to occur, and raises the <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Delta> event.</span></span>  
  
 [!code-csharp[ManipulationXNA#_GamePiece_ProcessInertia](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_processinertia)]  
  
 <span data-ttu-id="b0119-151">在呼叫其中一個 Draw 方法多載之前，不會實際呈現遊戲片段。</span><span class="sxs-lookup"><span data-stu-id="b0119-151">The game piece is not actually rendered until one of the Draw method overloads is called.</span></span> <span data-ttu-id="b0119-152">這個方法的第一個多載是從遊戲繪圖迴圈 ([Game.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) 方法) 重複呼叫。</span><span class="sxs-lookup"><span data-stu-id="b0119-152">The first overload of this method is called repeatedly from the game draw loop (the [Game.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) method).</span></span> <span data-ttu-id="b0119-153">這會呈現具有目前位置、旋轉和縮放比例的遊戲片段。</span><span class="sxs-lookup"><span data-stu-id="b0119-153">This renders the game piece with the current position, rotation, and scale factors.</span></span>  
  
 [!code-csharp[ManipulationXNA#_GamePiece_Draw](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_draw)]  
  
## <a name="additional-properties"></a><span data-ttu-id="b0119-154">其他屬性</span><span class="sxs-lookup"><span data-stu-id="b0119-154">Additional Properties</span></span>  
 <span data-ttu-id="b0119-155">**GamePiece** 類別使用三個私用屬性。</span><span class="sxs-lookup"><span data-stu-id="b0119-155">Three private properties are used by the **GamePiece** class.</span></span>  
  
1.  <span data-ttu-id="b0119-156">**Timestamp** – 取得操作和慣性處理器所要使用的時間戳記值。</span><span class="sxs-lookup"><span data-stu-id="b0119-156">**Timestamp** – Gets a timestamp value to be used by the manipulation and inertia processors.</span></span>  
  
2.  <span data-ttu-id="b0119-157">**X** – 取得或設定遊戲片段的 X 座標。</span><span class="sxs-lookup"><span data-stu-id="b0119-157">**X** – Gets or sets the X coordinate of the game piece.</span></span> <span data-ttu-id="b0119-158">設定時，可調整用於點擊測試的界限，以及操作處理器的樞紐分析位置。</span><span class="sxs-lookup"><span data-stu-id="b0119-158">When setting, adjusts the bounds used for hit testing and the pivot location of the manipulation processor.</span></span>  
  
3.  <span data-ttu-id="b0119-159">**Y** – 取得或設定遊戲片段的 Y 座標。</span><span class="sxs-lookup"><span data-stu-id="b0119-159">**Y** – Gets or sets the Y coordinate of the game piece.</span></span> <span data-ttu-id="b0119-160">設定時，可調整用於點擊測試的界限，以及操作處理器的樞紐分析位置。</span><span class="sxs-lookup"><span data-stu-id="b0119-160">When setting, adjusts the bounds used for hit testing and the pivot location of the manipulation processor.</span></span>  
  
 [!code-csharp[ManipulationXNA#_GamePiece_PrivateProperties](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_privateproperties)]  
  
## <a name="see-also"></a><span data-ttu-id="b0119-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0119-161">See Also</span></span>  
 [<span data-ttu-id="b0119-162">操作和慣性</span><span class="sxs-lookup"><span data-stu-id="b0119-162">Manipulations and Inertia</span></span>](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md)  
 [<span data-ttu-id="b0119-163">在 XNA 應用程式中使用操作和慣性</span><span class="sxs-lookup"><span data-stu-id="b0119-163">Using Manipulations and Inertia in an XNA Application</span></span>](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md)  
 [<span data-ttu-id="b0119-164">建立 GamePieceCollection 類別</span><span class="sxs-lookup"><span data-stu-id="b0119-164">Creating the GamePieceCollection Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
 [<span data-ttu-id="b0119-165">建立 Game1 類別</span><span class="sxs-lookup"><span data-stu-id="b0119-165">Creating the Game1 Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)

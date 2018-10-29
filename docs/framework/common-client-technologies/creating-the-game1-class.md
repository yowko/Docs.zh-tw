---
title: 建立 Game1 類別
ms.date: 03/30/2017
ms.assetid: 47932ce3-2ba5-476f-a26b-3ddfd5226f27
ms.openlocfilehash: c96fa846d11947af03faec26dd6de99e0aeec052
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452793"
---
# <a name="creating-the-game1-class"></a>建立 Game1 類別
針對所有 Microsoft XNA 專案，Game1 類別衍生自 [Microsoft.Xna.Framework.Game](https://docs.microsoft.com/previous-versions/windows/xna/bb197040%28v%3dxnagamestudio.41%29) 類別，其為 XNA 遊戲提供基本的圖形裝置初始化、遊戲邏輯和轉譯程式碼。 Game1 類別相當簡單，因為大部分工作都是在 GamePiece 和 GamePieceCollection 類別中完成。  
  
## <a name="creating-the-code"></a>建立程式碼  
 此類別的私用成員包含一個 **GamePieceCollection** 物件來保留遊戲片段、一個 [GraphicsDeviceManager](https://docs.microsoft.com/previous-versions/windows/xna/bb197317%28v%3dxnagamestudio.41%29) 物件和一個用來轉譯遊戲片段的 [SpriteBatch](https://docs.microsoft.com/previous-versions/windows/xna/bb199034%28v%3dxnagamestudio.41%29) 物件。  
  
 [!code-csharp[ManipulationXNA#_Game1_PrivateMembers](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_privatemembers)]  
  
 在遊戲初始化期間，這些物件會具現化。  
  
 [!code-csharp[ManipulationXNA#_Game1_ConstructorInitialize](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_constructorinitialize)]  
  
 呼叫 [LoadContent](https://docs.microsoft.com/previous-versions/windows/xna/bb975766%28v%3dxnagamestudio.41%29) 方法時，會建立遊戲片段，並將其指派給 **GamePieceCollection** 物件。 遊戲片段分為兩種類型： 片段的縮放比例稍有變更，導致有些片段較小，有些片段較大。  
  
 [!code-csharp[ManipulationXNA#_Game1_LoadContent](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_loadcontent)]  
  
 在執行遊戲時，XNA Framework 會重複呼叫 [Update](https://docs.microsoft.com/previous-versions/windows/xna/bb199616%28v%3dxnagamestudio.41%29) 方法。 [Update](https://docs.microsoft.com/previous-versions/windows/xna/bb199616%28v%3dxnagamestudio.41%29) 方法會在遊戲片段集合上呼叫 **ProcessInertia** 和 **UpdateFromMouse** 方法。 [建立 GamePieceCollection 類別](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)中有這些方法的說明。  
  
 [!code-csharp[ManipulationXNA#_Game1_UpdateGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_updategame)]  
  
 在執行遊戲時，XNA Framework 也會重複呼叫 [Draw](https://docs.microsoft.com/previous-versions/windows/xna/bb196422%28v%3dxnagamestudio.41%29) 方法。 [Draw](https://docs.microsoft.com/previous-versions/windows/xna/bb196422%28v%3dxnagamestudio.41%29) 方法會呼叫 **GamePieceCollection** 物件的 **Draw** 方法，來執行遊戲片段的轉譯。 [建立 GamePieceCollection 類別](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)中有這個方法的說明。  
  
 [!code-csharp[ManipulationXNA#_Game1_DrawGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_drawgame)]  
  
## <a name="see-also"></a>請參閱  
 [操作和慣性](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md)  
 [在 XNA 應用程式中使用操作和慣性](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md)  
 [建立 GamePiece 類別](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
 [建立 GamePieceCollection 類別](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
 [完整程式碼清單](../../../docs/framework/common-client-technologies/full-code-listings.md)

---
title: 建立 GamePieceCollection 類別
ms.date: 03/30/2017
ms.assetid: e4b037ee-1201-4a55-b198-0d6532ed6f35
ms.openlocfilehash: 6473f7afce1422ee31d4f1872f8310bdeeb9a3b6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="creating-the-gamepiececollection-class"></a>建立 GamePieceCollection 類別
**GamePieceCollection** 類別衍生自泛型清單類別，並引入可更輕鬆管理多個 **GamePiece** 物件的方法。  
  
## <a name="creating-the-code"></a>建立程式碼  
 **GamePieceCollection** 類別的建構函式會初始化 *capturedIndex* 私用成員。 這個欄位用來追蹤目前滑鼠捕捉到的遊戲片段。  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_PrivateMembersAndConstructor](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_privatemembersandconstructor)]  
  
 **ProcessInertia** 和 **Draw** 方法簡化了遊戲 [Game.Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) 和 [Game.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) 方法中必要的程式碼，因為會列舉集合中的所有遊戲片段，並在每個 **GamePiece** 物件上呼叫個別的方法。  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_ProcessInertiaAndDraw](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_processinertiaanddraw)]  
  
 **UpdateFromMouse** 方法也會在遊戲更新期間被呼叫。 藉由第一次檢查目前的捕捉 (如果有的話) 是否仍有作用，它只會啟用一個遊戲片段讓滑鼠捕捉。 若是如此，則不允許其他片段檢查捕捉。  
  
 如果目前沒有片段具有捕捉，則 **UpdateFromMouse** 方法會從最後一個到第一個列舉每個遊戲片段，並檢查該片段是否報告滑鼠捕捉。 若是如此，該片段會變成目前捕捉的片段，並且不進行任何更進一步的處理。 **UpdateFromMouse** 方法會最先檢查集合中的最後一個項目，如此一來，如果兩個片段重疊，則具有較高疊置順序者將取得捕捉。 疊置順序並不明確，也不可以變更；它只是受遊戲片段加入集合的順序所控管。  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_UpdateFromMouse](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_updatefrommouse)]  
  
## <a name="see-also"></a>請參閱  
 [操作和慣性](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md)  
 [在 XNA 應用程式中使用操作和慣性](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md)  
 [建立 GamePiece 類別](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
 [建立 Game1 類別](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)  
 [完整程式碼清單](../../../docs/framework/common-client-technologies/full-code-listings.md)
